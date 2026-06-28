# HoRNDIS — Android USB tethering driver for Mac OS X and macOS

**HoRNDIS** (pronounce: *"horrendous"*) is a driver for Mac OS X and macOS that allows you to use your Android phone's native [USB tethering](http://en.wikipedia.org/wiki/Tethering) mode to get Internet access. Intel only.

> **Note:** On macOS 11 (Big Sur) and later, HoRNDIS requires disabling kext signing in SIP. See [SIP configuration](#sip-configuration) below.

## Supported versions

| Version | Name |
|---|---|
| OS X 10.11 | El Capitan |
| OS X 10.12 | Sierra |
| OS X 10.13 | High Sierra |
| OS X 10.14 | Mojave |
| OS X 10.15 | Catalina |
| macOS 11 | Big Sur |
| macOS 12 | Monterey |
| macOS 13 | Ventura |
| macOS 14 | Sonoma |
| macOS 15 | Sequoia |

⚠️ macOS 26 (Tahoe) and Apple Silicon are not supported.

## SIP configuration

*Required for macOS 11 and later only.*

Since macOS Big Sur (11), Apple requires kexts to be signed with a certificate that is no longer issued to new developers. To load HoRNDIS, kext signing must be disabled in SIP:

1. Shut down your Mac
2. Boot into Recovery Mode (hold **Cmd+R** on Intel Macs)
3. Open **Utilities → Terminal** and run:
   ```sh
   csrutil enable --without kext
   ```
4. Restart

## Installation

* Download the `.pkg` from the [Releases](../../releases) page and run the installer
* If macOS blocks the extension: go to **System Settings → Privacy & Security** and click **Allow**

## Configuration

* Connect your phone to your Mac by USB
* On your Android phone, open **Settings** and navigate to the network or hotspot section (the exact path varies by manufacturer and Android version)
* Enable **USB tethering**
* The connection should appear automatically in your Mac's network settings

## Uninstallation

```sh
sudo kextunload /Library/Extensions/HoRNDIS.kext
sudo rm -rf /Library/Extensions/HoRNDIS.kext
```

## Building the source

* `git clone` the repository
* Run `make` to build and package (requires Xcode)

## Credits

* **Joshua Wise** (2012)
* **Mikhail Iakhiaev** (2018)
* **H. Hugo** ([Apheleos](https://github.com/Apheleos)) (2026)
