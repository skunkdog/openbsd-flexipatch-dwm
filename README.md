# Fork of dwm-flexipatch configured to work flawlessly on openbsd machine.

This dwm 6.8 (2bb919e, 2026-03-08) side project has a different take on dwm patching. It uses preprocessor directives to decide whether or not to include a patch during build time. Essentially this means that this build, for better or worse, contains both the patched _and_ the original code. The aim being that you can select which patches to include and the build will contain that code and nothing more. Due to the complexity of some of the patches dwm-flexipatch has diverged from mainstream dwm by making some core patches non-optional for maintenance reasons. For the classic dwm-flexipatch build refer to branch [dwm-flexipatch-1.0](https://github.com/bakkeby/dwm-flexipatch/tree/dwm-flexipatch-1.0).

For example to include the `alpha` patch then you would only need to flip this setting from 0 to 1 in [patches.h](https://github.com/bakkeby/dwm-flexipatch/blob/master/patches.def.h):
```c
#define BAR_ALPHA_PATCH 1
```

So if you have ever been curious about trying out dwm, but have been discouraged by manual patching, then this may be a good starting point to see what a "fully fledged" dwm can look like. Want to try out the `pertag` patch? Just flip a config and recompile. Once you have found out what works for you and what doesn't then you should be in a better position to choose patches should you want to start patching from scratch.


dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.


Requirements
------------
In order to build dwm you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install


Running dwm
-----------
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


Configuration
-------------
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.
