---
description: Player and server messaging, made easy.
---

# Message

Our custom messaging framework allows you to structure your messages with ease and allows you to edit placeholders with ease.

## Code Example

```java
        Message message = new Message("&7This is a custom message object with %players% online!");
        message.replace("%players%", Utils.decimalFormat(Bukkit.getOnlinePlayers().size()));
        
        // Send directly to a Player or the Console
        message.send(player);
        
        // Broadcast to all players
        message.broadcast();
```
