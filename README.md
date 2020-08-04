# Wie mache ich einen sich nach einem Zeitraum wechselnden Status eine Discord.js Bots?

Dieser Code sollte (ungefähr) bei dir am Anfang stehen:

```javascript
  const Discord = require("discord.js"); // Wir holen das Paket “discord.js”
  const client = new Discord.Client();
```

## Der Statuswechselcode

Nach dem oben stehenden Code sollte folgendes vorkommen:

```javascript

client.on("ready", () =>  {
  client.user.setStatus("online")//Setzt den Status auf Online
  
  let statuses = [
    {
      name: `Minecraft`,//Erklärt sich glaube ich von selbst
      type: "PLAYING"//Spielt (der name Oben)
    },
    {
      name: `Spotify`,
      type: "LISTENING"//Hört (der name oben) zu
    },
    {
      name: `RedCrafter07.de`,
      type: "WATCHING"//schaut (der name oben) zu
    },
    {
      name: "live"
      type: "STREAMING"//Streamt (der name oben),
      url: "https://twitch.tv/redcrafter07_live"//angeben, falls darunter ein Knopf sein soll, der zur URL führt ; nur bei dem Streamt-Status verfügbar (!)      
  ];
  
  setInterval(function() {
    let status = statuses[Math.floor(Math.random() * statuses.length)];//Status zufällig auswählen
    client.user.setActivity(status);//Den Status setzen
  }, 10000);//Intervall festlegen, die Zahl steht für die ms.
})

```

Falls du weitere Fragen hast, melde dich in der "Issues" - Abteilung, ich probiere schnellstmöglich zu antworten. 
