SonicDE MPBT workspace
======================

This is an [MPBT](https://github.com/metux/mpbt) workspace for building
[SonicDE](https://github.com/Sonic-DE/) (fork of KDE with full X11 compatibility)
all at once.

Warning: it's still an early work-in-progress.

howto:
------

* install MPBT: `go install github.com/metux/mpbt/cmd/mpbt-builder@latest`
* just fetch git repos: `./run-fetch`
* full build: `./run-build`
* create dependency graph: `./run-depgraph`

2do:
----

* model system packages
* * for now just testing on Devuan Excalibur) assuming many packages installed in the host
* * all the system packages yet need to be properly modeled, so at least MPBT can check what's missing
* * also need to check against various other distros
* add lots of dependencies currently picked from host, so we can additionally build the whole stack on our own
* add solutions for other distros
