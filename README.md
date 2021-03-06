# RSIA-Recompiled

RSIA-Recompiled is a recompiler/patcher for RuneScape: Idle Adventures' `Assembly-CSharp.dll` with included patches to make the game run without the (now defunct) servers.

## [Legal FAQs and Disclaimers](LEGAL.md)

## Requirements

Building this project requires you have the following tools installed and added to your PATH:

- [💾 `ilspycmd`](https://github.com/icsharpcode/ILSpy/tree/master/ICSharpCode.Decompiler.Console) (tested with version 7.1.0.0)
- [💾 `git`](https://git-scm.com/)
- [💾 `Visual Studio / msbuild`](https://visualstudio.microsoft.com/) (tested with VS2019)
- `wget` (optional, [💾 `Windows`](https://community.chocolatey.org/packages/Wget) / [💾 `Linux`](https://www.gnu.org/software/wget/))

## Preparations ([Why?](LEGAL.md))

It is necessary that you have a copy of the two key items:

- A copy of the games files downloaded from [💾 Steam](steam://install/452780). ([SteamDB](https://steamdb.info/app/452780/))
- A copy of the games web assets downloaded from the CDN. (tested with version [💾 `0.1.9`](ASSETS-0.1.9.txt))

The files should be placed in the project directory like so:

    README.md (you are here)
    data/
    ├─ idle-adventures.exe
    ├─ idle-adventures_data/
    │  ├─ Managed/
    │  │  ├─ Assembly-CSharp.dll
    │  │  ├─ [...]
    │  ├─ StreamingAssets/
    │  │  ├─ win32/
    │  │  │  ├─ art/
    │  │  │  ├─ data/
    │  │  │  ├─ scenes/
    │  │  │  ├─ win32

If you have `wget` installed, you can download the assets automatically using the following command:

    gradlew downloadAssets

Alternatively, you can download the assets manually and place them in the `data` directory as instructed above.

## Building

First, decompile and apply the patches to the games code:

    gradlew applyPatches

Next, build the game:

    gradlew build

The final game data will be copied to the `build` directory. Simply copy this over your Steam installation or use your favorite █████ ████████.

## Contributing

Should you want to contribute patches, you can follow these steps:

1. Apply fresh patches using `gradlew applyPatches`.
2. Make your changes in `src`.
3. Build and test your changes using `gradlew build`.
4. Once your changes are finalized, make commits in the `src` subrepository to be made into patches.
5. Generate patches for your commits using `gradlew makePatches`.
6. Commit your patches to the parent repository in your own fork.
7. Pull Request your changes!
