# BASIC TOOLS
These tools are not pretending to be penetration tools. They are critical to the penetration process, so we must master them.

## SSH (Secure shell)
- Runs on port 22 by default
- Provides secure remote access

```bash
ssh [username]@[IP]
```

## NETCAT
Netcat, ncat or nc is an network utility for interacting with TCP/UDP ports.
- Its primary usage is for connecting to shells
- It can be used to connect to any listening port and interact with services running

```bash
netcat [IP] [PORT]
```

## TMUX
It is a terminal multiplexer for expanding a standard Linux terminal's features. It should permits to have multiple windows within one terminal and jumping between them.

```bash
$ sudo apt install tmux -y
$ tmux
```

- [CTRL + B] -> The default key to input tmux command prefix (PREFIX)
- [PREFIX + C] -> Open new window
- [PREFIX + NUMBER] -> Switch between open windows
- [PREFIX + SHIFT + %] -> Split a window vertically into panes
- [PREFIX + SHIFT + "] -> Split a window horizontally into panes
- [PREFIX + ARROWS] -> Switch between the panes

## VIM/NEOVIM
Text editor. You don't have to use the mouse, which will significantly increase your productivity and efficiency in writting/editing code.

```bash
vim /etc/hosts
```

- i -> INSERT mode
- ESC -> get out of insert mode
- x -> cut character
- dw -> cut word
- dd -> cut full line
- yw -> copy word
- yy -> copy full line
- p -> paste

> We can multiply any command by adding a number before it. For example, '4yw' would copy 4 words.

- NUMBER -> go to those line
- w -> write file
- q -> quit file
- q! -> quit with no saving
-> wq -> write and quit file


