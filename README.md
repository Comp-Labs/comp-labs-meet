# Comp Labs Meet

Desktop application for [Comp Labs Meet] built with [Electron] modified from [Jitsi Meet Electron App].

### Gallery
- **Windows Application ![](/assets/screenshot-windows.png)**
- **macOS Application ![](/assets/screenshot-macos.png)**
- **Linux Application ![](/assets/screenshot-linux.png)**
- **Deeplinks Support - Watch Video:**

<!-- <a href="https://youtu.be/3PPVo2Ltm1E"><img src="https://user-images.githubusercontent.com/86196753/144702305-72c50732-88d7-4c1c-b4c5-346ced84506e.jpg" width="250" height="131.5"></a> -->

<iframe width="512" height="256" src="https://www.youtube.com/embed/krqDiUuNd4g" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Features

- [End-to-End Encryption](https://jitsi.org/blog/e2ee/) support (BETA)
- Works with any Jitsi Meet deployment
- Builtin auto-updates
- ~Remote control~ (Currently [Disabled](https://github.com/jitsi/jitsi-meet-electron/issues/483) due to [Security Issues](https://github.com/jitsi/security-advisories/blob/master/advisories/JSA-2020-0001.md))
- Always-On-Top window
- Support for deeplinks such as `comp-labs-meet://mymeeting` (will open `mymeeting` on the configured Jitsi Server URL in the App) or `comp-labs-meet://meet.example.com/mymeeting` (will open `mymeeting` on the Jitsi Meet Server running on `meet.example.com`)

## Installation from Installers

Download our latest release and you're off to the races!

| Windows | macOS | GNU/Linux (AppImage) | GNU/Linux (Deb) | Linux (Snap) |
| -- | -- | -- | -- | -- |
| [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.exe) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.dmg) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet-x86_64.AppImage) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet-amd64.deb) | [Download](https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.snap) |

NOTE: The GNU/LInux builds are 64-bit only.

## Installation from Public App Stores

Windows             |  macOS             |  Linux
:------------------:|:------------------:|:-------------:
<a href="https://d2q0s6dlkh7kge.cloudfront.net/html/platform404.html"><img src="https://user-images.githubusercontent.com/86196753/144703138-6dc9f792-429c-4bfc-9318-37bb6fea628a.png" width="216" height="78"></a>  |  [![MAS](https://user-images.githubusercontent.com/86196753/144703193-4547d9d3-bc96-4cf3-a82f-00a0b26f3358.png)](https://d2q0s6dlkh7kge.cloudfront.net/html/platform404.html)  |  [![LSS](https://user-images.githubusercontent.com/86196753/144703091-f425d98c-27ae-4ec2-922b-bc96413c9b8b.png)](https://d2q0s6dlkh7kge.cloudfront.net/html/platform404.html)

**Not yet available on all the App Stores**

## Development

If you want to hack on this project, here is how you do it.

<details><summary>Show building instructions</summary>

#### Installing dependencies

Install Node.js 16 first (or if you use [nvm](https://github.com/nvm-sh/nvm), switch to Node.js 16 by running `nvm use`).

<details><summary>Extra dependencies for Windows</summary>

```bash
npm install --global --production windows-build-tools
```
</details>

<details><summary>Extra dependencies for GNU/Linux</summary>

X11, PNG and zlib development packages are necessary. On Debian-like systems then can be installed as follows:

```bash
sudo apt install libx11-dev zlib1g-dev libpng-dev libxtst-dev
```
</details>

Install all required packages:

```bash
npm install
```

#### Starting in development mode

```bash
npm start
```

The debugger tools are available when running in dev mode and can be activated with keyboard shortcuts as defined here https://github.com/sindresorhus/electron-debug#features.

It can also be displayed automatically from the `SHOW_DEV_TOOLS` environment variable such as:

```bash
SHOW_DEV_TOOLS=true npm start
```

or from the application `--show-dev-tools` command line flag.

#### Building the production distribution

```bash
npm run dist
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

#### Publishing

1. Create release branch: `git checkout -b release-1-2-3`, replacing 1-2-3 with the desired release version
2. Increment the version: `npm version patch`, replacing `patch` with `minor` or `major` as required
3. Push release branch to github: `git push -u origin release-1-2-3`
4. Create PR: `gh pr create`
5. Once PR is reviewed and ready to merge, create draft Github release: `gh release create v1.2.3 --draft --title 1.2.3`, replacing v1.2.3 and 1.2.3 with the desired release version
6. Merge PR
7. Github action will build binaries and attach to the draft release
8. Test binaries from draft release
9. If all tests are fine, publish draft release

</details>

### Customise this Application

If you want to customise this application with your own needs such as logo, meeting url, text change on the app, here's how you do it.

- Install [nodejs](https://nodejs.org/en/download) `Install the LTS version, not the Latest version as it produces problems.`
- Install [Git](https://git-scm.com/downloads) `Select your Operating System name and install it`
- Download the Latest Compressed Source Code from `https://github.com/comp-labs/comp-labs-meet/releases/latest/download/comp-labs-meet.zip`
- Extract the zip file and open a new terminal inside the directory
- Run `npm install && npm start` from the Terminal. The App should start.
- You can edit the Electron Source Files to Customize the Application.

## Known issues

### Windows

A warning will show up mentioning the app is unsigned upon first install. This is expected.

### macOS

On macOS Catalina and above versions, a warning will be displayed on first install. The app won't open unless "open" is pressed. This dialog is only shown once.

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

[Comp Labs Meet]: https://github.com/comp-labs/comp-labs-meet
[Electron]: https://electronjs.org/
[latest release]: https://github.com/comp-labs-meet/releases/latest
[jitsi-meet-electron-sdk]: https://github.com/jitsi/jitsi-meet-electron-sdk
[jitsi-meet-electron-sdk README]: https://github.com/jitsi/jitsi-meet-electron-sdk/blob/master/README.md
[Jitsi Meet Electron App]: https://github.com/jitsi/jitsi-meet-electron
[community forum]: https://community.jitsi.org/
[LICENSE]: LICENSE
