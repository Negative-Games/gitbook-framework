# Input Listener

Our custom chat input listener framework allows you to listen for a player's chat input and execute code depending on what has been inputted.

## Code Example

```java
        InputListener.listen(player.getUniqueId(), response -> {
            response.setCancelled(true);
            Player user = response.getPlayer();
            user.sendMessage("You responded with: " + response.getMessage());

        });
```
