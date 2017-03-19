# zsh-command-time

Plugin that output `time: xx` after long commands and export `ZSH_COMMAND_TIME` variable for usage in your scripts.

It similar builin feature [REPORTTIME](http://zsh.sourceforge.net/Doc/Release/Parameters.html), but it outputs only
if user + system time >= `REPORTTIME` in config. For example:
```
$ time sleep 3
sleep 3  0,00s user 0,00s system 0% cpu 3,008 total
```
Sleep don't consume any cpu time and `REPORTTIME` "don't see" such idle commands.

If you need to monitor only cpu-angry commands, use `REPORTTIME` instead this plugin.


## Install with antigen
```
antigen bundle popstas/zsh-command-time
```


## Install for oh-my-zsh

Download:
```
git clone https://github.com/popstas/zsh-command-time.git ~/.oh-my-zsh/custom/plugins/command-time
```
And add `command-time` to `plugins` in `.zshrc`.


## Configuration

You can override defaults in `.zshrc`:
```
# If command execution time above min. time, plugins will not output time.
ZSH_COMMAND_TIME_MIN_SECONDS=3

# Set it to "" for disable echo `time: xx`.
ZSH_COMMAND_TIME_ECHO=1
```


## Usage with [powerlevel9k](https://github.com/bhilburn/powerlevel9k) theme

Add custom element in `.zshrc`:
```
POWERLEVEL9K_CUSTOM_COMMAND_TIME="zsh_command_time"
POWERLEVEL9K_CUSTOM_COMMAND_TIME_BACKGROUND="253" # white
POWERLEVEL9K_CUSTOM_COMMAND_TIME_FOREGROUND="000" # black
```

Add element `custom_command_time` to your prompt:
```
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status background_jobs vcs custom_command_time time)
```


## Provision with ansible
Plugin `command-time` included in ansible role [viasite-ansible/ansible-role-zsh](https://github.com/viasite-ansible/ansible-role-zsh)
with other useful plugins.
