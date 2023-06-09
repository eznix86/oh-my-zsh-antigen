

# Zsh + Antigen + Oh my Zsh = A Beautiful, Powerful, and Robust Shell
---

# Zsh

The **Z shell** ([**Zsh**](https://www.zsh.org)) is an extended Unix shell with
many improvements, including some features of
[Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell),
[ksh](https://en.wikipedia.org/wiki/KornShell), and
[tcsh](https://en.wikipedia.org/wiki/Tcsh).

The Zsh itself is neither beautiful nor smart but it enables extensibility so
that community-developed plugins can be applied to make it beautiful and
powerful.

The Zsh is so popular that it’s published to the package repository of almost
all Unix distributions (Ubuntu, Centos, macOS, etc) so that you can easily
install Zsh using your package manager:

```bash
# Ubuntu
sudo apt-get install -y zsh

# CentOS
sudo yum install -y zsh

# macOS (since macOS Catalina, Zsh has been installed with the OS)
brew install zsh
```

---

# Antigen

As we said, Zsh enables pluggability so that users can install plugins and
extend its features. However, Zsh itself does not provide a good plugin
management mechanism, including fetch, install, update, remove plugins, etc.

Fortunately, [**Antigen**](http://antigen.sharats.me) takes this responsibility
very well. Most Zsh plugins are published in the form of git repositories.
Antigen allows us to simply specify a remote repository's path, then it will
automatically fetch and install on the first run. Antigen also provides commands
to update and remove plugins easily.

## Install

First, download Antigen, simply run:

```bash
curl -L git.io/antigen > antigen.zsh
```

Then, paste the following lines into your `~/.zshrc` (if you didn’t have the
file, create one):

```bash
# Load Antigen
source "/path-to-your/antigen.zsh"

# Load Antigen configurations
antigen init ~/.antigenrc
```

## Configure

`~/.antigenrc` will be your Antigen configuration file, where plugins and themes
are listed.

Following is my `~/.antigenrc`:

```bash
# Load oh-my-zsh library
antigen use oh-my-zsh

# Load bundles from the default repo (oh-my-zsh)
antigen bundle git
antigen bundle command-not-found
antigen bundle docker

# Load bundles from external repos
antigen bundle zsh-users/zsh-completions
antigen bundle zsh-users/zsh-autosuggestions
antigen bundle zsh-users/zsh-syntax-highlighting

# Select theme
antigen theme denysdovhan/spaceship-prompt

# Tell Antigen that you're done
antigen apply
```

Skip the line `antigen use oh-my-zsh` for now, we’ll talk about that in the next
section.

To specify a plugin you want to apply:

```bash
antigen bundle remote-repo/url
```

For example, `zsh-users/zsh-completions`, `zsh-users/zsh-autosuggestions`
actually point to `github.com/zsh-users/zsh-completions` and
`github.com/zsh-users/zsh-autosuggestions`. Github is inferred automatically, if
the repositories are hosted under a different domain, just specify the domain.

To apply a theme, use `antigen theme remote-repo/url`.

Finally, you need to have the line `antigen apply` to freeze and apply all
previous configurations.

I’ve just used several plugins, you can find other awesome ones
[here](https://github.com/unixorn/awesome-zsh-plugins).

---

# Oh my Zsh

[**Oh my Zsh**](https://github.com/robbyrussell/oh-my-zsh) is a Zsh
configuration framework, which embeds a bunch of plugins and themes so that you
can turn them on and off easily.

You can easily use Oh my Zsh with Antigen by adding `antigen use oh-my-zsh` to
your `~/.antigenrc`.

Then, to turn on a plugin or use a theme from Oh my Zsh:

```bash
# Turn on an Oh my Zsh plugin
antigen bundle plugin-name
antigen bundle git
antigen bundle command-not-found
antigen bundle docker

# Apply an Oh my Zsh theme
antigen theme theme-name
antigen theme robbyrussell
```

Refer to the following links for a full list of Oh my Zsh
[plugins](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins) and
[themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes).
