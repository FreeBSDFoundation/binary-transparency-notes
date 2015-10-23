# Binary Artifact Transparency Notes

This repository contains notes, documents and sample package metadata related
to the Binary Artifact Transparency project.

# Repository Directory Structure

## metadata

Sample package metadata from various operating systems.

## metadata/freebsd

FreeBSD package metadata, from http://pkg.freebsd.org/freebsd:11:x86:64/latest/
`packagesite.yaml` is the main metadata file for the entire package repository.
`sample.yaml` is a pretty-printed version of one package entry.

## metadata/debian

Debian package metadata, fetched from the apt repository at
http://ftp.us.debian.org/debian -- these are the files that would be
needed by a pure debian stable machine on the amd64 (x86_64) platform,
using an en_US locale.

### `Release` and `Release.gpg`
   
`Release` identifies the metadata for all platforms for a given
distribution.  `Release.gpg` is an OpenPGP signature on it.

This is the one place where the cryptographic authority of the Debian
Archive Signing Key is invoked.

### `main/Contents-amd64.gz`

this provides a list of all the files installed by any package in the
repository (seful for things like "file not found").  I don't think
anything in this file needs to be logged for binary transparency.

### `main/binary-amd64/Release` and `main/binary-all/Release`

Simple text file identifying the distribution, version, architecture,
etc.

### `main/binary-amd64/Packages.xz`

actual binary package metadata, including dependency information,
checksums, and short (one-line) descriptions for all packages
distributed to this architecture specifically.

### `main/binary-all/Packages.xz`

Same as the `main/binary-amd64/Packages.xz` but used for packages that
are architecture-independent (e.g. consisting only of scripts,
platform-indepenent data, documentation)
