# SystemDumpViewer [![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
Viewer for SystemDump.xml files of [B&amp;R](https://www.br-automation.com) PLCs with a few nice features...

![SystemDumpViewer](https://github.com/bee-eater/SystemDumpViewer/blob/master/99_projinfo/Screenshot_211022169.png)

# Contributors welcome

This project adheres to the Contributor Covenant [code of conduct](CONTRIBUTING.md).
By participating, you are expected to uphold this code. Please report unacceptable behavior to [the owner](mailto:bee-eater@users.noreply.github.com).

# How to compile
1. Get Qt 5.12.6 from here: [Download](http://download.qt.io/official_releases/qt/5.12/5.12.6/qt-opensource-windows-x86-5.12.6.exe)
1. Install Qt with mingw730_32
1. Copy the qwt.dll from libs folder to you build/debug or build/release folder	

If you want to use another Qt version, you'll have to compile Qwt first. [Tutorial](https://www.youtube.com/watch?v=ZqFKwF6q7jQ)

# More info about the project
## Recommended folder structure
To make the .bat scripts and everything run smoothly, the following structure
is recommended:
![FolderStructure](https://github.com/bee-eater/SystemDumpViewer/blob/master/99_projinfo/folder_structure.png)

## Lanugages
Qt supports translation in the code.
If you want text translated, use tr("mytext"), if not use QString("mytext")

Steps with bt_EditLanguages.bat to add translations
1. Option 5 in batch: Update and remove obsolete
2. Edit the desired languages in Linguist (currently german, english, french, russian and polish)
3. Option 4 in batch: Release
4. Option 8 in batch: Copy to debug

Now you should have up to date .qm files and the translation should work in your debug environment

## Program structure 
**A very brief overview :-)**

### systemdump.h
Here is the main systemdump structure defined for the member this->SysDump in the main class
New values have to be added here.

### main_mapXml.cpp
In file main_mapXml.cpp there are the possible entries in the Systemdump.xml defined
as mappings with lowercase texts and enums, so switch cases can be used.
The std::maps and the enums themselves have to be defined in the mainwindow.h (Starting around line 212) aswell.

### main_readXml.cpp
In file main_readXml the values are read from the xml structure with the rapidxml library.
The function get_SystemDumpSections(...) reads all the sections. The error number thrown if
an unknown attribute is found defines the place in the code where to look for easier locating.
See file errorNumbers.txt for (possibly incomplete) list of error Numbers.
The values are written to this->SysDump...

### main_displayValues.cpp
Here the Values are displayed on the visu, using the values from this->SysDump
