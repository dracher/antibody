# antibody [![Build Status](https://travis-ci.org/caarlos0/antibody.svg?branch=master)](https://travis-ci.org/caarlos0/antibody) [![Coverage Status](https://coveralls.io/repos/caarlos0/antibody/badge.svg?branch=master)](https://coveralls.io/r/caarlos0/antibody?branch=master) [![Stories in Ready](https://badge.waffle.io/caarlos0/antibody.png?label=ready&title=Ready)](https://waffle.io/caarlos0/antibody)

A faster and simpler version of antigen.

> "Antigen is a small set of functions that help you easily manage your shell
> (zsh) plugins, called bundles. The concept is pretty much the same as
> bundles in a typical vim+pathogen setup. Antigen is to zsh, what Vundle
> is to vim."
>
> Read more: [Antigen](https://github.com/zsh-users/antigen).

### Why?

Antigen is really nice. But it is bloated and it is slow - 5+ seconds to load
on my Mac... that's way too much to wait for a prompt to load!

I'm aware that there is other attempts, like
[antigen-hs](https://github.com/Tarrasch/antigen-hs), but I'm don't want to
install a lot of stuff for this to work.

So, why Go, you might ask.

Well, the compiled Go program runs anywhere and doesn't depend on any shared
libraries. I also don't need to source it as it would be necessary with
plain simple shell. I also can do stuff in parallel with Go routines.
The little amount of shell written is needed because I can't source
something from inside a Go program (or at least don't yet know how to do it).

### What works

These are only antigen commands I ever used:

- `bundle`
- `update`
- `apply`

Antibody does just those three things, but you don't even need to `apply`.
Running `antibody bundle` will already apply the bundle given bundle.

### What doesn't work

- Modules without a `*.plugin.zsh` file;
- Modules that are not in GitHub (you can open a PR if you wish);
- The `theme` command (although some themes might just work with bundle);
- oh-my-zsh support: it looks very ugly to me and I won't do it;

### Usage

- Download the [last release](https://github.com/caarlos0/antibody/releases/);
- Uncompress it somewhere;
- `source antibody.zsh`.

> **Attention**: the `antibody` binary file should not be in your `$PATH`.
> You only need to source the `antibody.zsh` file!

Now, you can just `antibody bundle` stuff, e.g.,
`antibody bundle Tarrasch/zsh-autoenv`. The repository will be cloned at
`~/.antibody` and all `.zsh.plugin` files will be loaded.

If you ever need to update your bundles, just run `antibody update`.

### Protips

Prefer to use it like this:

```sh
$ cat plugins.txt
caarlos0/jvm
djui/alias-tips
caarlos0/zsh-mkc
zsh-users/zsh-completions
caarlos0/zsh-open-github-pr
zsh-users/zsh-syntax-highlighting
zsh-users/zsh-history-substring-search

$ antibody bundle < plugins.txt
```

This way antibody can concurrently clone the bundles, so it may be faster!

### In the wild

- I did this mostly for myself, so, my
[dotfiles](https://github.com/caarlos0/dotfiles/pull/78);


### Throughput Graph

[![Throughput Graph](https://graphs.waffle.io/caarlos0/antibody/throughput.svg)](https://waffle.io/caarlos0/antibody/metrics)
