# Overwrite default settings

## Speed up the dock responses
- Change the autohide value
```shell
defaults write com.apple.dock autohide-delay -float 0;
defaults write com.apple.dock autohide-time-modifier -float 0.65;
killall Dock
```

- Undo  changes
```shell
defaults delete com.apple.dock autohide-time-modifier;
defaults delete com.apple.dock autohide-delay;
killall Dock
```

- Source: https://macos-defaults.com/dock/autohide-delay.html#set-to-0-5-default-value

## Keep folders on top

- Read current value
```shell
defaults read com.apple.finder "_FXSortFoldersFirst"
```

- Keep folders on top when sorting by name
```shell
defaults write com.apple.finder "_FXSortFoldersFirst" -bool "true" && killall Finder
```

- Undo changes
```shell
defaults write com.apple.finder "_FXSortFoldersFirst" -bool "false" && killall Finder
```

- Reset changes
```shell
defaults delete com.apple.finder "_FXSortFoldersFirst" && killall Finder
```

- Source: https://macos-defaults.com/finder/_fxsortfoldersfirst.html#set-to-true

## # Changing file extension warning

- Read current value
```shell
defaults read com.apple.finder "FXEnableExtensionChangeWarning"
```

- Display a warning when changing a file extension in the Finder
```shell
defaults write com.apple.finder "FXEnableExtensionChangeWarning" -bool "true" && killall Finder
```

- Do not display the warning
```shell
defaults write com.apple.finder "FXEnableExtensionChangeWarning" -bool "false" && killall Finder
```

- Reset to default value
```shell
defaults delete com.apple.finder "FXEnableExtensionChangeWarning" && killall Finder
```

- Source: https://macos-defaults.com/finder/fxenableextensionchangewarning.html
