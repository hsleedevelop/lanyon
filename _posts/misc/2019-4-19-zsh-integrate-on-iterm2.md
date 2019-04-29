---
layout: post
title: Iterm2 - integrate zsh
description: Iterm2에 zsh을 통합하는 방법
category: misc
tags: [misc, ai]
lang: ko
---

1. install Iterm2
2. brew install zsh

3. install open-my-zsh
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
4. choose color in preferences
5. set ZSH_THEME="agnoster" in ~/.zshrc
6. change font to d2font by naver >> ligature
7. syntax_highlighting

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

8. remove mac-book

```
prompt_context() {
  if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
    prompt_segment black default "%(!.%{\%F{yellow}%}.)$USER"
  fi
}
```
