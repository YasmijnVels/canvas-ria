## WELCOME IMAGE GENERATOR

```js
const Discord = require("discord.js");
const client = new Discord.Client();
const { CanvasRia } = require("canvas-ria")
const riaCanvas = new CanvasRia();

client.once("ready", () => {
  console.log("Ready!");
});


client.on('guildMemberAdd', async member => {
	const channel = member.guild.channels.cache.find(ch => ch.name === 'general');
	if (!channel) return;

   let data = await riaCanvas.welcome(member, { link: "https://i.pinimg.com/originals/6c/d4/eb/6cd4ebf5081d9427be9a0316e664d0fc.jpg" })

    const attachment = new Discord.MessageAttachment(
      data,
      "welcome-image.png"
    );

    channel.send(attachment);   
   });

client.login("TOKEN");
```

![](https://cdn.discordapp.com/attachments/797812590553333760/798267833641467954/welcome-image.png)

### OPTIONS OF WELCOME

```js
let data = await riaCanvas.welcome(member, {options})
```

**link**: Link of the background image of welcome image || String
```js
  let data = await riaCanvas.welcome(member, { link: "https://i.pinimg.com/originals/6c/d4/eb/6cd4ebf5081d9427be9a0316e664d0fc.jpg" })
```
**blur**: Disable and enable blur effect (default = true) || Boolean
```js
 let data = await riaCanvas.welcome(member, { link: "https://i.pinimg.com/originals/6c/d4/eb/6cd4ebf5081d9427be9a0316e664d0fc.jpg", blur: false }) //Disables The Blur
```
**gradiant**: Add gradiant image as background image of welcome image || String
```js
 let data = await riaCanvas.welcome(member, { gradiant: "peakblue" })
 //GRADIANTS NAME - coldsky, peakblue, pinkman, aqua, darkness, angel
```

**block**: Remove the transparent image from image
```js
 let data = await riaCanvas.welcome(member, { link: "https://i.pinimg.com/originals/6c/d4/eb/6cd4ebf5081d9427be9a0316e664d0fc.jpg", block: false })
```



## RANK CARD(CUSTOM BKGROUND)

```js
const Discord = require("discord.js");
const client = new Discord.Client();
const { CanvasRia } = require("canvas-ria")
const riaCanvas = new CanvasRia();


client.on("ready", () => {
  console.log("ready to test")
})

client.on("message", async message => {
  if(message.content === "!rank") {
    
   let data = await riaCanvas.rankcard(
     {
       link: "https://www.itl.cat/pngfile/big/47-470340_best-rainbow-wallpaper-hd-with-image-resolution-pixel.jpg",
       name: message.author.username,
       discriminator: message.author.discriminator,
       level: 10,
       rank: 6,
       currentXP: 679,
       fullXP: 1000,
       avatar: message.author.displayAvatarURL({ format: "png"})
     
     })


    
     const attachment = new Discord.MessageAttachment(
     data,
      "rank-image.png"
    );
 
    message.channel.send(attachment);   
    
    
    
  }
})

client.login("TOKEN")
```

# RESULT
![](https://cdn.discordapp.com/attachments/797812590553333760/798267832407293992/rank-image.png)
