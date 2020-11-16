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


### AWS

AWS CloudFormation Template (with ECS Spot Pricing): https://github.com/vatertime/minecraft-spot-pricing (based on https://github.com/m-chandler/factorio-spot-pricing)

Own domain using Route53: https://docs.aws.amazon.com/de_de/Route53/latest/DeveloperGuide/CreatingHostedZone.html


### 200 clients

Problem: standard Minecraft client costs about 24€ - may be too much, if you want to 200 students?!

Alternatives? https://liquidbounce.net/  (https://github.com/CCBlueX/LiquidBounce)