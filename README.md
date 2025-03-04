# SteamCMD in Docker optimized for Unraid
This Docker will download and install SteamCMD. It will also install Killing Floor and run it.

To run this container you must provide a valid Steam username and password since the game needs a valid account to download (NOTICE: You must disable Steam Guard otherwise this container will not work, Steam recommens to make a new Steam account for dedicated servers).

**Update Notice:** Simply restart the container if a newer version of the game is available.

## Env params
| Name | Value | Example |
| --- | --- | --- |
| STEAMCMD_DIR | Folder for SteamCMD | /serverdata/steamcmd |
| SERVER_DIR | Folder for gamefile | /serverdata/serverfiles |
| GAME_ID | The GAME_ID that the container downloads at startup. If you want to install a static or beta version of the game change the value to: '215360 -beta YOURBRANCH' (without quotes, replace YOURBRANCH with the branch or version you want to install). | 215360 |
| GAME_PARAMS | Values to start the server | KF-bioticslab.rom?game=KFmod.KFGameType?VACSecured=true?MaxPlayers=6 |
| UID | User Identifier | 99 |
| GID | Group Identifier | 100 |
| VALIDATE | Validates the game data | blank |
| USERNAME | Leave blank for anonymous login | blank |
| PASSWRD | Leave blank for anonymous login | blank |

## Run example
```
docker run --name KillingFloor -d \
	-p 7707-7708:7707-7708/udp -p 7717:7717/udp -p 28852:28852 -p 28852:28852/udp -p 8075:8075 -p 20560:20560/udp \
	--env 'GAME_ID=215360' \
	--env 'GAME_PARAMS=KF-bioticslab.rom?game=KFmod.KFGameType?VACSecured=true?MaxPlayers=6' \
	--env 'USERNAME=YOURSTEAMUSER' \
	--env 'PASSWRD=YOURSTEAMPASSWORD' \
	--env 'UID=99' \
	--env 'GID=100' \
	--volume /path/to/steamcmd:/serverdata/steamcmd \
	--volume /path/to/killingfloor:/serverdata/serverfiles \
	ich777/steamcmd:killingfloor
```

This Docker was mainly edited for better use with Unraid, if you don't use Unraid you should definitely try it!

This Docker is forked from mattieserver, thank you for this wonderfull Docker.

### Support Thread: https://forums.unraid.net/topic/79530-support-ich777-gameserver-dockers/