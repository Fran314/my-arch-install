# My Arch Install

## Additional packages

-   openssh
-   borg
-   git
-   wget
-   curl
-   neofetch
-   ufw
-   vim
-   nvim
-   nano

-   npm ? (per `npm install -g @bitwarden/cli` visto che bitwarden-cli di pacman
    usa nodejs-lts-\* che va in conflitto con nodejs)

## Setup

Install npm if not previously installed

```
sudo pacman -S npm
```

Install bitwarden-cli via npm

```
sudo npm install -g @bitwarden/cli
```

Login to bitwarden and export the session with

```
bw login

export BW_SESSION="<YOUR_SESSION_TOKEN>"
```

where `<YOUR_SESSION_TOKEN>` is given in the output of the login.

Create the secrets with

```
mkdir -p ~/.local/secrets/borg/hdd
bw get notes hdd-rootdir > ~/.local/secrets/borg/hdd/rootdir
bw get notes hdd-latias-archive > ~/.local/secrets/borg/hdd/archive
bw get notes hdd-latias-config > ~/.local/secrets/borg/hdd/config
bw get notes hdd-latias-projects > ~/.local/secrets/borg/hdd/projects
bw get notes hdd-latias-various > ~/.local/secrets/borg/hdd/various

mkdir -p ~/.local/secrets/borg/umbreon
bw get notes umbreon-rootdir > ~/.local/secrets/borg/umbreon/rootdir
bw get notes umbreon-latias-archive > ~/.local/secrets/borg/umbreon/archive
bw get notes umbreon-latias-config > ~/.local/secrets/borg/umbreon/config
bw get notes umbreon-latias-projects > ~/.local/secrets/borg/umbreon/projects
bw get notes umbreon-latias-various > ~/.local/secrets/borg/umbreon/various

mkdir -p ~/.local/secrets/borg/regice
bw get notes regice-rootdir > ~/.local/secrets/borg/regice/rootdir
bw get notes regice-latias-archive > ~/.local/secrets/borg/regice/archive
bw get notes regice-latias-config > ~/.local/secrets/borg/regice/config
bw get notes regice-latias-projects > ~/.local/secrets/borg/regice/projects
bw get notes regice-latias-various > ~/.local/secrets/borg/regice/various
```

aggiungi hdd a fstab
