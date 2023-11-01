# Shell: Multiple Keyboard Layout
---------------------------------
Sometimes it is needed to use more than one keyboard layout. In moments like
that it is useful to know how to set on a not dependent from DE (Desktop
Environment) way a keyboard layout.

On Debian-based distros (distributions) the main directory for setting general
settings is located on `/etc/default` and in the case of keyboard the file
that aggregates that kind of information is the keyboard file, which should look
like that:

```
XKBLAYOUT="<layouts>"
XKBVARIANT="<layout_variants>"
XKBMODEL="<keyboard_model>"
XKBOPTIONS="<keyboard_other_options>"
```

## Explanation  
These are not the only fields that are possible on the file, but are the most
common. These fields have the following meaning:

XKBLAYOUT
    : defines all the keyboard layouts that are used on the system. Should be
    comma separated

XKBVARIANT
    : defines all the keyboard variants for each layout are used on the system.
    Should be comma separated, all keyboards should have a variant set, if not
    should have commas to indicate an empty option.

XKBMODEL
    : defines the keyboard model name. Usually it is defined as pc105 on most
    systems.

XKBOPTIONS
    : A list of options for keyboard, usually used for special keys.
    Should be comma separated.

## Example

A reason of why a user would want to do something like that is when a text
editor that requires a heavy use of special keys (e.g. Emacs) and a key should
be remaped, or when a DE or WM that does not have a way of chaging the keyboard
layout. In these situations an example of keyboard file would be something like
the following:

```
XKBLAYOUT="us,br,ru"
XKBVARIANT=",,"
BACKSPACE="guess"
XKBMODEL="pc105"
XKBOPTIONS="grp:rctrl_rshift_toggle,ctrl:swapcaps"
```

Where three layouts are being set (us,br,ru), having the default keyboard
variants (,,) with backspace having it's behavior linked to the chosen layout,
in a pc105 model. Finally the options selected for this example are to use 
the combination of RightControl and RightShift as a layout toggler, and a swap
between CapsLock and Ctrl for better use of keychords.

#### Caveat
Changes to `/etc/default/keyboard` do not become instantly available. For that
either reboot the system or use a trigger such as:  
```bash
udevadm trigger --subsystem-match=input --action=change
```

### References

- [Keyboard Debian Wiki](https://wiki.debian.org/Keyboard)
- [keyboard manpage](https://manpages.debian.org/bookworm/keyboard-configuration/keyboard.5.en.html)
- [xkeyboard-config manpage](https://manpages.debian.org/bookworm/xkb-data/xkeyboard-config.7.en.html)
