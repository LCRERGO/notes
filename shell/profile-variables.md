# Shell: Profile Variables
--------------------------
At the start of a Window Manager (WM) or Desktop Environment (DE) user
generally want some scripts to be run to set variables, start programs...
For this reason shell utilities have a few files that are read on specific
times (login of a user, start of a display manager...).

Probably one of the most remembered files is the *~/.profile*, but there are a
few things to consider about it. First it is only read by login shells, which
means that if you do a `su`; for example, the root PATH will not be read (on
Debian based distros the root PATH and the user are different), for that it is
needed to use `su -l` to execute a login shell.

Another thing that might happen when *~/.profile* is used is that it will not
be read by zsh, since the default profile for zsh is *~/.zprofile*, the fix is
pretty trivial: a simple symbolic link will do the trick.


