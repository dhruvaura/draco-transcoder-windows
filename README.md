# Draco Transcoder for Windows

A step-by-step guide for building the Windows `draco_transcoder.exe` from Google's official Draco source.

This repository does not contain or redistribute the Google Draco source code.

## About

Google Draco is an open-source C++ library and compression framework for 3D geometric data.

The official Draco repository provides a `draco_transcoder` tool for transcoding glTF and GLB assets with Draco compression.

This guide explains how to build the Windows executable using:

* Google Draco 1.5.7
* CMake
* Visual Studio 2022
* MSVC C++ compiler
* Windows SDK

## Build Environment

* Operating System: Windows
* Architecture: x64
* Visual Studio: 2022
* CMake: Installed and available in PATH
* Workload: Desktop development with C++
* Compiler: MSVC
* Draco Version: 1.5.7

## Source Repository

The Draco source code is maintained by Google:

https://github.com/google/draco

This repository only provides the build guide and Windows build artifacts. The Draco source code is not copied into this repository.

## Build Overview

Clone the official Draco repository with its submodules:

```bash
git clone --recursive --branch 1.5.7 https://github.com/google/draco.git
cd draco
```

Create a build directory:

```bash
mkdir build
cd build
```

Configure the project using CMake with Draco transcoder support enabled:

```bash
cmake .. -DDRACO_TRANSCODER_SUPPORTED=ON
```

Build the project using Visual Studio:

```bash
cmake --build . --config Release
```

The resulting executable will be generated as:

```text
draco_transcoder.exe
```

The exact output location can depend on the Visual Studio/CMake generator configuration.

## What is draco_transcoder.exe?

The executable can be used as part of a GLB/glTF processing pipeline to apply Draco compression to mesh geometry.

For example, it can be integrated into a desktop application or add-in after the normal GLB export process.

## Runtime Handling

In our application, Draco compression is treated as an optional post-processing step.

If:

* `draco_transcoder.exe` is missing
* the executable fails
* the process exceeds the configured timeout

the original GLB is retained and the export process can continue with a warning.

## Release

Pre-built Windows binaries are provided through the GitHub Releases section.

Download the latest Windows x64 release:

[GitHub Releases](../../releases)

## License and Attribution

Draco is an open-source project maintained by Google.

Please refer to the official Draco repository for the applicable license and third-party notices:

https://github.com/google/draco

The compiled binaries distributed through this repository were built from the official Draco 1.5.7 source.

## Disclaimer

This repository is an independent build guide and distribution repository.

It is not an official Google repository.
