# sscreen
SSH screen session manager with tab completion.

## Install

```bash
git clone git@github.com:HoldenMorris/sscreen.git
cd sscreen
./sscreen --install
source ~/.bashrc
```

## Usage

```bash
sscreen <host> <name>       # create named screen and attach
sscreen <host>              # connect to host (default action)
sscreen <host> connect      # same as above
sscreen <host> attach <screen>  # attach to existing screen
sscreen <host> list        # list screens on specific host
sscreen <host> run <name> <cmd> # run command in named screen
sscreen <host> kill <screen>    # kill a screen
sscreen list               # list screens on all SSH config hosts
sscreen hosts              # show SSH config hosts
sscreen --install          # install/upgrade sscreen
```

## Requirements
- SSH config in ~/.ssh/config with defined hosts
- screen installed on remote hosts
- bash-completion installed locally

---

## Screen Cheatsheet

### Start a Screen Session

```bash
screen -S session_name
```

### Detach from a Session

While inside a session, press: `Ctrl+a d`

### Reattach to a Session

```bash
screen -r session_name
screen -r 12345.pts-0.host  # by session ID
```

### Key Screen Commands

| Shortcut | Description |
|----------|-------------|
| `Ctrl+a c` | Create a new window |
| `Ctrl+a "` | List all windows |
| `Ctrl+a 0-9` | Switch to window by number |
| `Ctrl+a k` | Kill the current window |
| `Ctrl+a S` | Split screen horizontally |
| `Ctrl+a \|` | Split screen vertically |
| `Ctrl+a Tab` | Switch focus between split regions |
| `Ctrl+a [` | Enter scrollback mode |
| `Ctrl+a ]` | Paste copied text |
| `Ctrl+a ?` | Show help |

### Launch a Command in a Detached Screen via SSH

```bash
ssh user@host 'screen -S mytask -d -m bash -c "your_command_here"'
```

### Kill a Detached Screen

```bash
screen -ls                    # list sessions
screen -S 12345 -X quit       # kill by ID
screen -S session_name -X quit # kill by name
screen -wipe                  # remove dead sessions
```

### Auto-Start Screen on SSH Login

Add to ~/.bashrc on remote server:

```bash
if [ -z "$STY" ] && [ -n "$SSH_CLIENT" ]; then
  screen -RR -S main
fi
```
