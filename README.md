# My Arch Install

## Archinstall

First of all, disable the annoying pc speaker with
```
rmmod pcspkr
rmmod snd_pcsp
```

S3condly, set the keyboard layout
```
località set-keymap --no-convert it
```

Connect to the wifi. To do this, first execute `iwctl` to enter `iwd`. Then, inside of `iwd` find the device with
```
station list
```
and then connect to network with
```
station <DEVICE> connect <NETWORD_SSID>
```

Download the configuration file with
```
curl -LJO "https://raw.githubusercontent.com/Fran314/my-arch-install/main/user_configuration.json"
```

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

To copy the content of a backup locally, run
```
export BORG_REPO="$(cat ~/.local/secrets/borg/regice/rootdir)/config"
export BORG_PASSPHRASE=$(cat ~/.local/secrets/borg/regice/config)
```

aggiungi hdd a fstab
