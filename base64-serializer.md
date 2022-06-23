---
description: Convert things to and from Base64!
---

# Base64 Serializer

Our custom base64 serialized framework allows you to serialize items and inventories to base64 and deserialize items and inventories from base64 with relative ease.

### ItemStacks

```java
// Converting an itemstack to and from base64
ItemStack item = player.getItemInHand();

// This is the base64 code that you can save wherever you want
String base64 = BukkitSerializer.itemStackArrayToBase64(new ItemStack[]{item})

// This is the item resulting from the base64 code you provided
ItemStack converted = BukkitSerializer.itemStackArrayFromBase64(base64)[0];
```

### Inventories

```java
String[] inv = BukkitSerializer.playerInventoryToBase64(player.getInventory());
String contentsBase64 = inv[0]
String armorBase64 = inv[1]

Inventory inventory = BukkitSerializer.inventoryFromBase64(contentsBase64);
ItemStack[] armor = BukkitSerializer.itemStackArrayFromBase64(armorBase64);
```
