# mac-setup
Detailed setup instructions and automation for a quick machine setup

# configure os

## finder

show extensions
folders on top

## sign in with apple id

TODO

## setup touch id

TODO

## enable 3 fingers drag

```
defaults write com.apple.AppleMultitouchTrackpad Dragging -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Dragging -bool true
```
```
defaults write com.apple.AppleMultitouchTrackpad TrackpadThreeFingerDrag -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadThreeFingerDrag -bool true
```

## enable tap to click

```
defaults write com.apple.AppleMultitouchTrackpad Clicking -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true
defaults -currentHost write NSGlobalDomain com.apple.mouse.tapBehavior -int 1
```

## adjust key repeat speed

https://mac-os-key-repeat.vercel.app/

```
defaults write -g ApplePressAndHoldEnabled -bool false
defaults write -g InitialKeyRepeat -int 10
defaults write -g KeyRepeat -int 1
```

## configure hot corners

TODO

## configure dock

TODO

# install software

## install the `Dropbox`

https://www.dropbox.com/install

## install fonts

Open `Font Book` and drag in the fonts in `~/Dropbox/Sync/Fonts`

## install brew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## install `iTerm2`

```
/opt/homebrew/bin/brew install --cask "iterm2"
```

* Open `iTerm` preferences
* Go to `General > Preferences > Browse`
* Select `~/Dropbox/Sync/iTerm2`
* Click `Don't Copy` (wipes local settings)
* Set `Save Changes` to `Automatically`
* Restart `iTerm`

# install `XCode`

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

## Replace Spotlight with Alfred

See https://superuser.com/questions/1211108/remove-osx-spotlight-keyboard-shortcut-from-command-line/1688991#1688991

Disable "Show Spotlight search" hotkey

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

Disable "Show Finder search window" hotkey

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

## list of formulas

TODO

## setup chrome

TODO
