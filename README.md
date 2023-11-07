# SFML configuration set for Visual Studio projects
***
`Configuration Properties` → `C/C++` → `General` → `[ Additional Include Directories ]`
```
C:\a-directory-with-the-SFML-headers-directory\;
```
---
`Configuration Properties` → `C/C++` → `Proprocessor` → `[ Proprocessor Definition ]`
```
SFML_STATIC;
```
| Dynamic linking | Static linking |
|:-:|:-:|
| |`SFML_STATIC`|
---
`Configuration Properties` → `C/C++` → `Code Generatio` → `[ Runtime Library ]`
```
Multi-threaded (/MT)
```
| Dynamic linking (Debug) | Dynamic linking (Release) | Static linking (Debug) | Static linking (Release) |
|:-:|:-:|:-:|:-:|
|`Multi-threaded Debug DLL (/MDd)`|`Multi-threaded DLL (/MD)`|`Multi-threaded Debug (/MTd)`|`Multi-threaded (/MT)`|
---
`Configuration Properties` → `Linker` → `General` → `[ Additional Library Directories ]`
```
C:\a-directory-with-lib-type-files\;
```
---
`Configuration Properties` → `Linker` → `Input` → `[ Additional Dependencies ]`
```
sfml-main.lib
sfml-graphics-s.lib
freetype.lib
sfml-window-s.lib
gdi32.lib
OpenGL32.lib
sfml-network-s.lib
ws2_32.lib
sfml-audio-s.lib
vorbis.lib
vorbisfile.lib
vorbisenc.lib
flac.lib
ogg.lib
OpenAL32.lib
sfml-system-s.lib
winmm.lib
```
| Dynamic linking (Debug) | Dynamic linking (Release) | Static linking (Debug) | Static linking (Release) |
|:-|:-|:-|:-|
|`sfml-main-d.lib`<br>`sfml-graphics-d.lib`<br>`sfml-window-d.lib`<br>`sfml-network-d.lib`<br>`sfml-audio-d.lib`<br>`sfml-system-d.lib`|`sfml-main.lib`<br>`sfml-graphics.lib`<br>`sfml-window.lib`<br>`sfml-network.lib`<br>`sfml-audio.lib`<br>`sfml-system.lib`|`sfml-main-d.lib`<br>`sfml-graphics-s-d.lib`<br>`freetype.lib`<br>`sfml-window-s-d.lib`<br>`gdi32.lib`<br>`OpenGL32.lib`<br>`sfml-network-s-d.lib`<br>`ws2_32.lib`<br>`sfml-audio-s-d.lib`<br>`vorbis.lib`<br>`vorbisfile.lib`<br>`vorbisenc.lib`<br>`flac.lib`<br>`ogg.lib`<br>`OpenAL32.lib`<br>`sfml-system-s-d.lib`<br>`winmm.lib`|`sfml-main.lib`<br>`sfml-graphics-s.lib`<br>`freetype.lib`<br>`sfml-window-s.lib`<br>`gdi32.lib`<br>`OpenGL32.lib`<br>`sfml-network-s.lib`<br>`ws2_32.lib`<br>`sfml-audio-s.lib`<br>`vorbis.lib`<br>`vorbisfile.lib`<br>`vorbisenc.lib`<br>`flac.lib`<br>`ogg.lib`<br>`OpenAL32.lib`<br>`sfml-system-s.lib`<br>`winmm.lib`|

## SFML libraries dependencies scheme for static linking

```mermaid
graph BT;
    Audio([sfml-audio-s.lib]);
    Network([sfml-network-s.lib]);
    System([sfml-system-s.lib]);
    Window([sfml-window-s.lib]);
    Graphics([sfml-graphics-s.lib]);
    OpenGL[OpenGL32.lib];
    WS2[ws2_32.lib];
    OpenAL[OpenAL32.lib];
    Vorbis[vorbis.lib\nvorbisfile.lib\nvorbisenc.lib\nflac.lib\nogg.lib];
    FreeType[freetype.lib];
    Winmm[winmm.lib];
    GDI[gdi32.lib];

    System--->Network;
    System--->Window
    Window-->Graphics;
    OpenGL-->Window;
    WS2-->Network;
    FreeType-->Graphics;
    Winmm-->System;
    GDI-->Window;
    Vorbis-->Audio;
    OpenAL-->Audio;
    System--->Audio;

	classDef sfml fill:#333,stroke:#000,stroke-width:2px,color:#f0a;
    classDef lib3rd fill:#333,stroke:#000,stroke-width:2px,color:#f55;
    class Audio,Network,Graphics,Window,System, sfml
    class OpenGL,OpenAL,WS2,Vorbis,FreeType,Winmm,GDI, lib3rd

	linkStyle default stroke-width:2px,fill:none,stroke:grey
	linkStyle 3,4,5,6,7,8,9 stroke:blue,color:blue
	linkStyle 0,1,2,10 stroke:red,color:red
```
---
`Configuration Properties` → `Linker` → `System` → `[ SubSystem ]`
```
Windows (/SUBSYSTEM:WINDOWS)
```
| Debug | Release |
|:-:|:-:|
|`Console (/SUBSYSTEM:CONSOLE)`|`Windows (/SUBSYSTEM:WINDOWS)`|
