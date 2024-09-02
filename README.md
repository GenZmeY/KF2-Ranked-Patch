# KF2-Ranked-Patch
Makes kf2 server ranked  

## Legal
Use of this patch violates the [KF2 EULA](https://store.steampowered.com/eula/232090_eula_0) provisions that prohibit disassembling or modifying game files.  
If this is a problem for you, use [SafeMutLoader](https://github.com/GenZmeY/KF2-SafeMutLoader/), which is completely legal.  

## Warning
Applying this patch may require you to do things like execute a script, edit a binary file, restore execution rights after replacing a file. For this reason, **I can only recommend using this patch if you have full access to the system**, for example if you are using your own server or renting a VPS (virtual private server).  

If you are using a game hosting service, then performing the above actions may be difficult or even impossible, so I would recommend using [SafeMutLoader](https://github.com/GenZmeY/KF2-SafeMutLoader/) in this case.  

## Applying the patch (easy way)
Take the patched file from the [releases](https://github.com/GenZmeY/KF2-Ranked-Patch/releases):  
For windows: `KFGame.exe`  
For linux: `KFGameSteamServer.bin.x86_64`  

And place it on your server at this path (replace the existing file):  
`<kf2-server>/Binaries/Win64`

In the case of a linux system, make sure that after replacing the file has an execution flag and if it does not - add it using `chmod` like this:  
`chmod +x <path_to_KFGameSteamServer.bin.x86_64>`  

## Applying the patch (manually)
### Linux
#### Dependencies
- any GNU/Linux OS;
- dd, readelf, hexdump;
- Killing Floor 2 server.

#### Usage
1. install dependencies (dd, readelf, hexdump) using your OS's package manager;
2. copy [kf2-ranked-patch](kf2-ranked-patch) to your server;
3. make it executable: `chmod +x kf2-ranked-patch`;
4. run it like this: `./kf2-ranked-patch <path_to_KFGameSteamServer.bin.x86_64>`.

### Windows
#### Dependencies
- OS Windows
- Killing Floor 2 server;
- Hex editor (for example this one: [HxD](https://mh-nexus.de/en/hxd/)).

#### Usage
1. Open `<kf2_server_dir>\Binaries\Win64\KFServer.exe` in a Hex editor;
2. [Patch1] Find and replace the following sequence (in hex mode):  
   Find:  
   ```hex
   48 83 ec 28 81 89 e0 04 00 00 00 00 00 08 48 8b 0d 23 33 9f 00 48 8d 15 a4 b0 73 00 e8 0f 92 4b ff 48 8b 0d c0 9f cc 00 e8 d3 2f 57 ff 48 85 c0 74 0c 48 8b c8 48 83 c4 28 e9 42 09 e3 ff 48 83 c4 28 c3
   ```
   Replace:  
   ```hex
   90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 c3
   ```
3. [Patch2] Find and replace the following sequence (in hex mode):  
   Find:  
   ```hex
   48 8b c4 55 41 56 41 57 48 8d 68 a1 48 81 ec 90 00 00 00 48 c7 45 d7 fe ff ff ff 48 89 58 08 48 89 70 10 48 89 78 18 4c 89 60 20 4d 8b f9 4d 8b f0 48 8b da 48 8d 15 f9 0a 71 00 48 8d 4d ff e8 4c cf 3f ff 90 48 8d 15 0c 09 72 00 48 8d 4d ef e8 3b cf 3f ff 90 48 8b cb e8 52 89 4b ff 48 8b c8 48 8d 55 1f e8 f6 d4 40 ff 90 48 8d 55 0f 48 8b c8 e8 e9 26 42 ff 90 45 33 e4 4c 89 65 27 48 8b 4d 1f 48 85 c9 74 09 e8 43 c7 43 ff 4c 89 65 1f 8b 45 07 85 c0 74 28 7f 20 4c 8d 0d ef 0b 37 00 41 b8 45 02 00 00 48 8d 15 42 15 37 00 48 8d 0d 83 15 37 00 e8 86 8b 4a ff 48 8b 5d ff eb 07 48 8d 1d c9 0b 37 00 8b 45 17 85 c0 74 28 7f 20 4c 8d 0d b9 0b 37 00 41 b8 45 02 00 00 48 8d 15 0c 15 37 00 48 8d 0d 4d 15 37 00 e8 50 8b 4a ff 48 8b 4d 0f eb 07 48 8d 0d 93 0b 37 00 48 8b d3 ff 15 8a e4 35 00 85 c0 74 7d 8b 45 f7 85 c0 74 28 7f 20 4c 8d 0d 76 0b 37 00 41 b8 45 02 00 00 48 8d 15 c9 14 37 00 48 8d 0d 0a 15 37 00 e8 0d 8b 4a ff 48 8b 5d ef eb 07 48 8d 1d 50 0b 37 00 8b 45 17 85 c0 74 28 7f 20 4c 8d 0d 40 0b 37 00 41 b8 45 02 00 00 48 8d 15 93 14 37 00 48 8d 0d d4 14 37 00 e8 d7 8a 4a ff 48 8b 4d 0f eb 07 48 8d 0d 1a 0b 37 00 48 8b d3 ff 15 11 e4 35 00 85 c0 0f 85 56 03 00 00 41 8b f4 41 8b 46 08 49 8b fc 85 c0 0f 8e 98 01 00 00 0f 1f 80 00 00 00 00 48 85 ff 78 0d 3b f0 7c 29 48 85 ff 75 04 85 c0 74 20 4c 8d 0d d7 0a 37 00 41 b8 52 02 00 00 48 8d 15 2a 14 37 00 48 8d 0d 6b 14 37 00 e8 6e 8a 4a ff 49 8b 0e 48 8b 0c f9 e8 d2 87 4b ff 48 8b c8 48 8d 55 2f e8 76 d3 40 ff 90 48 8d 55 df 48 8b c8 e8 69 25 42 ff 90 4c 89 65 37 48 8b 4d 2f 48 85 c9 74 09 e8 c6 c5 43 ff 4c 89 65 2f 8b 45 07 85 c0 74 28 7f 20 4c 8d 0d 72 0a 37 00 41 b8 45 02 00 00 48 8d 15 c5 13 37 00 48 8d 0d 06 14 37 00 e8 09 8a 4a ff 48 8b 5d ff eb 07 48 8d 1d 4c 0a 37 00 8b 45 e7 85 c0 74 28 7f 20 4c 8d 0d 3c 0a 37 00 41 b8 45 02 00 00 48 8d 15 8f 13 37 00 48 8d 0d d0 13 37 00 e8 d3 89 4a ff 48 8b 4d df eb 07 48 8d 0d 16 0a 37 00 48 8b d3 ff 15 0d e3 35 00 85 c0 74 79 8b 45 f7 85 c0 74 28 7f 20 4c 8d 0d f9 09 37 00 41 b8 45 02 00 00 48 8d 15 4c 13 37 00 48 8d 0d 8d 13 37 00 e8 90 89 4a ff 48 8b 5d ef eb 07 48 8d 1d d3 09 37 00 8b 45 e7 85 c0 74 28 7f 20 4c 8d 0d c3 09 37 00 41 b8 45 02 00 00 48 8d 15 16 13 37 00 48 8d 0d 57 13 37 00 e8 5a 89 4a ff 48 8b 4d df eb 07 48 8d 0d 9d 09 37 00 48 8b d3 ff 15 94 e2 35 00 85 c0 75 28 4c 89 65 e7 48 8b 4d df 48 85 c9 74 09 e8 be c4 43 ff 4c 89 65 df ff c6 48 ff c7 41 8b 46 08 3b f0 7d 0e e9 78 fe ff ff 4c 89 65 e7 e9 9e 01 00 00 41 8b f4 41 8b 47 08 49 8b fc 85 c0 0f 8e 9f 01 00 00 48 85 ff 78 0d 3b f0 7c 29 48 85 ff 75 04 85 c0 74 20 4c 8d 0d 34 09 37 00 41 b8 52 02 00 00 48 8d 15 87 12 37 00 48 8d 0d c8 12 37 00 e8 cb 88 4a ff 49 8b 0f 48 8b 0c f9 e8 2f 86 4b ff 48 8b c8 48 8d 55 2f e8 d3 d1 40 ff 90 48 8d 55 df 48 8b c8 e8 c6 23 42 ff 90 4c 89 65 37 48 8b 4d 2f 48 85 c9 74 09 e8 23 c4 43 ff 4c 89 65 2f 8b 45 07 85 c0 74 28 7f 20 4c 8d 0d cf 08 37 00 41 b8 45 02 00 00 48 8d 15 22 12 37 00 48 8d 0d 63 12 37 00 e8 66 88 4a ff 48 8b 5d ff eb 07 48 8d 1d a9 08 37 00 8b 45 e7 85 c0 74 28 7f 20 4c 8d 0d 99 08 37 00 41 b8 45 02 00 00 48 8d 15 ec 11 37 00 48 8d 0d 2d 12 37 00 e8 30 88 4a ff 48 8b 4d df eb 07 48 8d 0d 73 08 37 00 48 8b d3 ff 15 6a e1 35 00 85 c0 74 79 8b 45 f7 85 c0 74 28 7f 20 4c 8d 0d 56 08 37 00 41 b8 45 02 00 00 48 8d 15 a9 11 37 00 48 8d 0d ea 11 37 00 e8 ed 87 4a ff 48 8b 5d ef eb 07 48 8d 1d 30 08 37 00 8b 45 e7 85 c0 74 28 7f 20 4c 8d 0d 20 08 37 00 41 b8 45 02 00 00 48 8d 15 73 11 37 00 48 8d 0d b4 11 37 00 e8 b7 87 4a ff 48 8b 4d df eb 07 48 8d 0d fa 07 37 00 48 8b d3 ff 15 f1 e0 35 00 85 c0 75 28 4c 89 65 e7 48 8b 4d df 48 85 c9 74 09 e8 1b c3 43 ff 4c 89 65 df ff c6 48 ff c7 41 8b 47 08 3b f0 7d 1c e9 78 fe ff ff 4c 89 65 e7 48 8b 4d df 48 85 c9 74 05 e8 f3 c2 43 ff 41 8b dc eb 05 bb 01 00 00 00 4c 89 65 17 48 8b 4d 0f 48 85 c9 74 09 e8 d7 c2 43 ff 4c 89 65 0f 4c 89 65 f7 48 8b 4d ef 48 85 c9 74 09 e8 c1 c2 43 ff 4c 89 65 ef 4c 89 65 07 48 8b 4d ff 48 85 c9 74 05 e8 ab c2 43 ff 8b c3 4c 8d 9c 24 90 00 00 00 49 8b 5b 20 49 8b 73 28 49 8b 7b 30 4d 8b 63 38 49 8b e3 41 5f 41 5e 5d c3
   ```
   Replace:  
   ```hex
   90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 48 31 C0 B8 01 00 00 00 C3
   ```

## How it works
This patch modifies the `KFGameInfo::SetGameUnranked()` function so that it does nothing - this prevents the server from going into an unranked state.  
The patch also modifies the `KFGameInfo::ValidateForXP()` function so that it always returns true. `ValidateForXP()` prevents XP from being gained for killing custom zeds and using custom weapons - modifying this function makes it possible to gain XP in these cases.  

The patch for Linux is a bash script that searches for and patches these functions in the executable file, works with any version of the KF2 server.  
In the case of Windows, there is no automation and the work to find the necessary functions was done manually, so replacing the specified hex sequences is relevant only for a specific version of the KF2 server (currently 1150 and 1150v2).  

## Notes
- Game updates and integrity checks replace the executable file (`KFGameSteamServer.bin.x86_64` / `KFServer.exe`) with original one, so after these events the patch must be applied again.

## License
[![license](https://img.shields.io/github/license/GenZmeY/KF2-Ranked-Patch)](LICENSE)
