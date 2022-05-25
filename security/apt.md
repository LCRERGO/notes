# apt
-----
In Debian based distros the main way to manage software packages is by using
the apt (Advanced Package Tool), to make more secure how package is
installed it is needed that the fingerprint of each package (md5sum,
sha1sum...) to be checked before being installed. For that the files
**InRelease** **Release** are downloaded from each repository mirror to make
sure that each package is assured to be secure.

It may be possible for an adversary to sneak an untrusted source of
packages onto the *sources.list* file. For that reason it is recomended that
only use repositories that can have it's figerprint checked against a gpg set
of keys.

Debian official repositories have it's gpg signatures provided by the
*debian-archive-keyring* package which normally comes preinstalled with
Debian based distros. The downloaded signatures are stored under
*/etc/apt/trusted.gpg.d/*. In case third party keys are needed to be added,
which is not recommended for the average user, the key simply be moved to this
location or added to it with `apt-key add < key.asc`.

