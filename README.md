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
defaults write com.apple.AppleMultitouchTrackpad TrackpadThreeFingerDrag -bool true

defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Dragging -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadThreeFingerDrag -bool true
```

## enable tap to click

```
defaults write com.apple.AppleMultitouchTrackpad Clicking -bool true
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true
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

## manual install

* install `Homebrew`: https://brew.sh/
* install the `Dropbox` client: https://www.dropbox.com/install
  * in preferences make sure the `Sync` folder is selected

## automatic install

This script will symlink many of the shared config in the home folder, set the correct permissions and install a list of software from a brewfile

    ~/Dropbox/Sync/dotfile/install.sh

## list of formulas

TODO

## setup chrome

TODO
