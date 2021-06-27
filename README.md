require("dotenv").config()
const Discord = require('discord.js')
const client = new Discord.Client();

client.on("ready", () => {
  console.log("bot is online");
  client.user
    .setActivity("!h = עזרה", { type: "" })
    .catch(console.error); 
});

  const token = "ODU0MzkyNTAxNTE5NTE1Njg4.YMjRBg.OjozQ-xyrZS5m9eQxBeNInIp67k"

  const prefix = "!"

  client.on("message", async message => {
    if(message.author.bot) return;
    if (!message.guild) return;
    const args = message.content.slice(prefix.length).trim().split(/ +/g);
//MY CMD'S

if(message.content === '!ping') {
  message.channel.send(`🏓 Pong!
  Ping is ${Math.round(client.ws.ping)}ms`);
 }

 if (message.content.startsWith(`!h`)) {
  let voicechannel = message.member.voice.channel
  let reason = args.join(" ")
  let embed = new Discord.MessageEmbed()
      .setColor("RED")
      .setTitle("Helpme")
      .setDescription(`${message.author.username} **צריך עזרה!**`)
      .addField(`המשתמש נמצא בחדר: `, voicechannel || "**המשתמש לא נמצא בחדר דיבור!**")
      .addField(`**סיבה**:`, reason || "**אין סיבה**")
      .setThumbnail('')
      .setTimestamp()
      
       message.channel.send('@Support', embed);
      
      }
      if (message.content.startsWith(`${prefix}sug`)) {
          let embed = new Discord.MessageEmbed()
          .setColor("GREEN")
          .setTitle("new sug")
          .setDescription((args.join(" ")).slice(5)) 
          .setFooter(`This sug created by ${message.author.username}`)
          .setTimestamp()
          if(!args[1]) return message.channel.send("please specify a sug reason")
          message.delete()
          let MessageEmbed = await message.channel.send(embed);
          await MessageEmbed.react('👍')
          await MessageEmbed.react('👎')
      
  }

  if (message.content.startsWith("https://", "www.")) {   ////חוסם קישורים
  if (!message.member.hasPermission("ADMINISTRATOR")) return;
  message.delete().then(message.channel.send(". בבקשה לא לפרסם"))
  }
  
  if(message.content === "!iq") {

      const number = Math.floor(Math.random() * 200) + 0;
    message.reply("יש לך " + number + " אייקיו!");

    }

    if(message.content.startsWith(prefix+'av')){
  
      
      if(message.mentions.users.size){
          let member=message.mentions.users.first()
      if(member){
          const emb=new Discord.MessageEmbed().setImage(member.displayAvatarURL()).setTitle(member.username).setColor(GREEN)
          message.channel.send(emb)
          
      }
      else{
          message.channel.send("Sorry none found with that name")

      }
      }else{
          const emb=new Discord.MessageEmbed().setImage(message.author.displayAvatarURL()).setTitle(message.author.username)
       
          .setDescription('__𝕐𝕠𝕦𝕣 𝕡𝕣𝕠𝕗𝕚𝕝𝕖__')
          .setURL("https://cdn.discordapp.com/avatars/758366514788565034/c1931fb27e7a172c92cb68d44a08b575.webp")
          .setThumbnail("https://cdn.discordapp.com/avatars/758366514788565034/c1931fb27e7a172c92cb68d44a08b575.webp~")
         .setTitle('ℂ𝕝𝕚𝕔𝕜 𝕙𝕖𝕣𝕖 𝕥𝕠 𝕤𝕖𝕖 𝕪𝕠𝕦𝕣 𝕡𝕙𝕠𝕥𝕠.')
         .setURL("")

          message.channel.send(emb)
      }
}

if (message.content.startsWith(`${prefix}-rep`)) {
  let embed = new Discord.MessageEmbed()
  .setColor("GREEN")
  .setTitle("new -rep")
  .setDescription((args.join(" ")).slice(5)) 
  .setFooter(`This -rep created by ${message.author.username}`)
  .setTimestamp()
  if(!args[1]) return message.channel.send("please specify a -rep reason")
  message.delete()
  let MessageEmbed = await message.channel.send(embed);
  await MessageEmbed.react('👍')
  await MessageEmbed.react('👎')

}

if (message.content.startsWith(`${prefix}+rep`)) {
  let embed = new Discord.MessageEmbed()
  .setColor("GREEN")
  .setTitle("new +rep")
  .setDescription((args.join(" ")).slice(5)) 
  .setFooter(`This +rep created by ${message.author.username}`)
  .setTimestamp()
  if(!args[1]) return message.channel.send("please specify a +rep reason")
  message.delete()
  let MessageEmbed = await message.channel.send(embed);
  await MessageEmbed.react('👍')
  await MessageEmbed.react('👎')

}

});

client.login(token);
