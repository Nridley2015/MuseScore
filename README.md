![MuseScore](mscore/data/musescore_logo_full.png)
 Music notation and composition software

## Edited By

* Nicholas Ridley
* Daniel Griessler
* Nabil Osorio
* Guilherme Bueno Dorea

[![Travis CI](https://secure.travis-ci.org/musescore/MuseScore.svg)](https://travis-ci.org/musescore/MuseScore)
[![Appveyor](https://ci.appveyor.com/api/projects/status/bp3ww6v985i64ece/branch/master?svg=true)](https://ci.appveyor.com/project/MuseScore/musescore/branch/master)

[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)

MuseScore is an open source and free music notation software.
For support, contribution, bug reports, visit [MuseScore.org](https://musescore.org). Fork and make pull requests!

## Features

* WYSIWYG design, notes are entered on a "virtual notepaper"
* TrueType font(s) for printing & display allows for high quality scaling to all sizes
* easy & fast note entry
* many editing functions
* MusicXML import/export
* Midi (SMF) import/export
* MuseData import
* Midi input for note entry
* integrated sequencer and software synthesizer to play the score
* print or create pdf files

## More info
* [MuseScore Homepage](https://musescore.org)
* [MuseScore Git workflow instructions](https://musescore.org/en/developers-handbook/git-workflow).
* [How to compile MuseScore?](https://musescore.org/en/developers-handbook/compilation)

## License
MuseScore is licensed under GPL version 2.0. See LICENSE.GPL in the same directory.

## Packages
* **aeolus** Clone of [Aeolus](http://kokkinizita.linuxaudio.org/linuxaudio/aeolus/)
Disabled by default in the stable releases. See http://dev-list.musescore.org/Aeolus-Organ-Synth-td7578364.html
Kept as an example of how to integrate with a complex synthesizer.

* **assets** Graphical assets, use them if you need a MuseScore icon. For logo, color etc... see https://musescore.org/en/about/logos-and-graphics

* **awl** Audio Widget Library, from the MusE project

* **build** Utility files for build

* **bww2mxml** Command line tool to convert BWW files to MusicXML. BWW parser is used by MuseScore to import BWW files.

* **demos** A few MuseScore files to demonstrate what can be done

* **fluid** Clone of [FluidSynth](https://sourceforge.net/projects/fluidsynth/), ported to C++ and customized

* **fonts** Contains fontforge source (sfd) + ttf/otf fonts. MuseScore includes the "Emmentaler" font from the Lilypond project.

* **libmscore** Data model of MuseScore

* **mscore** Main code for the MuseScore UI

* **msynth** Abstract interface to Fluid + Aeolus

* **mtest** Unit testing using QTest

* **omr** Optical music recognition

* **share** Files moved to /usr/share/... on install

* **test** Old tests. Should move to mtest

* **vtest** Visual tests. Compare reference images with current implementation

* **thirdparty** Contains projects which are included for convenience, usually to integrate them into the build system to make them available for all supported platforms.

    * **thirdparty/rtf2html**
    Used for capella import

    * **thirdparty/diff**
    Not used currently. [Diff, Match and Patch Library](https://code.google.com/p/google-diff-match-patch/)

    * **thirdparty/ofqf**
    OSC server interface. Based on [OSC for Qt4](http://www.arnoldarts.de/projects/ofqf/)

    * **thirdparty/singleapp**
    Clone from [Qt Single Application](https://github.com/qtproject/qt-solutions/tree/master/qtsingleapplication)

    * **thirdparty/portmidi**
    Clone from [PortMidi](https://sourceforge.net/projects/portmedia/)

    * **thirdparty/beatroot**
    It's a core part of BeatRoot Vamp Plugin by Simon Dixon and Chris Cannam,
    used in MIDI import for beat detection. (https://code.soundsoftware.ac.uk/projects/beatroot-vamp/repository)


## Building
**Read the developer handbook for a [complete build walkthrough](https://musescore.org/en/developers-handbook/compilation) and a list of dependencies.**

**Ubuntu Only** 
Run the following commands in Terminal (Note you must have at least 2GB RAM and 20GB Disk Space)

    sudo apt-get install git cmake g++

    sudo apt-get install libasound2-dev portaudio19-dev libmp3lame-dev libsndfile1-dev libportmidi-dev

    sudo apt-get install libssl-dev libpulse-dev libfreetype6-dev libfreetype6

    sudo apt-get install libdrm-dev libgl1-mesa-dev libegl1-mesa-dev

    sudo apt-get install libqt4-dev qtbase5-dev qttools5-dev qttools5-dev-tools qtquick1-5-dev \
    qtscript5-dev libqt5xmlpatterns5-dev libqt5svg5-dev libqt5webkit5-dev

After running the last command, install Qt at  http://qt-project.org/

Move the installer to your Home directory and open a terminal window (Ctrl+Alt+T on Ubuntu).


Give the installer execute permissions:

     sudo chmod +x filename.run


Run the installer ("sudo" is not required if you choose to install to your Home directory in Step 5):
     
     sudo ./filename.run

Install Qt 5.8 or later, Musescore also does not yet support version 5.10.

Run the following commands to verify the installation of Qt

     echo 'export PATH=/opt/Qt/5.8/gcc_64/bin:$PATH' >> ~/.bashrc
     source ~/.bashrc
     qmake -version

 
### Getting sources
If using git to download repo of entire code history of master MuseScore, type:

    git clone https://github.com/musescore/MuseScore.git
    cd MuseScore

If using git to download repo of entire code history of this branch, type:

    git clone https://github.com/Nridley2015/MuseScore
    cd MuseScore
    
Else can just download the latest source release tarball from https://github.com/musescore/MuseScore/releases, and then from your download directory type:

    tar xzf MuseScore-x.x.x.tar.gz
    cd MuseScore-x.x.x

### Release Build
To compile MuseScore, type:.

    make revision
    make 
    sudo make install

If something goes wrong, then remove the whole build subdirectory with `make clean` and start new with `make release`.

### Running
To start MuseScore, type:

    mscore

The Start Center window will appear on every invocation, until you disable that setting via the "Preferences" dialog.

### Testing
See [mtest/README.md](/mtest/README.md) or https://musescore.org/en/developers-handbook/testing for instructions on how to run the test suite.

## Deleting Notes
Deleting notes in MuseScore replaces the note with a rest in its place.
The following are ways to delete notes:

1. Select a note by clicking on it. Then press the DEL key to delete it. 
2. In note entry mode, delete the last entered note by hitting Backspace.
3. Right click a note, and select delete.

You can also place a rest in place of a note and it performs the same function. 
