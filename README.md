# minecraft
Notes on how to build a Minecraft server for schools


### Links

Vanilla, Bukkit, Spigot, Paper, Forge??? https://www.spigotmc.org/wiki/what-is-spigot-craftbukkit-bukkit-vanilla-forg/


### Docker?

Most used (also in production from https://mcserverhosting.net/):

https://github.com/itzg/docker-minecraft-server (https://hub.docker.com/r/itzg/minecraft-server)

See Plugin / Spigot use: https://github.com/itzg/docker-minecraft-server/tree/master/examples/paper-build-plugins

(download Worldedit from https://dev.bukkit.org/projects/worldedit/files)

Example - see [docker-compose.yml](docker-compose.yml):

```yaml
version: '3.7'

services:
  minecraft:
    build: .
    environment:
      EULA: "TRUE"
      TYPE: "SPIGOT"
    ports:
    - 25565:25565
    stdin_open: true
    tty: true
```

##### Server console access

For the server console the RCON CLI is used. Therefore we need to log into the container with: 

```shell script
docker exec -i minecraft_minecraft_1 rcon-cli
```

Giving operator (op) rights to users: https://minecraft-de.gamepedia.com/Befehl/op

If you want to give `axl_2000` the operator rights, do:

```
op axl_2000
```


### AWS

AWS CloudFormation Template (with ECS Spot Pricing): https://github.com/vatertime/minecraft-spot-pricing (based on https://github.com/m-chandler/factorio-spot-pricing)

Own domain using Route53: https://docs.aws.amazon.com/de_de/Route53/latest/DeveloperGuide/CreatingHostedZone.html


### 200 clients

Problem: standard Minecraft client costs about 24€ - may be too much, if you want to 200 students?!

Alternatives? https://liquidbounce.net/  (https://github.com/CCBlueX/LiquidBounce)

Disable Pillagers: https://marc.tv/stabiler-minecraft-server-raspberry-pi4/#welche-hardware-benoetigt-man 


##### Resources per User

https://mc-gameserver-mieten.de/gameserver-knowhow/wie-viel-ram-minecraft/

Historic: 100MB/User - 10Users/1GB RAM

--> But today it's more like: 15-20Users/1GB RAM

> With 64GB of RAM the server should be able to run around 1000 Users



# Links

Complete Minecraft isometric landscape rendering: https://marc.tv/overviewer-minecraft-docker-synology/