# SteamCMD in Docker optimized for Unraid
This Docker will download and install SteamCMD. It will also install The Forest and run it.

**SERVERNAME:** 'The Forest Docker' **SERVERPASSWORD:** 'Docker' **ADMINPASSWORD:** 'adminDocker' (you can change this in your SERVERFOLDER/config/config.cfg)

**WARNING:** You have to create a Steam Token to play Online.
Create your token here: https://steamcommunity.com/dev/managegameservers (please note that you must generate the token for the APPID: '242760' and every gameserver needs it's own token!!!). After creating your token you have to go to the file .../theforest/config/config.txt and append your token to the line that starts with: serverSteamAccount (eg: serverSteamAccount YOURTOKEN).  

**Update Notice:** Simply restart the container if a newer version of the game is available.

## Env params
| Name | Value | Example |
| --- | --- | --- |
| STEAMCMD_DIR | Folder for SteamCMD | /serverdata/steamcmd |
| SERVER_DIR | Folder for gamefile | /serverdata/serverfiles |
| GAME_ID | The GAME_ID that the container downloads at startup. If you want to install a static or beta version of the game change the value to: '556450 -beta YOURBRANCH' (without quotes, replace YOURBRANCH with the branch or version you want to install). | 556450 |
| GAME_PARAMS | Values to start the server | empty |
| UID | User Identifier | 99 |
| GID | Group Identifier | 100 |
| GAME_PORT | Port the server will be running on | 27015 |
| VALIDATE | Validates the game data | blank |
| USERNAME | Leave blank for anonymous login | blank |
| PASSWRD | Leave blank for anonymous login | blank |

## Run example
```
docker run --name TheForest -d \
	-p 8766:8766/udp -p 27015:27015/udp -p 27016:27016/udp \
	--env 'UID=99' \
	--env 'GID=100' \
	--volume /path/to/steamcmd:/serverdata/steamcmd \
	--volume /path/to/theforest:/serverdata/serverfiles \
	ich777/steamcmd:theforest
```

This Docker was mainly edited for better use with Unraid, if you don't use Unraid you should definitely try it!

This Docker is forked from mattieserver, thank you for this wonderfull Docker.

### Support Thread: https://forums.unraid.net/topic/79530-support-ich777-gameserver-dockers/