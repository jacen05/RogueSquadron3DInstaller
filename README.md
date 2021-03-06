RogueSquadron3DInstaller
========================

**Star Wars : Rogue Squadron 3D** unofficial installer

Game published in 1998 by [LucasArts](http://www.starwars.com/games-apps), developed by [Factor 5](http://www.factor5.de/)

*for Windows (All 32 and 64 bit versions from XP) and Wine*

*tested on Windows 7 Ultimate x64, Ubuntu 14.04 Trusty x64, Debian Wheezy 7.6 x64 on Wine 1.7.26, 1.7.27 and 1.7.28, with Intel graphics HD4000, Nvidia Geforce 620m, and Geforce GTX 660Ti*

**This software is freeware. It is neither supported nor endorsed by LucasArts. Use at your own risk! Original CD required.**

**The source code of this installer, excluding all files licensed or containing elements licensed by other parties, is subject to [Attribution-NonCommercial-NoDerivs 3.0 Unported (CC BY-NC-ND 3.0) license](https://creativecommons.org/licenses/by-nc-nd/3.0/).**

**You may only redistribute the original executables when done free of charge and all files are left intact (no additions, removals or alterations).**

**The only goal of this installer is to provide a means to install and play this game on newer systems, in the context of video game history preservation, and not in any way to bypass the original copy protection (which it doesn't), or favor piracy**

Made with [nsis](http://nsis.sourceforge.net) 3.0b1

## Changelog

See [changelog.txt](changelog.txt)

## Goal

The goal is to make a 'definitive' version of the game, to allow playing without hassles on recent computers.

Since the original installer is a 16bit executable, it won't run on 64bit Windows, and Wine on recent linux kernels (>= 3.14) by default.

It has also known issues with recent graphic cards.

Since it needs a few compatibility fixes and additions, i feel it is simpler to bundle all the requirements into one package.

## Features

- Independent installer : needs the original cd, but can be run from anywhere, no need to burn a modified cdrom
- Contains update 1.2
- Detects game version to avoid unecessary updates
- Installs DirectX 9.0c
- Installs [nGlide](http://www.zeus-software.com/downloads/nglide) glide wrapper, allowing to play the game in 3dfx mode, up to 7860x4320 (although i have tested only up to 1920x1080). Automatically sets the renderer to glide.
- Patches the game to fix the Direct3D mission crash bug. The game is known to crash at the end of missions in D3D mode (albeit of limited use since the game doesn't work with a lot of cards in D3D mode)
- Detects Wine (to disable directx installation and unsupported file copying method, force path)
- Asks to run graphic settings at the end of setup
- '/nocdprompt' command line switch to avoid asking two times for the cdrom when already asked before (i.e in [PlayOnLinux](http://www.playonlinux.com/) or [Lutris](https://lutris.net/))

## Plans / Issues

- Make an 1.3 update. It was only distributed in newer rogue squadron cds, never been packaged separatly. It was made to support more graphics cards and fix a few bugs. But i don't really know the real differences between 1.2 and 1.3
- Test with non-english versions
- Wait for the next nGlide update. The game runs perfect with latest version (1.03), but has a [mission crash bug of its own](http://www.zeus-software.com/forum/viewtopic.php?f=10&t=729), so you need to relaunch the game after each mission. Penultimate (1.02) has no bug, but the game feels laggy in every resolution. For now i'll provide two versions of the installer, one for each nGlide version. Up for you to choose. Thanks to them for their amazing work !
- Optionally integrate [SweetFX](http://forums.guru3d.com/showthread.php?t=381912), to allow for shiny new (or rusty) graphics for those who want it ! It is known to work with nGlide.
- Who knows ? [Reverse engineering Rogue Squadron 3D](http://satd.sk/web/rs/)
- Update the [Wine HQ page](https://appdb.winehq.org/objectManager.php?sClass=application&iId=3258)
- Test on Mac (Wine)
- Make the menu video work (by properly configuring LucasArts SANM fourcc)

## Dependencies

- NSIS 3.0b1 : [Download page](http://nsis.sourceforge.net/Download) / [Direct link](http://prdownloads.sourceforge.net/nsis/nsis-3.0b1-setup.exe?download)

- NSIS Plugins and Headers (also available in the nsis folder in this repository, merge the contents of this folder to nsis installation folder):
  * [AccessControl plug-in](http://nsis.sourceforge.net/AccessControl_plug-in) **[v.1.0.8.1](http://nsis.sourceforge.net/mediawiki/images/4/4a/AccessControl.zip)**:

    Written by [Mathias Hasselmann](http://taschenorakel.de/mathias/)
    
    NSIS-Unicode port by [Olivier Marcoux](http://wizou.fr/)
    
    Major changes by [Afrow UK](http://www.afrowsoft.co.uk/)
    
    Win95/WinNT4 support and bugfixes by [Anders](http://nsis.sourceforge.net/User:Anders)
    
  * [nsArray plug-in](http://nsis.sourceforge.net/Arrays_in_NSIS) **[v.1.1.1.6](http://nsis.sourceforge.net/mediawiki/images/9/97/NsArray.zip)**:

    Written by [Afrow UK](http://www.afrowsoft.co.uk/)
    
  * [NsisFile plug-in](http://nsis.sourceforge.net/NsisFile_plug-in) **[v.1.0](http://wiz0u.free.fr/prog/nsisFile/latest.php)**:

    Written by [Wizou](http://nsis.sourceforge.net/User:Wizou)
    
  * [Advanced Uninstall Log NSIS Header](http://nsis.sourceforge.net/Advanced_Uninstall_Log_NSIS_Header) **[Download](http://nsis.sourceforge.net/mediawiki/images/1/12/Advunlog.zip)**:
    
    Written by [Red Wine](http://nsis.sourceforge.net/User:Red_Wine)

    **This header needs a fix or an error will be triggered during compilation** : 
    
    l.428 change
    ```!undef ID ${__LINE__}```
    to
    ```!undef ID```

  * [NSISdl translated header](http://forums.winamp.com/showthread.php?postid=1279800#18) **[2004-02-18](http://forums.winamp.com/attachment.php?attachmentid=24748&d=1077111624)**:

    Written by deguix

    Supported languages with their translators in alphabetical order:

      English default language by Yaroslav Faybishenko and Justin Frankel

      Chinese, Simplified translation by Kii Ali <kiiali@cpatch.org>
    
      Chinese, Traditional translation by "matini" and Kii Ali <kiiali@cpatch.org>
    
      Croatian translation by Igor Ostriz

      German tranlation by Jan T. Sott

      Lithuanian translation by Vytautas Krivickas

      Portuguese, Brazilian translation by "deguix"
      
## Compilation

- Clone this repository or download and extract archive
- Right-click on RS3DInstaller_nglide_102.nsi or RS3DInstaller_nglide_103.nsi, then click 'Compile NSIS Script'
- Run the resulting executable, et voila !

## Installation

- Download one of the two versions of the installer :
  * [RS3DInstaller-0.96_nglide_102.exe](http://github.com/medfreeman/RogueSquadron3DInstaller/raw/master/RS3DInstaller-0.96_nglide_102.exe) feels a bit laggy, but has no crash at the end of missions
  * [RS3DInstaller-0.96_nglide_103.exe](http://github.com/medfreeman/RogueSquadron3DInstaller/raw/master/RS3DInstaller-0.96_nglide_103.exe) is smoother, but you need to relaunch the game after every mission
- Insert original cdrom
- Run the new installer
- Play the game !

## Links and thanks

- [development PlayOnLinux Rogue scripts](https://github.com/medfreeman/playonlinux/tree/master/RogueSquadron3D/WIP)
  * [Testing game page](http://www.playonlinux.com/en/app-2277-Star_Wars__Rogue_Squadron_3D.html)
- [nGlide](http://www.zeus-software.com/downloads/nglide)
  * [Bug fix request thread](http://www.zeus-software.com/forum/viewtopic.php?f=10&t=729)
- [nsis](http://nsis.sourceforge.net)
- D3D Mission crash fix references
  * http://forum.pj64-emu.com/archive/index.php/t-4168.html
  * http://www.lucasforums.com/archive/index.php/t-171387.html
- [Wine](https://www.winehq.org/)
  * [Wine game page](https://appdb.winehq.org/objectManager.php?sClass=application&iId=3258)
- [PlayOnLinux](http://www.playonlinux.com/)
- [Lutris](https://lutris.net/)
- [SweetFX](http://forums.guru3d.com/showthread.php?t=381912)
- [Reverse engineering Rogue Squadron 3D](http://satd.sk/web/rs/)
  * [Tools](https://github.com/dpethes/rerogue)
- [Markus Egger](http://www.markusegger.at/Software/Games/Rogue/Instructions.html)

## Disclaimer

**Star Wars, Rogue Squadron (3D), LucasArts, Microsoft, Windows, Windows 7, Vista, XP, DirectX and all the entities mentioned in this readme are ©, ® and/or ™ of their respective holders.**

**The file gfx/icon/rogue.ico is the original rogue squadron 3D icon, © LucasArts**

**The files gfx/header/rogue.bmp and gfx/welcome/rogue.bmp were made by myself, and contain Rogue Squadron 3D logo © LucasArts**

**The file assets/update/rogueupd12.exe is the original rogue squadron 3D update v.1.2 © LucasArts**

**The file license/LICENSE.TXT is the original game license, and is property of LucasArts**

**This installer source code is available solely to prove that there's no intent to include malicious software inside this installer**
