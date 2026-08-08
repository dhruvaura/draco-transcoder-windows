# Draco Transcoder Windows Build

A Windows x64 build of Google's Draco `draco_transcoder`, built from the official Draco 1.5.7 source using CMake and Visual Studio 2022.

This repository provides the build guide and a pre-built Windows executable through GitHub Releases.

## What is Draco?

[Google Draco](https://github.com/google/draco) is an open-source C++ library and compression framework for 3D geometric data.

Draco provides compression and decompression capabilities for 3D geometry and can be used with glTF and GLB workflows.

The official Draco project includes a `draco_transcoder` tool for glTF/GLB transcoding and Draco compression.

## About This Repository

The purpose of this repository is to document how I built the Windows version of:

```text
draco_transcoder.exe
```

from the official Google Draco 1.5.7 source.

The Google Draco source code is not copied into this repository.

This repository provides:

* Windows build instructions
* CMake configuration
* Visual Studio build information
* A pre-built Windows x64 executable
* Release package containing the executable and applicable Draco license

## Build Environment

The build was performed on Windows using:

| Component            | Version / Configuration     |
| -------------------- | --------------------------- |
| Draco                | 1.5.7                       |
| Programming Language | C++                         |
| Build System         | CMake                       |
| IDE                  | Visual Studio 2022          |
| Compiler             | Microsoft Visual C++ (MSVC) |
| Platform             | Windows x64                 |
| Transcoder           | `draco_transcoder`          |

## Requirements

Before building Draco on Windows, install:

### Visual Studio 2022

Install Visual Studio 2022 with:

* Desktop development with C++
* MSVC C++ compiler
* Windows SDK

### CMake

Install CMake and make sure it is available from the command line.

Verify:

```powershell
cmake --version
```

### Git

Git is required to download the Draco source together with its submodules.

Verify:

```powershell
git --version
```

## Download Draco 1.5.7

Clone the official Draco repository using the 1.5.7 tag and include its submodules:

```powershell
git clone --recursive --branch 1.5.7 https://github.com/google/draco.git
```

Move into the source directory:

```powershell
cd draco
```

The `--recursive` option downloads the required Git submodules.

## Configure the Build

Create a build directory:

```powershell
mkdir build
cd build
```

Configure Draco using CMake:

```powershell
cmake .. -DDRACO_TRANSCODER_SUPPORTED=ON
```

The important configuration option is:

```text
DRACO_TRANSCODER_SUPPORTED=ON
```

This enables the Draco transcoder.

## Build the Release Version

Build the Release configuration:

```powershell
cmake --build . --config Release
```

After a successful build, the Windows executable is generated in the Release output directory:

```text
draco_transcoder.exe
```

## Verify the Executable

Run:

```powershell
.\draco_transcoder.exe --help
```

The command should display the available transcoder options.

## Pre-built Windows Release

A pre-built Windows x64 version is available through GitHub Releases.

[Download the latest Windows release](https://github.com/dhruvaura/draco-transcoder-windows/releases)

The release package contains:

```text
draco-transcoder-win64-v1.5.7.zip
|
+-- draco_transcoder.exe
+-- LICENSE
```

The `draco.lib` file generated during the build is not included because it is not required to run the standalone transcoder executable.

## Example Workflow

A typical workflow can be:

```text
3D Model
   |
   v
GLB / glTF
   |
   v
draco_transcoder.exe
   |
   v
Draco-compressed GLB
   |
   v
Web / Unity / Unreal / AR / VR / Real-time 3D
```

Draco can be used as part of a GLB/glTF processing pipeline to reduce mesh geometry size.

## Why Draco Compression?

3D models can contain a significant amount of mesh geometry data.

Draco compression can help reduce the size of mesh geometry and can be useful for applications involving:

* 3D web viewers
* AR applications
* VR applications
* Real-time 3D applications
* Digital twins
* glTF / GLB pipelines
* Interactive 3D experiences

The compression result depends on the input model and transcoding configuration.

## Source

This build is based on the official Google Draco 1.5.7 source:

https://github.com/google/draco

Please refer to the official project for the original source code, documentation, license information, and project development.

## License

The Draco project is licensed under the terms provided by the official Draco repository.

The applicable Draco `LICENSE` file is included with the distributed Windows build.

This repository does not modify or replace the original Draco license.

## Disclaimer

This is an independent Windows build of the Google Draco project.

This repository is not an official Google repository and is not affiliated with Google.

The Draco source code remains available from the official project:

https://github.com/google/draco
