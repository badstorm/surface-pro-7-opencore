# Surface Pro 7 - macOS - OpenCore
---
OpenCore configuration for support macOS on Surface Pro 7

### Surface Specs
- Intel® Core™ i5-1035G4 Quad-Core
- 8 GB LPDDR4x RAM
- Intel® Iris™ Plus
- SSD 256 GB

### Releases

| Release |  OC  |  macOS  |
|---------|------|---------|
| 1663    | 0.63 | 10.15.5 / 11.0 |
| 1660    | 0.60 | 10.15.5 |
| 1559    | 0.59 | 10.15.5 |


### Status
|  Status             |         Feature                 |            Note                      |
|---------------------|---------------------------------|--------------------------------------|
|  :white_check_mark: |  Graphic Acceleration          |  QE/CI works, screen blinking at resolution 1368x912 scaled. WORKAROUND: Try change resolution |
|  :white_check_mark: |  Wifi & Bluetooth              |  With [OpenIntelWireless](https://github.com/OpenIntelWireless/itlwm) |
|  :white_check_mark: |  Type Cover  (keyboard/mouse)  |  With RHUB and VoodooI2C|                                 |
|  :white_check_mark: |  Audio                         |  With VoodooHDA   |
|                     |                                |                   |
|  :heavy_exclamation_mark: |  Battery Status          |                   | 


### Trackpad configuration
Trackpad works but macOS not find it in settings. You need to manaul configure it. Here my configuration:
```
sudo defaults write NSGlobalDomain com.apple.trackpad.forceClick -bool false
sudo defaults write com.apple.AppleMultitouchTrackpad ForceSuppressed -bool true
sudo defaults write com.apple.AppleMultitouchTrackpad ActuateDetents -bool false

sudo defaults write com.apple.AppleMultitouchTrackpad Clicking -bool true 
sudo defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true 
sudo defaults -currentHost write NSGlobalDomain com.apple.mouse.tapBehavior -int 1 
sudo defaults write NSGlobalDomain com.apple.mouse.tapBehavior -int 1

sudo defaults write com.apple.AppleMultitouchTrackpad Dragging -bool true 
sudo defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Dragging -bool true

# REBOOT
```
