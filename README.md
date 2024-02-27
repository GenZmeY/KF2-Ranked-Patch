# KF2-Ranked-Patch
Makes kf2 server ranked  

## Legal
Use of this patch violates the [KF2 EULA](https://store.steampowered.com/eula/232090_eula_0) provisions that prohibit disassembling or modifying game files.  
If this is a problem for you, use [SafeMutLoader](https://github.com/GenZmeY/KF2-SafeMutLoader/), which is completely legal.  

## Dependencies
- any GNU/Linux OS;
- dd, readelf, hexdump;
- Killing Floor 2 server.

## Usage
1. install dependencies (dd, readelf, hexdump) using your OS's package manager;
2. copy [kf2-ranked-patch](kf2-ranked-patch) to your server;
3. make it executable: `chmod +x kf2-ranked-patch`;
4. run it like this: `./kf2-ranked-patch <path_to_KFGameSteamServer.bin.x86_64>`.

## Notes
- Game updates and integrity checks replace the executable file (`KFGameSteamServer.bin.x86_64`) with original one, so after these events the patch must be applied again.
