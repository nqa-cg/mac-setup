# My MacOS Setup

This repo contains info on all the apps / settings / tools I use on my Mac.

- [What Macbook do I have ?](#what-macbook-do-i-have)
- [Homebrew / Terminal / Shell](#homebrew--terminal--shell)
- [Install Some Brew Casks](#install-some-brew-casks)
- [OS Settings](#os-settings)
- [Browser](#browser)
- [Node.JS](#nodejs)
- [VS Code](#vs-code)
- [Alfred](#alfred)
- [Github setup](#github-setup)

## What Macbook do I have ?

I am using a M1 macbook pro 14" 2021. These are the specs at a glance:

- Apple M1 Pro
- 32GB Memory
- 1TB Flash Storage
- 10 cores (8 performance and 2 efficiency)
- macOS Monterey version 12.5

## Homebrew / Terminal / Shell

### Homebrew

[Homebrew](https://brew.sh/), THE missing package manager for macOS, allows us to install _the stuff we need_ from the command line.

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

- General
  - Closing
    - Quit when all windows are closed
  - Window
    - Adjust window when changing font size
- Profiles
  - General
    - Working directory -> Reuse previous session's directory
  - Colors
    - Color Presets
      - Smoooooth
  - Text
    - Use thin strokes for anti-aliased text -> On Retina Displays
    - Font -> [Fira Code](https://github.com/tonsky/FiraCode)
    - Font Weight -> Retina
    - Font Size -> 24
  - Window
    - Transparency -> 25
    - Blur -> 10
    - Blending -> 50
    - Use transparency
  - Keys
    - Key Mappings -> Presets -> Natural Text Editing
      - this allows us to use keyboard shortcuts native to macOS.

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
alfred
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

## OS Settings

These are my preferred settings:

### Finder

- Finder -> Preferences
  - General -> Show these items on desktop -> Select None
  - General -> New finder windows show -> Home folder
  - Tags -> Select None
  - Sidebar -> Show these items in the sidebar -> Select Desktop, Documents, Downloads, Home folder, Locations (all except primary hdd)
  - Advanced -> Show all filename extensions
  - Advanced -> Show warning before changing an extension -> No
  - Advanced -> When performing a search -> Search the current folder
- View
  - Show Sidebar
  - Show Preview
  - Show Toolbar
  - Show Tab Bar
  - Show Path Bar

### Dock

I don't use the Dock at all. It takes up screen space, and I can use Spotlight Search to launch apps. I make the dock as small as possible and auto hide it.

- System Preferences
  - Dock & Menu Bar
    - Size -> Small as possible
    - Position on screen -> Right
    - Automatically hide and show the Dock -> Yes

### Trackpad

- System Preferences
  - Trackpad -> Point and Click
    - Enable Tap to click
  - Trackpad -> More Gestures
    - App Expose
  - Accessibility -> Pointer Control -> Trackpad Options
    - Enable dragging -> Three finder drag

### Menu Bar Customization

Items from left to right are supposed to be as follows:

1. Keep you awake
2. Rectangle
3. Bluetooth
4. Battery
5. Control Center
6. Date
7. Time

- System Preferences -> Dock and Menu Bar
  - Wifi -> Don't show in menu bar
  - Bluetooth -> Show in menu bar
  - Battery -> Show Percentage
  - Clock -> Date Options
    - Show the day of the week
  - Clock -> Time Options
    - Show AM/PM
    - Display the time with seconds
  - Spotlight -> Don't show in menu bar

## Browser

[Install chrome](https://www.google.com/chrome/downloads/) and setup chrome profiles. Apart from base chrome the only other browser extension I use is [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en).

## Node.JS

I use nvm to manage the installed versions of Node.js on my machine. This allows me to easily switch between Node.js versions depending on the project I'm working in.

See installation instructions [here](https://github.com/nvm-sh/nvm#installing-and-updating).

OR run this command (make sure v0.39.1 is still the latest)

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

After installation you'll want to add the following to your .bash_profile / .zshrc etc.

```sh
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

Now that nvm is installed, you can install a specific version of node.js and use it:

```sh
nvm install node
nvm ls
nvm use node
node --version
```

## VS Code

VS Code was installed in [this section](#install-some-brew-casks), if you skipped it run the following command

```sh
brew install visual-studio-code
```

Once installed, open the app and head over to the `Extensions` tab on the left side panel and look for the following packages and install them:

1. Code Spell Checker - `streetsidesoftware.code-spell-checker`
2. Dotenv Official - `dotenv.dotenv-vscode`
3. ES Lint - `dbaeumer.vscode-eslint`
4. FontSize Shortcuts - `fosshaas.fontsize-shortcuts`
5. Git Lens - `eamodio.gitlens`
6. Material Icon Theme - `PKief.material-icon-theme`
7. Material Theme - `Equinusocio.vsc-material-theme`
8. Prettier - `esbenp.prettier-vscode`

Once installed, we now need to update settings for these extensions, first step is to copy the following config

- CMD+SHIFT+P -> Open User Settings (JSON)

paste the following in there

```json
{
  "workbench.colorTheme": "Material Theme Ocean High Contrast",
  "editor.formatOnPaste": true,
  "editor.formatOnSave": true,
  "prettier.requireConfig": true,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "window.zoomLevel": 2,
  "editor.minimap.enabled": false,
  "explorer.confirmDelete": false,
  "workbench.iconTheme": "material-icon-theme",
  "editor.fontLigatures": true,
  "editor.fontFamily": "FiraCode-Retina, Menlo, Monaco, 'Courier New', monospace",
  "editor.fontWeight": "450",
  "workbench.colorCustomizations": {
    "[Material Theme Ocean High Contrast]": {}
  },
  "editor.linkedEditing": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  }
}
```

I also prefer setting the `Material Theme: Set Accent Color` as `Teal`

## Alfred

Alfred was installed in [this section](#install-some-brew-casks), if you skipped it run the following command

```sh
brew install --cask alfred
```

Once installed, open alfred and `Begin Setup`. Don't bug powerpack and skip that step. Give alfred access to accessibility and file disk.

Now you want to change the shortcut to open alfred to `CMD + Space`, to do that, open

- System Preferences -> Keyboard -> Shortcuts -> Spotlight -> uncheck all shortcuts

Now open alfred, open alfred settings by hitting `CMD + comma`

- General -> Alfred Hotkey -> `CMD + Space`

> TIP: use `'` or `CMD + Space + Space` to lookup folders or files
> TIP: to open the finder location where a file is located, hit `CMD + Enter`

### Alfred Preferences

1. Features -> Web Search

- change google to `g`
- change maps to `m`
- apple maps -> ☐ enabled
- change youtube to `yt`
- add giphy
  - add custom search
  - search URL: `https://giphy.com/search/{query}`
  - encode spaces: `-`
  - title: `Giphy`
  - keyword: `gif`
  - download giphy icon and set it as custom search icon

2. Features -> System

- Empty Trash -> ✅ confirm
- Restart -> ✅ confirm
- Shutdown -> ✅ confirm
- Volume up -> ☐
- Volume down -> ☐

3. Appearance

- Alfred macOS Dark
- Options -> Hide Hat on Alfred Window
- Options -> I want to see -> 5

## Github setup

Github should be installed on your terminal. If not go set that up first, follow [these steps](https://cli.github.com/manual/installation).

Now, I prefer github integrated via SSH, before we do that, we need to setup github account globally on this machine.

```sh
git config --global user.name "Naman Avasthi"
git config --global user.name

git config --global user.email "naman.avasthi@gmail.com"
git config --global user.email
```

optionally, you can also set the default init branch for any repo by

```sh
git config --global init.defaultBranch main
git config --global user.defaultBranch
```

Now, lets start setting up our ssh connection with our github account. Please follow [these docs by github on ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh).

First step is to establish a ssh key on your local machine, this is going to generate a public and private key and we are going to expose the public key in our github profile online.

```sh
ssh-keygen -t ed25519 -C “naman.avasthi@gmail.com"

Generating public/private algorithm key pair.
Enter a file in which to save the key (/Users/YOU/.ssh/id_algorithm): [Press enter]
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```

Make sure you remember what passphrase you use, I'd recommend to leave this empty otherwise accessing public or private key can get annoying.

Now, we want to copy the public key generated,

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

Head over to [github.com](https://github.com/) and login

- Click profile picture on top-left -> settings
- Access -> SSH and GPG keys -> New SSH Key

Give a suitable title, Key type will be `Authentication Key` and inside the Key text field, paste the public key already copied with the last command we ran.
Hit Add SSH Key and you are all set!
