# node-ffprobe-installer

Platform independent binary installer of [FFprobe](https://ffmpeg.org/) for node projects. Useful for tools that should "just work" on multiple environments.

Installs a binary of `ffprobe` for the current platform and provides a path and version. Supports Linux, Windows and Mac OS/X.

A combination of package.json fields `optionalDependencies`, `cpu`, and `os` let's the installer only download the binary for the current platform. See also "Warnings during install", below.

## Install

    npm install --save @ffprobe-installer/ffprobe

## Usage examples

```javascript
const ffprobe = require('@ffprobe-installer/ffprobe');
console.log(ffprobe.path, ffprobe.version);
```

### process.spawn()

```javascript
const ffprobePath = require('@ffprobe-installer/ffprobe').path;
const spawn = require('child_process').spawn;
const ffprobe = spawn('ffprobePath', args);
ffprobe.on('exit', onExit);
```

### [fluent-ffmpeg](https://github.com/fluent-ffmpeg/node-fluent-ffmpeg)

```javascript
const ffprobePath = require('@ffprobe-installer/ffprobe').path;
const ffmpeg = require('fluent-ffmpeg');
ffmpeg.setFfprobePath(ffprobePath);
```

## Warnings during install

To automatically choose the binary to install, [optionalDependencies](https://docs.npmjs.com/files/package.json#optionaldependencies) are used. This currently outputs warnings in the console, an issue that is [tracked by the npm team here](https://github.com/npm/npm/issues/9567).

## The binaries

Downloaded from the sources listed at [ffmpeg.org](https://ffmpeg.org/download.html):

* Linux (20161109-g1bbb18f): https://www.johnvansickle.com/ffmpeg/
* Mac OS/X (82222-gcee1f4c): https://evermeet.cx/ffmpeg/
* Windows 32-bit (20161108-1bbb18f): https://ffmpeg.zeranoe.com/builds/win32/static/
* Windows 64-bit (20161108-1bbb18f): https://ffmpeg.zeranoe.com/builds/win64/static/

For version updates, submit issue or pull request.

## Upload new versions

In every updated `platforms/*` directory:

    npm run upload

## See also

* [node-ffmpeg-installer](https://www.npmjs.com/package/@ffmpeg-installer/ffmpeg) - This project is a fork of ffmpeg-installer
