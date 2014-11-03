---
title: Digging Into RubyGems
author: admin
layout: post
permalink: /digging-into-rubygems/
categories:
  - ruby
  - software
---
Every developer has experienced an episode of painful dependency management. Missing libs, &#8220;dll hell,&#8221; and hours of wasted effort. Been there. It&#8217;s painful.

Luckily for those working in the Ruby ecosystem, there is a nice tool that helps with dependency management: RubyGems.

In this post we&#8217;ll dive a little deeper into how RubyGems works with your Ruby code to properly load and manage gems. Understanding the load process will better prepare you when things go wrong (and things will, won&#8217;t they?) It will also give you insights into how to hook and innovate outside the normal RubyGems&#8217;s behaviour if you so choose.

**Ruby&#8217;s `$LOAD_PATH` or Where&#8217;s my library?!**

When you load a dependency via Ruby&#8217;s `require` or `load`, where does Ruby go to fetch that library? Answer: `$LOAD_PATH`.

Ruby&#8217;s `$LOAD_PATH` is an array of directories that Ruby will search in to find and load dependencies.

This is what my Mac OS X system Ruby&#8217;s `$LOAD_PATH` looks like (Ruby 1.8.7):

<pre class="brush: ruby; title: ; notranslate" title="">$ irb
irb&gt; $LOAD_PATH
=&gt; ["/opt/local/lib/ruby/site_ruby/1.8", "/opt/local/lib/ruby/site_ruby/1.8/i686-darwin10",
"/opt/local/lib/ruby/site_ruby", "/opt/local/lib/ruby/vendor_ruby/1.8", "/opt/local/lib/ruby/vendor_ruby/1.8/i686-darwin10", "/opt/local/lib/ruby/vendor_ruby", "/opt/local/lib/ruby/1.8", "/opt/local/lib/ruby/1.8/i686-darwin10","."]
</pre>

When I `require 'myfile'` in my Ruby code (if I am running my system 1.8.7 version), Ruby will try and find the file `myfile.rb` in one of the directories above and run it. If not, it will raise a `LoadError` exception.

At a crude level, you could manually drop dependencies in the `$LOAD_PATH` to load libraries. But programmers are lazy and that&#8217;s a lot of work. Wouldn&#8217;t it be cool if there was a tool to manage gems for you?

Enter RubyGems.

**RubyGems: Painless dependency management**

