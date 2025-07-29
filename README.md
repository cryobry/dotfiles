# dotfiles

Deploy configurations using [GNU Stow](https://www.gnu.org/software/stow/manual/stow.html) packages.

* Deploy all common configs

```bash
stow -d common/home -R --adopt -t "$HOME" $(ls common/home)
sudo stow -d common/root -R --adopt -t / $(ls common/root)
```

* Deploy common configs one-by-one

```bash
stow -d common/home -R --adopt -t "$HOME" zsh
sudo stow -d common/root -R --adopt -t / package
```

* Deploy all device-specific configs
  
```bash
stow -d workstation/home -R --adopt -t "$HOME" $(ls workstation/home)
sudo stow -d workstation/root -R --adopt -t / $(ls workstation/root)
```

* Deploy device-specific configs one-by-one

```bash
stow -d workstation/home -R --adopt -t "$HOME" btrbk
sudo stow -d workstation/root -R --adopt -t / grub
```

* Full deploy

```bash
HOSTNAME=workstation # usually the default
stow -d common/home -R --adopt -t "$HOME" $(ls common/home)
stow -d "$HOSTNAME/home" -R --adopt -t "$HOME" $(ls "$HOSTNAME/home")
sudo stow -d common/root -R --adopt -t / $(ls common/root)
sudo stow -d $HOSTNAME/root -R --adopt -t / $(ls "$HOSTNAME/root")
```
