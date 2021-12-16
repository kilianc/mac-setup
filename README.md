# mac-setup

Detailed setup instructions and automation for a quick machine setup.

# configure os

* Finder
  * show extensions
  * show folders on top
* Hot corners
  * TR: Notification Center
  * BR: Desktop
  * TL: Mission Control
  * BL: Lock Screen
* Dock
  * No recents
  * No downloads
  * Autohide
  * Remove all apps
* Apple id
  * Login in System Preferences and check App Store
  * Enable Desktop Sync: System Preferences > Apple ID > iCloud Options
* Touch id
  * Enable for unlock and purchases

## Enable 3 fingers drag

```
defaults write com.apple.AppleMultitouchTrackpad Dragging -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Dragging -bool true
```
```
defaults write com.apple.AppleMultitouchTrackpad TrackpadThreeFingerDrag -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadThreeFingerDrag -bool true
```

## Enable tap to click

```
defaults write com.apple.AppleMultitouchTrackpad Clicking -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true
defaults -currentHost write NSGlobalDomain com.apple.mouse.tapBehavior -int 1
```

N.B. This is currently resulting in a weird lag, I haven't found a solution yet.

## Adjust key repeat speed

https://mac-os-key-repeat.vercel.app/

```
defaults write -g ApplePressAndHoldEnabled -bool false
defaults write -g InitialKeyRepeat -int 12
defaults write -g KeyRepeat -int 1
```

## Install the `Dropbox` client

Go to https://www.dropbox.com/connect and use the iPhone app > Account > Connect a computer.

Configure selective sync and opt in on the `Sync` folder, then open Finder and right click on it to Smart Sync > Local.

## Install fonts

Open `Font Book` and drag in the fonts in `~/Dropbox/Sync/Fonts`.

## Install `Homebrew`

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install `iTerm2`

```
/opt/homebrew/bin/brew install --cask "iterm2"
```

* Open `iTerm` preferences
* Go to `General > Preferences > Browse`
* Select `~/Dropbox/Sync/iTerm2`
* Click `Don't Copy` (wipes local settings)
* Set `Save Changes` to `Automatically`
* Restart `iTerm`

# Install `XCode`

Open the `App Store` and install `XCode` from the developer section.

## install all apps

This script will symlink many of the shared config in the home folder, set the correct permissions and install a list of software from a brewfile.

```
~/Dropbox/Sync/dotfiles/install.sh
```

Follow ups:

* `1Password`: use the iPhone QR code to sign-in and verify access to passwords and licenses
* `iStat Menus`: load settings from `iStat Menus Settings.ismp`
* `Bartender`: TODO: looking for a way to export/import settings
* `Alfred`: activate license, set macOS permissions and set the preferences folder to `~/Dropbox/Sync/Alfred`

## Setup chrome

* Create a persona and login on work account
* Create a persona and login on personal account

## Replace Spotlight with Alfred

See https://superuser.com/questions/1211108/remove-osx-spotlight-keyboard-shortcut-from-command-line/1688991#1688991

Disable `"Show Spotlight search"` hotkey:

```sh
/usr/libexec/PlistBuddy ~/Library/Preferences/com.apple.symbolichotkeys.plist \
  -c "Delete :AppleSymbolicHotKeys:64" \
  -c "Add :AppleSymbolicHotKeys:64:enabled bool false" \
  -c "Add :AppleSymbolicHotKeys:64:value:parameters array" \
  -c "Add :AppleSymbolicHotKeys:64:value:parameters: integer 65535" \
  -c "Add :AppleSymbolicHotKeys:64:value:parameters: integer 49" \
  -c "Add :AppleSymbolicHotKeys:64:value:parameters: integer 1048576" \
  -c "Add :AppleSymbolicHotKeys:64:type string standard"
```

Disable `"Show Finder search window"` hotkey:

```sh
/usr/libexec/PlistBuddy ~/Library/Preferences/com.apple.symbolichotkeys.plist \
  -c "Delete :AppleSymbolicHotKeys:65" \
  -c "Add :AppleSymbolicHotKeys:65:enabled bool false" \
  -c "Add :AppleSymbolicHotKeys:65:value:parameters array" \
  -c "Add :AppleSymbolicHotKeys:65:value:parameters: integer 65535" \
  -c "Add :AppleSymbolicHotKeys:65:value:parameters: integer 49" \
  -c "Add :AppleSymbolicHotKeys:65:value:parameters: integer 1572864" \
  -c "Add :AppleSymbolicHotKeys:65:type string standard"
```

Open `Alfred` preferences and change the shortcut back to `⌘ + ⎵`
