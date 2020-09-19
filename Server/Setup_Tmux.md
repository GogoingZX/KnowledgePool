# Setup - Tmux

[TOC]

---

## Tmux

### Install

```bash
$ wget https://github.com/tmux/tmux/releases/download/3.1b/tmux-3.1b.tar.gz

$ tar zxvf tmux-3.1b.tar.gz

$ cd tmux-3.1b

$ ./configure && make

$ make install
```



### Update Config

* Path: `~/.tmux.conf`

```bash
$ vi ~/.tmux.conf
```

```bash
## Tmux Config
## Version: tmux 3.1b

# Shift arrow to switch windows
bind -n S-Left previous-window
bind -n S-Right next-window

set -g monitor-activity on
set -g visual-activity off

set -g default-terminal "screen-256color"
setw -q -g utf8 on

set -g history-limit 5000     # boost history
set -g base-index 1           # start windows numbering at 1
setw -g pane-base-index 1     # make pane numbering consistent with windows
set -g status-interval 10     # redraw status line every 10 seconds

set -g status-fg black
set -g status-bg green

set-window-option -g window-status-current-style fg=black
set-window-option -g window-status-current-style bg=white

set -g status-right " (๑•̀ㅂ•́) %H:%M:%S %Y-%m-%d %a  "

bind | split-window -h
bind - split-window -v

bind Left select-pane -L
bind Right select-pane -R
bind Up select-pane -U
bind Down select-pane -D

set -g mouse on
#set -g default-command /bin/zsh

# Easy config reload
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"
```



