# Work in Progress

The gem-no-executable library is a rubygems plugin that lets you prevent executables from being installed.

`gem install tilt --no-executable`

# Motivation

The original motivation for this library was the "tilt" library for Ruby, which is an interface for various template engines.
The problem is that it also installs a "tilt" executable that conflicts with the `tilt` microservice command line tool.

In theory this could be worked around using the `--format-executable` option to the `gem install` command. Unfortunately, tools like
rbenv can't take advantage of it because behind the scenes rubygems uses `RbConfig::CONFIG['ruby_install_name']` and rbenv
sets its install name to just plain "ruby" regardless of version.

# Solution

With this plugin you can now pass the `--no-executable` option to `gem install` to prevent executables for that library
from being installed.