RubyGems is a tool to discover, distribute, manage and build gems. When you install RubyGems (http://docs.rubygems.org/read/chapter/3), it does two things: it writes the source to one of the directories in Ruby&#8217;s `$LOAD_PATH` so you can `require 'rubygems'` in Ruby and installs the command line tool gem to help manage the gems themselves. They work together: by installing gems in a standard place, RubyGems can then work more intelligently about how to make libraries accessible from Ruby.

After I installed RubyGems 1.6.2, I see that `rubygems.rb` was installed in `/opt/local/lib/ruby/site_ruby/1.8`, which is part of the `$LOAD_PATH`. The gem command line tool was installed in `/opt/local/bin`.

Furthermore, the gem command tool I use to install gems has the following environment setup:

<pre class="brush: ruby; title: ; notranslate" title="">$ gem environment
RubyGems Environment:
- RUBYGEMS VERSION: 1.6.2
- RUBY VERSION: 1.8.7 (2010-01-10 patchlevel 249) [i686-darwin10]
- INSTALLATION DIRECTORY: /opt/local/lib/ruby/gems/1.8
- RUBY EXECUTABLE: /opt/local/bin/ruby
- EXECUTABLE DIRECTORY: /opt/local/bin
- RUBYGEMS PLATFORMS:
- ruby
- x86-darwin-10
- GEM PATHS:
- /opt/local/lib/ruby/gems/1.8
- /Users/iha/.gem/ruby/1.8
- GEM CONFIGURATION:
- :update_sources =&gt; true
- :verbose =&gt; true
- :benchmark =&gt; false
- :backtrace =&gt; false
- :bulk_threshold =&gt; 1000
- REMOTE SOURCES:
- http://rubygems.org/
</pre>

Notice the value of `INSTALLATION DIRECTORY`; that&#8217;s where my gems are installed when I run `gem install name_of_a_gem`. How does RubyGems decide to put gems there? It&#8217;s relative to where the `ruby` executable directory is, which in my case is in `/opt/local/bin/`.

No wasted effort deciding for yourself where to put gems, the gem tool decides for you. You&#8217;ll notice too that it&#8217;ll try and find gems from the remote site http://rubygmes.org, a popular gem hosting site. Nice!

Let&#8217;s go ahead and install Nokogiri, a popular XML parser, from rubygems.org.

<pre class="brush: ruby; title: ; notranslate" title="">$ gem install nokogiri # go off to remote source http://rubygems.org
...
$ gem list&lt;/code&gt;

*** LOCAL GEMS ***

nokogiri (1.4.4)
</pre>

Great! We just installed our first gem. And going to the install directory we notice:

<pre class="brush: ruby; title: ; notranslate" title="">$ cd /opt/local/lib/ruby/gems/1.8/gems
$ ls
nokogiri-1.4.4/
</pre>

as expected by the gem command-line tool&#8217;s environment.

Let&#8217;s run some Ruby code via irb and require Nokogiri.

<pre class="brush: ruby; title: ; notranslate" title="">$ irb
irb&gt; require 'nokogiri'
LoadError: no such file to load -- nokogiri
from (irb):1:in `require'
from (irb):1
from :0
</pre>

As expected, it can&#8217;t find Nokogiri, since the Nokogiri gem was installed in `/opt/local/lib/ruby/gems/1.8/gems/nokogiri-1.4.4/`, which is not in `$LOAD_PATH`, so Ruby can&#8217;t find it. To make installed gems accessible from Ruby we first have to load RubyGems (recall `rubygems.rb` is in the `$LOAD_PATH`):

<pre class="brush: ruby; title: ; notranslate" title="">irb&gt; require 'rubygems'
=&gt; true
irb&gt; require 'nokogiri'
=&gt; true
</pre>

Success! We just loaded our first gem.

At this point, we might reasonably assume that RubyGems has placed Nokogiri in `$LOAD_PATH`, which is why `require 'nokogiri'` now works, but this is not the case. In fact, `$LOAD_PATH` has not changed at all:

<pre class="brush: ruby; title: ; notranslate" title="">irb&gt; $LOAD_PATH
=&gt; ["/opt/local/lib/ruby/gems/1.8/gems/nokogiri-1.4.4/lib", "/opt/local/lib/ruby/site_ruby/1.8", "/opt/local/lib/ruby/site_ruby/1.8/i686-darwin10", "/opt/local/lib/ruby/site_ruby", "/opt/local/lib/ruby/vendor_ruby/1.8", "/opt/local/lib/ruby/vendor_ruby/1.8/i686-darwin10", "/opt/local/lib/ruby/vendor_ruby", "/opt/local/lib/ruby/1.8", "/opt/local/lib/ruby/1.8/i686-darwin10", "."]
</pre>

If `$LOAD_PATH` is unchanged, how were we able to require Nokogiri?? By overriding `require`.

Looking at the source, we notice that RubyGems 1.6.2 has done exactly that:

<pre class="brush: ruby; title: ; notranslate" title="">#--
# Copyright 2006 by Chad Fowler, Rich Kilmer, Jim Weirich and others.
# All rights reserved.
# See LICENSE.txt for permissions.
#++

module Kernel

 if defined?(gem_original_require) then
    # Ruby ships with a custom_require, override its require
    remove_method :require
  else
    ##
    # The Kernel#require from before RubyGems was loaded.

    alias gem_original_require require
    private :gem_original_require
  end

  ##
  # When RubyGems is required, Kernel#require is replaced with our own which
  # is capable of loading gems on demand.
  #
  # When you call require 'x', this is what happens:
  # * If the file can be loaded from the existing Ruby loadpath, it
  # is.
  # * Otherwise, installed gems are searched for a file that matches.
  # If it's found in gem 'y', that gem is activated (added to the
  # loadpath).
  #
  # The normal require functionality of returning false if
  # that file has already been loaded is preserved.

  def require path
 if Gem.unresolved_deps.empty? or Gem.loaded_path? path then
      gem_original_require path
    else
      spec = Gem.searcher.find_active path

      unless spec then
        found_specs = Gem.searcher.find_in_unresolved path
        unless found_specs.empty? then
          found_specs = [found_specs.last]
        else
          found_specs = Gem.searcher.find_in_unresolved_tree path
        end

        found_specs.each do |found_spec|
          # FIX: this is dumb, activate a spec instead of name/version
          Gem.activate found_spec.name, found_spec.version
        end
      end

      return gem_original_require path
    end
  rescue LoadError =&gt; load_error
 if load_error.message.end_with?(path) and Gem.try_activate(path) then
      return gem_original_require(path)
    end

    raise load_error
  end

  private :require

end
</pre>

Requiring RubyGems loads the `Gem` module which has it&#8217;s own internal path array. This array is used by the overridden require method to search for installed gems, in addition to looking in `$LOAD_PATH`.

That path is:

<pre class="brush: ruby; title: ; notranslate" title="">irb&gt; Gem.all_load_paths
=&gt; ["/opt/local/lib/ruby/gems/1.8/gems/nokogiri-1.4.4/lib"]
</pre>

So we see the path to Nokogiri in the `Gem` module&#8217;s internal path, which is used in the overwritten `require` to search for gems. The `Gem` module constructs this array by going into the default gem respository (in this case `/opt/local/lib/ruby/gems/1.8`) and writes the absolute path to the `lib` directory of each gem into the array, as well as any gem-specific load paths defined in the `.gemspec` file of each gem. You can override the default gem repository by defining the environment variable `$GEM_PATH`.

This explains how we were able to require Nokogiri without changing `$LOAD_PATH`.

So now we see the big picture: Manage gems via the gem command-line tool; `require 'rubygems'` and then require any gem in Ruby after that.

**Ruby 1.9**

As of Ruby 1.9, you no longer need to explicitly `require 'rubygems'` as it&#8217;s now baked right into Ruby. However, if you are running 1.8, be careful of literring your code with `require 'rubygems'` all over as some prominent Rubyists have argued (https://gist.github.com/54177)&#8211;and I believe rightly&#8211;that it unecessarily couples your code to RubyGems, which is really a environment setup configuration.

The workaround is to set the `RUBYOPT` environment variable to &#8216;rubygems&#8217; so that Ruby will run with &#8216;-rubygems&#8217; as an option to automatically load RubyGems on startup.

**Conclusion or The Path To Enlightenment**

It might have occurred to you that despite my plug for RubyGems, there&#8217;s a problem. By default `require 'nokogiri'` pulls the latest gem from your gem repo. But what if I have different versions of Nokogiri? And what if my code needs to load different versions depending on some condition (say, testing versus development)?

Luckily there&#8217;s an answer: Bundler. We&#8217;ll explore Bundler and versioned dependency management in Rails in our next post. But in the meantime, you can require RubyGems and make your life that more painless for now.