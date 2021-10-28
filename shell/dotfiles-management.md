# Shell: Dotfiles Management
----------------------------
It is possible to manage an user dotfiles in a very elegant way by using a git
bare repository, since it is not required to move files around or even create
symbolic links.

First it is needed to create the bare repository:
```bash
git init --bare <bare_repository_location>
```

Then to manipulate the repository it is usually easier with an alias (for this
text the "dotfiles" alias will be used):
```bash
alias dotfiles='git --git-dir=<bare_repository_location> --work-tree=${HOME}'
```

It should be noted that the purpose to have a dotfiles directory is for it to
manage files in the HOME directory, that is why the work-tree is set for that
enviromental variable. After that git will track ALL files in the HOME
directory to make a more sane config it should be useful to track only files
that are already on the git index, which can be achieved with:
```bash
dotfiles config --local status.showUntrackedFiles no
```
