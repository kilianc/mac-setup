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



## install all apps

This script will symlink many of the shared config in the home folder, set the correct permissions and install a list of software from a brewfile.

```
~/Dropbox/Sync/dotfiles/install.sh
```

* iStat menu
* bartender
* brew install --cask visual-studio-code
  * login with github

## list of formulas

TODO

## setup chrome

TODO
