# Comp Labs Meet

Desktop application for [Comp Labs Meet] built with [Electron] modified from [Jitsi Meet Electron App].

### Gallery
- Windows Application ![](/assets/screenshot-windows.png)
- macOS Application ![](/assets/screenshot-macos.png)
- Linux Application ![](/assets/screenshot-linux.png)
- Deeplinks Support shown on macOS but works on all platforms. ![](/assets/deeplinks.mp4)

## Features

- [End-to-End Encryption](https://jitsi.org/blog/e2ee/) support (BETA)
- Works with any Jitsi Meet deployment
- Builtin auto-updates
- ~Remote control~ (currently [disabled](https://github.com/jitsi/jitsi-meet-electron/issues/483) due to [security issues](https://github.com/jitsi/security-advisories/blob/master/advisories/JSA-2020-0001.md))
- Always-On-Top window
- Support for deeplinks such as `comp-labs-meet://myroom` (will open `myroom` on the configured Jitsi instance) or `comp-labs-meet://jitsi.mycompany.com/myroom` (will open `myroom` on the Jitsi instance running on `jitsi.mycompany.com`)

## Installation

Download our latest release and you're off to the races!

| Windows | macOS | GNU/Linux (AppImage) | GNU/Linux (Deb) | Linux (Snap) |
| -- | -- | -- | -- | -- |
| [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.exe) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.dmg) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet-x86_64.AppImage) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet-amd64.deb) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.snap) |

NOTE: The GNU/LInux builds are 64-bit only.

### Third-Party builds

<iframe src="https://snapcraft.io/comp-labs-meet/embedded?button=black&channels=true" frameborder="0" width="100%" height="520px" style="border: 1px solid #CCC; border-radius: 2px;"></iframe>

**Yet to be published**

## Development

If you want to hack on this project, here is how you do it.

**Building instructions**

#### Installing dependencies

Install Node.js 16 first (or if you use [nvm](https://github.com/nvm-sh/nvm), switch to Node.js 16 by running `nvm use`).

**Extra dependencies for Windows**

```bash
npm install --global --production windows-build-tools
```

**Extra dependencies for GNU/Linux**

X11, PNG and zlib development packages are necessary. On Debian-like systems then can be installed as follows:

```bash
sudo apt install libx11-dev zlib1g-dev libpng-dev libxtst-dev
```

Install all required packages:

```bash
npm install
```

#### Working with jitsi-meet-electron-sdk

[jitsi-meet-electron-sdk] is a helper package which implements many features
such as remote control and the always-on-top window. If new features are to be
added / tested, running with a local version of these utils is very handy, here
is how to do that.

By default the @jitsi/electron-sdk is build from npm. The default dependency path in package.json is:

```json
"@jitsi/electron-sdk": "^3.0.0"
```

To work with local copy you must change the path to:

```json
"@jitsi/electron-sdk": "file:///Users/name/jitsi-meet-electron-sdk-copy",
```

To build the project you must force it to take the sources as `npm update` will
not do it.

```bash
npm install @jitsi/electron-sdk --force
```

NOTE: Also check the [jitsi-meet-electron-sdk README] to see how to configure
your environment.


## Known issues

### Windows

A warning will show up mentioning the app is unsigned upon first install. This is expected.

### macOS

On macOS Catalina a warning will be displayed on first install. The app won't open unless "open" is pressed. This dialog is only shown once.

### GNU/Linux

If after downloading it, you can't execute the file directly, try running `chmod u+x ./jitsi-meet-x86_64.AppImage`

**NOTE for old GNU/Linux distributions**

You might get the following error:

```
FATAL:nss_util.cc(632)] NSS_VersionCheck("3.26") failed. NSS >= 3.26 is required.
Please upgrade to the latest NSS, and if you still get this error, contact your
distribution maintainer.
```

If you do, please install NSS (example for Debian / Ubuntu):

```bash
sudo apt-get install libnss3
```

## Translations

The json files are for all the strings inside the application and can be translated [here](/app/i18n/lang).

New translations require the addition of a line in [index.js](/app/i18n/index.js).

`Localize desktop file on linux` requires the addition of a line in [package.json](/package.json).
Please search for `Comment[hu]` as an example to help add your translation of the English string `Jitsi Meet Desktop App` for your language.

## License

MIT License. See the [LICENSE] file.

## Community

Jitsi is built by a large community of developers, if you want to participate,
please join [community forum].

[Comp Labs Meet]: https://github.com/comp-labs-meet
[Electron]: https://electronjs.org/
[latest release]: https://github.com/comp-labs-meet/releases/latest
[jitsi-meet-electron-sdk]: https://github.com/jitsi/jitsi-meet-electron-sdk
[jitsi-meet-electron-sdk README]: https://github.com/jitsi/jitsi-meet-electron-sdk/blob/master/README.md
[Jitsi Meet Electron App]: https://github.com/jitsi/jitsi-meet-electron
[community forum]: https://community.jitsi.org/
[LICENSE]: LICENSE
