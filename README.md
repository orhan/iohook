# My notes

## Building on Intel MAC

To get the build to progress using C++17, instead use this build command:
`CXXFLAGS="--std=c++17" node build.js --runtime electron --version 11.1.0 --abi 85 --upload=false`

See more: https://wilix-team.github.io/iohook/manual-build.html#macos

## Tweaks to support M2 build

First off, to get things working on arm64, had to update build.js as per: https://github.com/nodejs/node-gyp/issues/2673#issuecomment-1165324060

Next, my node was for some reason running as x64. If you could get it to run as arm64, you could probably just run the build script as above. Personally I couldn't get that working, so instead I overwrote build.js and manually included `let arch = 'arm64'`, after which the build seemed to work.

## After building

The output will be put into `prebuilds` folder. Open up the zip and copy paste the relevant build files over to the node_modules/iohook of your project.

## Publishing a new version

1. Make your change
2. Commit your change
3. `yarn publish` and bump version number
4. `git push` and check that the build github action completes succesfully

# iohook

[![NPM version](https://img.shields.io/npm/v/iohook?color=%230088FF)](https://www.npmjs.com/package/iohook)
[![Release date](https://img.shields.io/github/release-date/delewis13/iohook?color=%230088FF)](https://github.com/delewis13/iohook/releases/latest)
[![GitHub Super-Linter](https://github.com/delewis13/iohook/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)
[![CI](https://github.com/delewis13/iohook/actions/workflows/ci.yml/badge.svg)](https://github.com/delewis13/iohook/actions/workflows/ci.yml)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?color=%23008880)](https://github.com/prettier/prettier)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/iohookjs/Lobby)
[![Issues](https://img.shields.io/github/issues-raw/delewis13/iohook)](https://github.com/delewis13/iohook/issues)

## About

Node.js global native keyboard and mouse listener.

This module can handle keyboard and mouse events via native hooks inside and outside your JavaScript/TypeScript application.

Found a bug? Have an idea? Feel free to post an [issue](https://github.com/delewis13/iohook/issues) or submit a [PR](https://github.com/delewis13/iohook/pulls).

**Check out the [documentation](https://delewis13.github.io/iohook).**

## Platform support

- Versions >= 0.6.0 support only officially supported platforms versions.
- Versions 0.5.X are the last to support Electron < 4.0.0
- Versions 0.4.X are the last to support for Node < 8.0 and Electron < 2.0.0

## Installation

iohook provides prebuilt version for a bunch of OSes and platforms.

### Linux (including WSL)

```bash
# On Linux (including WSL) platform, you will need libxkbcommon-x11 installed
sudo apt-get install -y libxkbcommon-x11-0
```

### All platforms

```bash
npm install iohook --save # or yarn add iohook
```

## FAQ

Q. _Does this module require Java ?_

A. No, this module doesn't require Java (like jnativehook) or any other runtimes.

Q. _Is iohook compatible with Node/Electron version X.Y.Z ?_

A. We try to match the currently supported version of both [Node](https://nodejs.org/en/about/releases/) and [Electron](https://electronjs.org/docs/tutorial/support#currently-supported-versions).

## Apps

Are you using iohook in your project ? Please tell us in a [PR](https://github.com/delewis13/iohook/pulls) so we an add it to the list !

- [Cortex](https://crtx.gg/)
- [Tracklify](https://tracklify.com/)
- [CrewLink](https://github.com/ottomated/CrewLink)
- [Runtime](https://github.com/yikuansun/desktopspeedruntools#runtime-speedrun-tools)

## Contributors

Thanks to _kwhat_ for the [libuiohook](https://github.com/kwhat/libuiohook) project and [ayoubserti](https://github.com/ayoubserti) for the first iohook prototype.

- [vespakoen](https://github.com/vespakoen) (prebuild system implementation)
- [matthewshirley](https://github.com/matthewshirley) (Windows prebuild fix)
- [djiit](https://github.com/djiit) (project & community help)
- [ezain](https://github.com/eboukamza) (add feature enable/disable mouse click propagation)
- [anoadragon453](https://github.com/anoadragon453) (electron 4+ support)
- [ykhwong](https://github.com/ykhwong) (node-gyp usage, electron 9+ support)
- All the other contributors. Feel free to extend this list !
