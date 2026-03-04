# sscreen
SSH screen session manager with tab completion.

## Install

```bash
git clone git@github.com:HoldenMorris/sscreen.git
cd sscreen
./sscreen --install
source ~/.bashrc
```

Usage

sscreen <host>          # connect to host (default action)
sscreen <host> connect  # same as above
sscreen <host> list     # list screens on specific host
sscreen list            # list screens on all SSH config hosts
sscreen hosts           # show SSH config hosts
sscreen <host> run <cmd> # run command in named screen
sscreen --install       # install/upgrade sscreen

Requirements
- SSH config in ~/.ssh/config with defined hosts
- screen installed on remote hosts
- bash-completion installed locally
