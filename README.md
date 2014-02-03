KPP-Helsinki
============

This is the [KPP – The Kinetic PreProcessor][1] with some small 
modifications as we use it at the [Atmospheric Modelling Group][2] at 
the University of Helsinki.

To Build
--------

Along the lines of the [original `readme`][3], to build KPP on Ubuntu (I 
have Ubuntu 13.10), you need:

* flex (install Ubuntu package: flex)
* bison (install Ubuntu package: bison)
* `libfl.a` is located at `/usr/lib/x86_64-linux-gnu/libfl.a` (if not, use
  `locate libfl.a` to find it). I already added this path to `Makefile.defs`
  so you need to do nothing about this.
* Add something like this to your `.bashrc`

        export KPP_HOME=$HOME/kpp-helsinki
        PATH=$PATH:$HOME/kpp-helsinki/bin

* Then (here in the project main directory) run `make`. Now you should have
the KPP executable `bin/kpp`.

Main Changes I Made
-------------------

* This should compile on a recent Ubuntu without any edits needed
* Increase MAX_EQN 400 to 10000, MAX_SPECIES 500 to 2000
* Optimization flags to `Makefile.defs`
* Remove some unnecessary files (*.out, *.mod etc.) left by the original developers (by
accident, I assume)

(This README.md is written with [Markdown][4] syntax.)

Todo
----

Increase buffer sizes for longer reaction rate strings, and longer
chemical names.
Ref. http://www.cs.helsinki.fi/u/ssmoland/physics/michael/ditte/1/
But the `char str[80];` could be fixed in `scan.y` not in `y.tab.*`.

[1]: http://people.cs.vt.edu/~asandu/Software/Kpp/
[2]: https://wiki.helsinki.fi/display/AMG/
[3]: https://github.com/samposm/kpp-helsinki/blob/master/readme
[4]: http://daringfireball.net/projects/markdown/basics
