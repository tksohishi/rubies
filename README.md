Rubies
======

Rubies (or rbs) is a small script to switch Ruby runtime by rewriting PATH and GEM_HOME.
No tricks. The script is written in Ruby works with a small shell script.

*This script does*

 *  Switch Ruby in your shell environment.
 *  Switch RubyGems repository.

*This script doesn't*

 *  Install, uninstall Ruby.
 *  Install, uninstall RubyGems itself.
 *  Manage gems, libraries, etc.

Getting Started
---------------

1.  Clone this repository to `~/.rubies`.

2.  Source `~/.rubies/src/rubies.sh` in your `~/.bashrc` or `~/.zshrc`.
    Sorry, no `csh` support.

        source "$HOME/.rubies/src/rubies.sh"

3.  Install Ruby into `~/.rubies` by yourself from Ruby source code.
    Example configure scripts, patches are in `~/.rubies/src/`.

        $ tar xzvf ruby-enterprise-1.8.7-2009.10.tar.gz
        $ cd ruby-enterprise-1.8.7-2009.10
        $ ./installer -a "$HOME/.rubies/ruby-enterprise-1.8.7-2009.10"

4.  If you wanted to select installed Ruby more easy, create a symlink.

        $ cd ~/.rubies
        $ ln -s ruby-enterprise-1.8.7-2009.10 ree

5.  Switch Ruby by `rubies` or `rbs` command.

        $ rubies ree

Switch Ruby in each Projects
----------------------------

[rvm](https://rvm.beginrescueend.com/) provides `cd` command hook
so we can switch Ruby in each project directories which is nice.
Rubies provides same hook which can read existing `.rvmrc` file.

1.  Add `enable_rubies_cd_hook` in your `~/.bashrc` or `~/.zshrc`
    after source `~/.rubies/src/rubies.sh`.

        source "$HOME/.rubies/src/rubies.sh"
        enable_rubies_cd_hook

2.  Place `.rubiesrc` in each project directory or `~/` which can select default Ruby.
    `.rubiesrc` is YAML format.
	We can use only `ruby` parameter for now which selects Ruby.

        $ echo "ruby: ree" > ~/.rubiesrc
