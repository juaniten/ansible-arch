# OmArch Bootstrap with Ansible

This is my personal **Ansible playbook to bootstrap **Omarchy** — my Arch Linux spin ([https://omarchy.org/](https://omarchy.org/)). It makes sure my system has the stuff I actually want and gets rid of the bloatware Omarchy  ships with.


## What it does

* Installs all the stuff I actually need (`git`, `stow`, `wget`, etc.)
* Uninstalls the stuff I don’t want (aka bloatware)
* Clones my dotfiles repo into `~/.dotfiles`
* Uses GNU Stow to symlink my dotfiles into `$HOME`


## Prerequisites

* Omarchy (or any Arch-based distro)
* Ansible:

```bash
sudo pacman -S ansible
```

* Ansible collection for pacman module:

```bash
ansible-galaxy collection install community.general
```

---

## How to use it

1. Clone the bootstrap repo:

```bash
git clone https://github.com/juaniten/bootstrap.git
cd bootstrap
```

2. Edit `bootstrap.yml` if needed:

* Make sure `dotfiles_repo` points to your dotfiles repo:

```yaml
dotfiles_repo: "https://github.com/<you-user-name>/<your-dotfiles-repo>.git"
```

* Adjust `packages_present` and `packages_absent` to taste

3. Run the playbook:

```bash
ansible-playbook bootstrap.yml
```

* It’ll ask for your sudo password for installing/removing packages
* Then it installs what you like, removes what you hate, clones your dotfiles, and stows them

## Notes / Tips

* If `~/.dotfiles` exists but isn’t a git repo, the playbook may throw an error.
* Everything is idempotent, so you can run this as often as you want without breaking your system.


## License

MIT — do whatever you want with it.

