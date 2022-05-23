# Changing Default Applications
-------------------------------
Sometimes it may be needed to change default applications to be run with an
specific file for that reason there are a few ways to that conforming with
[XDG specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html).
It should be noted that there are a few applications that do not respect the
way to open a file by using `xdg-open` which is the main program from xdg suite
responsible for that, in those cases each deafult application
should be set inside the user application if possible.

## First option (xdg-mime)
`xdg-mime` is an application that comes with the XDG suite that sets the
default applications that should be used for each 
[mimetype](https://datatracker.ietf.org/doc/html/rfc6838) of a file.

To find which application is currently opening a mimetype:
```
xdg-mime query default type/subtype
```

To find the mimetype of a specified file:
```
xdg-mime query filetype file
```

Finally to set an application for one or more mimetypes (if more than one
mimetype they should be separated by spaces):
```
xdg-mime default application.desktop mimetype(s)
```

It should be noted that the application **should be** a *.desktop* file.

## Second option (mimeapps.list)

If XDG utils are on the system a file in $XDG\_CONFIG\_HOME is created by the
name *mimeapps.list* this file lists all the mimetypes in three sections:

- Added Associations
- Removed Associations
- Default Applications

Added and removed associations are used generally for graphical
applications to add and remove alternate options for opening diferent
files. The only section that alters the same functionality as `xdg-mime` is
the default section.

## Caveats
The bigest caveat of using *xdg-mime* and *mimeapps.list* is that neither of
them support regular expressions, so if you have application that should be
used for multiple mimetypes, each mimetype should be set individually.
