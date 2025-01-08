# New Linux App

Welcome to the new version of our Linux application, now powered by Chromium Embedded Framework (CEF) and compiled with gcc/g++7. This README will help you get started with setting up and running the application.

## Table of Contents

- [New Linux App](#new-linux-app)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
    - [Using the .deb Package](#using-the-deb-package)
      - [Download the .deb Package:](#download-the-deb-package)
      - [Install the Package:](#install-the-package)
    - [Using the .tar.xz Archive](#using-the-tarxz-archive)
      - [Download the .tar.xz Archive:](#download-the-tarxz-archive)
      - [Extract the Archive:](#extract-the-archive)
  - [Troubleshooting](#troubleshooting)
    - [Additional Support](#additional-support)
  - [Previous Versions](#previous-versions)
## Introduction

This new version of our Linux app leverages the Chromium Embedded Framework (CEF) to provide a robust and modern web-based interface. CEF allows us to integrate web technologies seamlessly into our native application.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- **gcc/g++7**: The compiler used to build the application.
- **CMake**: A tool to manage the build process.
- **Git**: To clone the repository.
- **Dependencies**:
  - **glibc 2.27+**: The GNU C Library, providing core libraries essential for the application's runtime environment.
  - **libfreetype6**: A library for rendering text using TrueType fonts, crucial for text display within the application.
  - **libavformat/libavutil/libavcodec/libswscale**: Libraries from the FFmpeg project, enabling multimedia processing and playback capabilities.
  - **libasound2**: The ALSA library for sound support, ensuring audio output is managed correctly.
  - **libx11**: The X11 library, facilitating graphical interface interactions on Unix-like systems.
  - **libgles2-mesa**: The Mesa OpenGL ES 2.0 library, supporting hardware-accelerated graphics rendering.

You can install the necessary tools and dependencies on a Debian-based system using the following commands:

```sh
sudo apt update
sudo apt install libc6 libfreetype6 libavformat-dev libavutil-dev libavcodec-dev libswscale-dev libasound2 libx11-6 libgles2-mesa
```

## Installation
### Using the .deb Package

#### Download the .deb Package:
Download the .deb package from the releases page or the provided link.

#### Install the Package:
```sh
sudo dpkg -i path/to/AURGA.Viewer-xxx.deb
```

### Using the .tar.xz Archive
#### Download the .tar.xz Archive:
Download the .tar.xz archive from the releases page or the provided link.

#### Extract the Archive:
```sh
tar xvf path/to/AURGA.Viewer-xxx.xz
./aurgav/aurgav
```

## Troubleshooting
- **Issue**: Application crashes on startup.
  - **Solution**: Check the console output for more information. Ensure all prerequisites are installed. Run `sudo apt install build-essential cmake git libc6 libfreetype6 libavformat-dev libavutil-dev libavcodec-dev libswscale-dev libasound2 libx11-6 libgles2-mesa` if needed.

### Additional Support

If you encounter issues that are not resolved through the above steps, we recommend running the application and navigating to the home page. The home page provides detailed troubleshooting guides, FAQs, and links to our support forum where you can seek further assistance from our community and support team.


## Previous Versions
Notice: Previous versions of this application have been moved to the old_versions folder. If you need to access older releases, please navigate to this directory.

---

Thank you for using our new Linux app! If you have any questions or need further assistance, feel free to open an issue on our GitHub repository.
