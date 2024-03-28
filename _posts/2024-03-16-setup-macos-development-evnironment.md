---
layout: post
title: "Setup macOS Development Environment"
---

I do not use `.zshenv` since it has some bugs in macOS (it will be sourced after `.zprofile`).

`.zshrc`:

```sh
if type brew &>/dev/null
then
  FPATH="/opt/homebrew/share/zsh/site-functions:${FPATH}"
  FPATH="/opt/homebrew/share/zsh-completions:${FPATH}"

  autoload -Uz compinit
  compinit
fi

source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh

eval "$(starship init zsh)"
eval "$(atuin init zsh --disable-up-arrow)"

alias ll="eza -l"
alias tree="eza -T"
alias python=".venv/bin/python"
alias pip="uv pip"
```

`.zprofile`:

```sh
eval "$(/opt/homebrew/bin/brew shellenv)"
. "$HOME/.cargo/env"

export PATH="$HOME/go/bin:$PATH"
export VOLTA_HOME="$HOME/.volta"
export PATH="$VOLTA_HOME/bin:$PATH"
export PATH="$HOME/.local/bin:$PATH"
```

## Reference

- [What should/shouldn't go in .zshenv, .zshrc, .zlogin, .zprofile, .zlogout?](https://unix.stackexchange.com/questions/71253/what-should-shouldnt-go-in-zshenv-zshrc-zlogin-zprofile-zlogout)