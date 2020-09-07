# zsh-xi

E***x***ecute commands when spawning ***i***nteractive zsh session, as if you had entered the commands manually. Optionally, start everything inside a terminal.

### Usage

Commands are read from stdin. Use `echo <cmd> | zsh-xi` for simple one-liners
such as `echo vim /tmp/scratchpad | zsh-xi`. When dealing with more complex
constructs use the heredoc syntax, e.g.

```sh
# compile your C project and run tests whenever files change
zsh-xi <<EOF
echo "main.c" |
  entr -rpcs "make; ./build/test --all"
EOF
```

After your command finishes execution you will find it inside your active
shell's history, as if you had spawned a shell and had entered the command
yourself.

The shell may be **spawned inside a new terminal window** by passing the
terminal-specific startup command prefix as arguments to `zsh-xi`.

```sh
# Spawn zsh in kitty and define foo=bar
echo "foo=bar" | zsh-xi kitty

# Spawn neovim in a gnome-terminal
echo "nvim" | zsh-xi gnome-terminal --

# Spawn st and display the weather
echo "curl wttr.in" | zsh-xi st
```

### Installation

Requires **zshi** found [here](https://github.com/romkatv/zshi). To install simply make the scripts available to your \$PATH. For example:

```sh
sudo curl -L -o /usr/local/bin/zshi "https://raw.githubusercontent.com/romkatv/zshi/master/zshi"
sudo curl -L -o /usr/local/bin/zsh-xi "https://raw.githubusercontent.com/slavistan/zsh-xi/master/zsh-xi"
```
