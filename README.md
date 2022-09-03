# My MacOS Setup

This repo contains info on all the apps / settings / tools I use on my Mac.

- [What Macbook do I have ?](#what-macbook-do-i-have)
- [Homebrew / Terminal / Shell](#homebrew--terminal--shell)
- [Install Some Brew Casks](#install-some-brew-casks)

## What Macbook do I have ?

I am using a M1 macbook pro 14" 2021. These are the specs at a glance:

* Apple M1 Pro
* 32GB Memory
* 1TB Flash Storage
* 10 cores (8 performance and 2 efficiency)
* macOS Monterey version 12.5

## Homebrew / Terminal / Shell

### Homebrew

[Homebrew](https://brew.sh/), THE missing package manager for macOS, allows us to install *the stuff we need* from the command line.

To install Homebrew, open up a terminal app and run the following command:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After homebrew installation is done, make sure to read the last few lines printed, there could be further steps needed to be done to complete the installation. 

### Terminal

The first app I like to install is to replace the built-in `Terminal` with [iTerm2](https://iterm2.com/). Check out their [documentation](https://iterm2.com/documentation.html) for more information on what it can do.

We can install this using a [Homebrew cask](https://github.com/Homebrew/homebrew-cask) for iterm2. 

> NOTE: a homebrew cask is a full application, similar to what we would install from the Apple store or when we download a DMG.

Run the following command in the terminal,

```sh
brew install iterm2
```

Once installed, close terminal (like completely, CMD+Q) and launch iterm2. Customize the settings / preference to your liking, you can do that by pressing `CMD+COMMA`. These are my preffered settings:

* General
    * Closing
        * Quit when all windows are closed
    * Window
        * Adjust window when changing font size
* Profiles
    * General
        * Working directory -> Reuse previous session's directory
    * Colors
        * Color Presets
            * Smoooooth
    * Text
        * Use thin strokes for anti-aliased text -> On Retina Displays
        * Font -> [Fira Code](https://github.com/tonsky/FiraCode)
        * Font Weight -> Retina
        * Font Size -> 24
    * Window
        * Transparency -> 25
        * Blur -> 10
        * Blending -> 50
        * Use transparency
    * Keys
        * Key Mappings -> Presets -> Natural Text Editing
            * this allows us to use keyboard shortcuts native to macOS. 

### Shell

Mac now comes with `zsh` as the default [shell](https://en.wikipedia.org/wiki/Comparison_of_command_shells). Linux users might prefer `bash` over zsh but I personally don't mind zsh for my development purposes.

The only customization I recommend is to install [Oh My Zsh](https://ohmyz.sh/). They've got great [documentation](https://github.com/ohmyzsh/ohmyzsh/wiki) on what they provide out of the box and on any customization you can add on top of things.

I like to run [aliases with my shell and Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet) provides a ton. I do add one other alias on top of this, which is for `cls`. Switching between a Windows machine at work and home development on mac can get annoying, this comes in handy. To add this alias, I assume you have already installed Oh My Zsh, head over to your `root` directory and look for a file called `.zshrc`. If you don't find this it's highly likely you are in the wrong directory or didn't install `Oh My Zsh` properly. Proceed to add the following to the file,

```sh
nano .zshrc

alias cls="clear"
```
write to file, save and exit. Now running `cls` in terminal will run clear command!

## Install Some Brew Casks

Here are a few casks I like to install, create a file called `casks.txt` inside a folder with the following contents:

```txt
app-cleaner
discord
keepingyouawake
keka
rectangle
sublime-text
visual-studio-code
vlc
```
Edit this list to be any brew cask you like,

> TIP: you can lookup if a brew casks exists using `brew search <cask name>`

Now, what we want to do is to install these casks, to do that, run the following command inside the same folder,

```sh
xargs brew install < casks.txt
```

Wait for installation to go through, once done, close iterm2. Few of the apps in here require a few more customizations, we will get to those later.

