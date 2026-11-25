# rushes-parts

FFmpeg and PHP, as [Rushes](https://github.com/x0on/rushes) uses them, built here from each project's own
source. Nobody stands between the source and the program: GitHub compiles it, in the open, from the recipe in
this repository, and every build is published with its fingerprint (SHA-256), the license texts it must carry,
and a list of exactly what went into it.

Why this exists: FFmpeg and PHP publish source code, not ready-made programs for the Mac. Rushes used programs
other people had compiled. Those were honest as far as anyone knows, but they could not be checked, and they
could not be updated when a security release came out and the compiler had not caught up. Here, a new release is
one changed version number.

## What is built

| Part | From | With | License of the result |
|---|---|---|---|
| **FFmpeg** (ffmpeg, ffprobe) | ffmpeg.org, the release's signed source | OpenH264 (Cisco), zlib; Apple's VideoToolbox and AudioToolbox from macOS | LGPL-2.1-or-later: no GPL part is built in |
| **PHP** (the `php` command) | php.net, by [static-php-cli](https://github.com/crazywhalecc/static-php-cli) | only what Rushes' pages use: SQLite, mbstring, ctype, session, filter, zip | PHP License 3.01 |

For Apple Silicon and Intel Macs. Each release here holds, for each chip: the program in a zip, `SHA256SUMS`,
`parts.json` (every source that went in, with its version, license and fingerprint) and `LICENSES`.

## How a build is made

The recipes are the two files in `.github/workflows`. To build a new version: change the version at the top of
the recipe, and push a tag (`ffmpeg-9.1-1`, `php-8.5.13-1`: the part, its version, and which build of it this
is). GitHub does the rest and publishes the release. Each recipe ends by running the programs the way Rushes
does (a proxy, a still, a catalogue query), so a build that compiles but does not work is not published.

## What is not here

No change to FFmpeg's or PHP's source: they are compiled as their projects publish them. Nothing of Rushes
itself, and nothing private.
