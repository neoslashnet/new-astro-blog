---
title: "iTerm2 w/ Oh My Zsh quick config"
pubDate: 2021-02-23
intro: Set up your terminal with this Oh My Zsh quick config.
author: dg
tag: macOS
image: ../../assets/iterm.jpg
---

I recently went through the process to configure my iTerm2 shell in macOS. Here is a quick guide to get it up and running in little to no time.

Once you have iTerm2 installed, we can switch the default shell to Zsh:

*Preferences &gt; Profiles &gt; General &gt; Command - Select Command and enter "/bin/zsh"*

Now Zsh is the default shell.

Once you are using zsh by default, you can install Oh My Zsh, which is a framework managing Zsh configuration.

```python
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

At this point, iTerm is now set up with Zsh so you can install powerlevel10k which is a Zsh plugin providing a powerline (a bar with different information). It is highly customizable and can show the path, git status, time, etc.

Start by downloading powerlevel10k into Zsh themes:

```python
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

After the theme is installed, you need to edit your configuration file-

nano ~/.zshrc and modify the ZSH\_THEME:

```python
nano ~/.zshrc
```

and modify the **ZSH\_THEME**

```python
ZSH_THEME="powerlevel10k/powerlevel10k"
```

After your file is saved, close iTerm2 and open it again. You should be prompted to how you want to customize your terminal settings.

Enjoy!