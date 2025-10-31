# Build instructions

## Build on Windows

## Build dynamic version to debug project:

-   Download and install [gstreamer](https://gstreamer.freedesktop.org/data/pkg/windows/1.16.3/) runtime and devel -msvc-x86_64-1.16.3.msi
-   Download and install [Qt5.15.2 msvc2019_64 incl. QT WebEngine and QtCreator](https://www.qt.io/download-qt-installer-oss?hsCtaTracking=99d9dd4f-5681-48d2-b096-470725510d34%7C074ddad0-fdef-4e53-8aa8-5e8a876d6ab4) (When in customize look out for a drop down and activate Archive for versions < Qt6)
-   Add the GStreamer bin path (e.g. C:\gstreamer\1.0\x86_64\bin) to PATH variable into the QtCreator project build enviroment settings
-   Build and run MapMap project within QtCreator (Ctrl-R)

## Build static version for release:

-   Download and install gstreamer-x86 [runtime](https://gstreamer.freedesktop.org/data/pkg/windows/1.16.2/gstreamer-1.0-mingw-x86-1.16.2.msi) and [devel](https://gstreamer.freedesktop.org/data/pkg/windows/1.16.2/gstreamer-1.0-devel-mingw-x86-1.16.2.msi)
-   Build a [Qt static environment](https://wiki.qt.io/Building_a_static_Qt_for_Windows_using_MinGW) (This [video](https://www.youtube.com/watch?v=nEQGrBiz2T0) may explain it better)
-   Build MapMap using QtCreator (qmake, build release)
-   Copy all dll files of the gstreamer's bin folder (e.g. C:\gstreamer\1.0\x86\bin) into the target folder together with MapMap.exe
-   Copy all dll files of the gstreamer's plugin folder (e.g. C:\gstreamer\1.0\x86\lib\gstreamer-1.0) into an new folder named 'plugin' in parallel to MapMap.exe.
-   Run MapMap.exe

#### For packaging

-   Open Qt terminal via a Start Menu and run the following command:
    `windeployqt --release --no-system-d3d-compiler <path-to-app-binary>`
-   Replace all the `*.qm` files that exists in `released-binary`/translations folder by the ones from `source-code`/translations folder
-   Download and install [Inno Setup](https://jrsoftware.org/isdl.php) to create an installation wizard setup

## Editing translations

You might need to update the files:

```
cd src/mapmap
lupdate mapmap.pro
```

Then, do this:

```
lrelease mapmap.pro
```
