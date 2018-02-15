# Heroku Minecraft Buildpack

Este es un [Buildpack de Heroku](https://devcenter.heroku.com/articles/buildpacks)
para correr un servidor de Minecraft en un [dyno](https://devcenter.heroku.com/articles/dynos).

Gracias al desarrollador Chengsong por la idea del Deploy a Dropbox [Perfil de Chengsong](https://github.com/Chengsong).

## Variables ENV

### DropBox

El sistema de Archivos de Heroku es [efimero](https://devcenter.heroku.com/articles/dynos#ephemeral-filesystem),
lo cual significa que los archivos escritos en el sistema de archivos seran destruidos cuando el dyno se reinicie.

Debes definir tu Token de Autenticacion de Dropbox para sincronizar el Mundo de Minecraft a tu cuenta de Dropbox con:

```
$ heroku config:set DROPBOX_API_TOKEN="MY_DROPBOX_TOKEN"
```

### ngrok

Debes definir tu Token de Autenticacion de Ngrok para abrir tu vpn a tu servidor de Minecraft:

```
$ heroku config:set NGROK_API_TOKEN="MY_NGROK_TOKEN"
```

Puedes personalizarlo con la variable de configuracion `NGROK_OPTS`. For example:

```
$ heroku config:set NGROK_OPTS="-subdomain=my-subdomain"
```

Puedes configurar el server de Minecraft creando un archivo de configuracion `server.properties`
en tu proyecto y añadiendolo a Git. Puedes configurar cosas tales como el modo Creativo o Hardcore, la cantidad de usuarios que pueden ingresar, e incluso un Pack de Texturas. Las opciones varias estan descritas en la [Minecraft Wiki](http://minecraft.gamepedia.com/Server.properties).

Puedes agregar archivos como `banned-players.json`, `banned-ips.json`, `ops.json`,
`whitelist.json` a tu repositorio de Git y el servidor de Minecraft lo tomará.
