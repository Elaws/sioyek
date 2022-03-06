# Modifications from original Sioyek repo

- [0ce19d6](https://github.com/Elaws/sioyek/commit/0ce19d63f00716d1fd20d8c76d6baafbe6f0f573) 

Windows positions/sizes are saved between each `toggle_window_configuration` command. Command to be defined in *keys_user.config*.

- [c9b33ae](https://github.com/Elaws/sioyek/commit/c9b33ae3734b59d87e302c8b57dd73b64016682b)

Added "- Sioyek" to window title (for compatibility with some AHK scripts that require software name in window title).

- [f31250](https://github.com/Elaws/sioyek/commit/f3125067582fe1ab1bdfa713f903c206c319bdfd)

`copy_window_size_config` command (*keys_user.config*) also saves windows positions/sizes to *prefs_user.config*, so that windows positions are remembered at Sioyek startup. First, following configuration must be added to *prefs_user.config* (customize with your screen's dimensions), then everything is automatic :

\# Config when using a single window
single_main_window_size 1920 1017
single_main_window_move 0 0

\# Config with helper window
main_window_size 958 1008
main_window_move 0 0
helper_window_size 958 1008
helper_window_move 960 0

- [e23719](https://github.com/Elaws/sioyek/commit/e23719b61132d3d38253f2cae6b11b6fe45ba6ab)

If windows positions are not yet configured in *prefs_user.config*, `toggle_window_configuration` defaults to splitting the screen in two to display helper window, instead of trying to launch it on the second monitor (which may fail under special circumstances if not other checks are made, as currently).

- [5bccec](https://github.com/Elaws/sioyek/commit/5bcce4cec5c357a899ede3801129fbd273e7b97b)

Fix (workaround) for helper window not recovering proper position when snapped.

- [91c7ef](https://github.com/Elaws/sioyek/commit/91c7eff3794ac9f98ba3b86020af6f52cb9ab936)

Maj + scroll now goes to next/previous page.

- [b5fdb1](https://github.com/Elaws/sioyek/commit/b5fdb1646bacbbeddee708c3f4e7e0f7059139b0)

Compatibility with Zotero's "open-pdf/[...]?page=i" links !

- [e57d23](https://github.com/Elaws/sioyek/commit/e57d238dcf5614c6109bd605530e984c7171b0e5)

Several custom color modes with `apply_custom_color` command (*keys_user.config*) : <S-c> (or any key combination of your choice) + `letter`. 26 commands (from a to z) so as many possible color modes ! Define color modes in *prefs_user.config* :

## For scores (Yellow background / ochre text)
custom_background_color_a    0.59 0.51 0.37
custom_text_color_a    0.02 0.03 0.04

## "A la" Sublime Text (Dark blue-ish background / white text)
custom_background_color_b    0.20 0.24 0.27
custom_text_color_b    0.85 0.87 0.91

As with original Sioyek, wwitch between custom color mode and normal using `toggle_custom_color` command (*keys_user.config*).

---
# Sioyek

Sioyek is a PDF viewer designed for reading research papers and technical books.
## Contents
* [Installation](#install)
* [Documentation](#documentation)
* [Video Demo](#feature-video-overview)
* [Features](#features)
* [Build Instructions](#build-instructions)

## Install
### Official packages
There're installers for Windows, macOS and Linux. See [Releases page](https://github.com/ahrm/sioyek/releases).

### Third-party packages for Linux
If you prefer to install sioyek with a package manager, you can look at this list. Please note that they are provided by third party packagers. USE AT YOUR OWN RISK! If you're reporting a bug for a third-party package, please mention which package you're using.

Distro | Link | Maintainer
------- | ----- | -------------
Arch | [AUR Sioyek-git](https://aur.archlinux.org/packages/sioyek-git/) | [@randomn4me](https://github.com/randomn4me)  
Fedora | [Copr endle/sioyek](https://copr.fedorainfracloud.org/coprs/endle/sioyek/) | [@Endle](https://github.com/Endle)  

## Documentation
You can view the official documentation [here](https://sioyek-documentation.readthedocs.io/en/latest/) .
## Feature Video Overview

[![Sioyek feature overview](https://img.youtube.com/vi/yTmCI0Xp5vI/0.jpg)](https://www.youtube.com/watch?v=yTmCI0Xp5vI)

## Features

### Quick Open

https://user-images.githubusercontent.com/6392321/125321111-9b29dc00-e351-11eb-873e-94ea30016a05.mp4

You can quickly search and open any file you have previously interacted with using sioyek.

### Table of Contents

https://user-images.githubusercontent.com/6392321/125321313-cf050180-e351-11eb-9275-c2759c684af5.mp4

You can search and jump to table of contents entries.

### Smart Jump

https://user-images.githubusercontent.com/6392321/125321419-e5ab5880-e351-11eb-9688-95374a22774f.mp4

You can jump to any referenced figure or bibliography item *even if the PDF file doesn't provide links*. You can also search the names of bibliography items in google scholar/libgen by middle clicking/shif+middle clicking on their name.

### Overview

https://user-images.githubusercontent.com/6392321/154683015-0bae4f92-78e2-4141-8446-49dd7c2bd7c9.mp4

You can open a quick overview of figures/references/tables/etc. by right clicking on them (Like Smart Jump, this feature works even if the document doesn't provide links).

### Mark

https://user-images.githubusercontent.com/6392321/125321811-505c9400-e352-11eb-85e0-ffc3ae5f8cb8.mp4

Sometimes when reading a document you need to go back a few pages (perhaps to view a definition or something) and quickly jump back to where you were. You can achieve this by using marks. Marks are named locations within a PDF file (each mark has a single character name for example 'a' or 'm') which you can quickly jump to using their name. In the aforementioned example, before going back to the definition you mark your location and later jump back to the mark by invoking its name. Lower case marks are local to the document and upper case marks are global (this should be very familiar to you if you have used vim).

### Bookmarks

https://user-images.githubusercontent.com/6392321/125322503-1a6bdf80-e353-11eb-8018-5e8fc43b8d05.mp4

Bookmarks are similar to marks except they are named by a text string and they are all global.

### Highlights


https://user-images.githubusercontent.com/6392321/130956728-7e0a87fa-4ada-4108-a8fc-9d9d04180f56.mp4


Highlight text using different kinds of highlight, you can search among all the highlights.

### Portals (this feature is most useful for users with multiple monitors)



https://user-images.githubusercontent.com/6392321/125322657-41c2ac80-e353-11eb-985e-8f3ce9808f67.mp4

Suppose you are reading a paragraph which references a figure which is not very close to the current location. Jumping back and forth between the current paragraph and the figure can be very annoying. Using portals, you can link the paragraph's location to the figure's location. Sioyek shows the closest portal destination in a separate window (which is usually placed on a second monitor). This window is automatically updated to show the closest portal destination as the user navigates the document.


### Configuration


https://user-images.githubusercontent.com/6392321/125337160-e4832700-e363-11eb-8801-0bee58121c2d.mp4

You can customize all key bindings and some UI elements by editing `keys_user.conf` and `prefs_user.conf`. The default configurations are in `keys.conf` and `prefs.conf`.



## Build Instructions

### Linux
1. Install Qt 5 and make sure `qmake` is in `PATH`.
2. Install `libharfbuzz`:
```
sudo apt install libharfbuzz-dev
```
3. Clone the repository and build:
```
git clone --recursive https://github.com/ahrm/sioyek
cd sioyek
./build_linux.sh
```
### Windows
1. Install Visual Studio (tested on 2019, other relatively recent versions should work too)
2. Install Qt 5 and make sure qmake is in `PATH`.
3. Clone the repository and build using 64 bit Visual Studio Developer Command Prompt:
```
git clone --recursive https://github.com/ahrm/sioyek
cd sioyek
build_windows.bat
```

### Mac
1. Install Xcode and Qt 5.
2. Clone the repository and build:
```
git clone --recursive https://github.com/ahrm/sioyek
cd sioyek
chmod +x build_mac.sh
./build_mac.sh
```
