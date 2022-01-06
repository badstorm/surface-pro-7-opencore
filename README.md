# Surface Pro 7 - macOS - OpenCore
---
OpenCore configuration for support macOS on Surface Pro 7


### Surface Specs
- Intel® Core™ i5-1035G4 Quad-Core
- 8 GB LPDDR4x RAM
- Intel® Iris™ Plus
- SSD 256 GB


### Status
|  Status             |         Feature                 |            Note                      |
|---------------------|---------------------------------|--------------------------------------|
|  :white_check_mark: |  Graphic Acceleration          |  QE/CI works |
|  :white_check_mark: |  Wifi & Bluetooth              |  With [OpenIntelWireless](https://github.com/OpenIntelWireless/itlwm) |
|  :white_check_mark: |  Type Cover  (keyboard/mouse)  |  With RHUB and VoodooI2C|                                 |
|  :white_check_mark: |  Audio                         |  With AppleALC   |
|                     |                                |                   |
|  :heavy_exclamation_mark: |  Battery Status          |                   | 
|  :heavy_exclamation_mark: |  Camera Front and Rear        |                   | 


### Install Notes
- Type Cover works but macOS Installer ask for a keyboard/mouse. For install macOS use a USB keyboard/mouse
- For a better Wifi experience, use **itlwm** instead of **AirportItlwm** with [HeliPort](https://github.com/OpenIntelWireless/HeliPort) (Simple enable/disable them in `config.plist`)

### Trackpad configuration
Trackpad works but macOS not find it in settings. You need to manaul configure it. Here my configuration:
```
// This configuration works for me, but someone make it work removing sudo

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

### Secure Boot
If you want to boot without the anoing red bar with the lock icon you can try [this workaround](https://github.com/badstorm/surface-pro-7-opencore/blob/master/SecureBoot.With.Grub.md). *Thanks to @Xiashangning* 
