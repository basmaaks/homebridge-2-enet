[![verified-by-homebridge](https://badgen.net/badge/homebridge/verified/purple)](https://github.com/homebridge/homebridge/wiki/Verified-Plugins)


Homebridge to eNet from jung/gira.

Now its possible to switch your switches / shutters and lights within homekit with feedback.

When you switch your light on/off dims or move you shutter from your wall switch its reflected in homekit. Dim your light is on the fly in homekit, the lights goes inmiditly to the desired dim value

Initial written by Julianbx, then Levlevin picked it up, Huglerster made a fork to build it in docker and christophfausak did made the move the eNet api and gives us feedback. I did speed up the script by removing an old fault and rewrote the dimming section so the light reacts inmetidlaty

So thanks to Julianbx, Levlevin, Huglester and Christophfausak for making the script.

This release (1.0.0) was made possible bij them.

This plugin can communicate with Jung/Gira Mobile Gateways and their provisioned devices. Currently, the whole setup needs to be done with the respective Jung/Gira eNet app. Then you need to get the channels for your devices. You might guess them - first used channel is 16. Or you use the sampe-gateway.js from the homebridge-enet package to read the config of your gateway.

Version history :
v1.0.1
Just a little fix, made a typo in index.js

v1.0.0
Clean up the code, rewrite of the readme and modified the config screen.

v0.8.0
Added config screen in homebridge, no needed to modify the config.json bij hand.

v0.7.6
speed up dimming lightbulb, now the lightbulb reacts at instance

v0.7.5
Improved speed bij disable 5 times feedback from gateway

v0.7.3
Integrated eNet-api. Improved debug logging.

v0.7.2
Position updates for switch devices.Allow duration property on lightbulb devices. Fix shutter callback issues. Fix issues with status updates when using multiple gateways.

v0.7.1
Fix timing issues on lightbulb devices.

v0.7.0
Position updates for shutter devices.

v0.6.4
Now the eNet-Commands can update the homekit states and brightness. So, when using a hardware dimmer or switch the lightbulbs current state will be reflected. There is an issue with time delay and overlapping messages by the mobileGate: When changing the dimmer setting the mobile gate gives an update too fast and the bulb gets updated "on the way" to the desired dim setting. Not yet sure how to slow things down! Nontheless, it works with my dimmers and switches. Hopefully I didn't break anything, so please be careful.

Installation
1. Install homebridge using: npm install -g homebridge
2. install this plugin using : npm install -g homebridge-2-enet
3. Update the settings using homebrdige.

Configuration

Just use the homebridge settings. explantion of the settings :
autodiscover is optional. If set to false, no broadcast discovery takes place, all gateways need to have the "host" property set.

gateways is a list of gateways.
For each gateway, you need to give an identification, which will be used to find the gateway on the network. You have three possibilities:
* host - if you provide a hostname or ip address that is the identification for the gateway.
* mac - you can specify the mac-address of the gateway, e.g. by running sampe-discovery.js from the homebridge-2-enet package.
* name - identify gateway by its name. You can set this name with the Jung/Gira eNet app. Factory default is "Mobile Gate"

accessories is a list of defined accessories on the gateway. Every accessory has the following properies:
* channel - The eNet channel assigned to the accessory.
* name - The HomeKit name of the accessory.
* type - Type of accessory. Currently supported:
    * Shutter - Window accessory. You can set the target position.
    * Switch - An on/off switch.
    * Light - Same as Switch, but with a Lightbulb icon on Homekit.
* duration - optional When the accessory is switched on, it will be automatically switched off after duration seconds. Only for Switch and Light accessories.
* dimmable - optional Only for Light accessories.

License
Published under the MIT License.
