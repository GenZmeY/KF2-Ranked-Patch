# KF2-Ranked-Patch

# Description
Makes kf2 server ranked  

# Dependencies
- any GNU/Linux OS
- dd, readelf, hexdump
- kf2 server

# Usage
- install dependencies (dd, readelf, hexdump) using your OS's package manager
- copy [kf2-ranked-patch](kf2-ranked-patch) to your server
- make it executable: `chmod +x kf2-ranked-patch`
- run it like this: `./kf2-ranked-patch <path_to_KFGameSteamServer.bin.x86_64>`

# Enable auto-patching
If you are using [KF2-SRV](https://github.com/GenZmeY/KF2-SRV) then copy [kf2-ranked-patch](kf2-ranked-patch) to `/usr/share/kf2-srv/patch/` so that the server will automatically apply the patch after each update  

# Notes
- need to patch `KFGameSteamServer.bin.x86_64` after every KF2 update
