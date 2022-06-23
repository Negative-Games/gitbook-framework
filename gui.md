# GUI

Our custom GUI / Menu framework allows you to create GUIs and GUI functions with ease. You no longer need to write boilerplate code for your menus. It's all in one class!

## Information

This is a custom abstract menu framework which allows you to create menus with ease and with custom click functions without the need of making boilerplate listeners for every menu you make.

### Highlights

* Chest GUI (9 slots, up to 6 rows)
* Hopper GUI (5 slots)
* Dropper GUI (3 slots, 3 rows)

## Chest GUI

```java
public class ExampleChestMenu extends GUI {
    public ExampleChestMenu() {
        super("&a&lTest Menu", 3);

        ItemStack diamond = new ItemStack(Material.DIAMOND);
        ItemStack iron = new ItemStack(Material.IRON_INGOT);
        ItemStack gold = new ItemStack(Material.GOLD_INGOT);
        ItemStack bedrock = new ItemStack(Material.BEDROCK);
        
        
        // Set an item without a click event
        // The reason why this is a function is because you could do conditional items.
        setItem(0, player -> {
            if (player.hasPermission("myserver.admin")) {
                return bedrock;
            } else {
                return diamond;
            }
        });
        
        // This is what you would do if you do not want conditional items.
        setItem(0, player -> diamond);
        
        // Set an item with a click event
        setItemClickEvent(1, player -> diamond, (player, event) -> {
            player.sendMessage("&aYou clicked the diamond!");
            player.closeInventory();
        });
        
        // Add an item to the next available slot without a click event
        addItem(player -> iron);
        
        // Add an item to the next available slot with a click event
        addItemClickEvent(player -> gold, (player, event) -> {
            player.sendMessage("&aYou clicked the gold!");
            player.closeInventory();
        });
    }
}
```

## Hopper GUI

```java
public class ExampleHopperGUI extends HopperGUI {
    public ExampleHopperGUI() {
        super("&6&lExample Hopper GUI");


        ItemStack diamond = new ItemStack(Material.DIAMOND);
        ItemStack iron = new ItemStack(Material.IRON_INGOT);
        ItemStack gold = new ItemStack(Material.GOLD_INGOT);
        ItemStack bedrock = new ItemStack(Material.BEDROCK);


        // Set an item without a click event
        // The reason why this is a function is because you could do conditional items.
        setItem(0, player -> {
            if (player.hasPermission("myserver.admin")) {
                return bedrock;
            } else {
                return diamond;
            }
        });

        // This is what you would do if you do not want conditional items.
        setItem(0, player -> diamond);

        // Set an item with a click event
        setItemClickEvent(1, player -> diamond, (player, event) -> {
            player.sendMessage("&aYou clicked the diamond!");
            player.closeInventory();
        });

        // Add an item to the next available slot without a click event
        addItem(player -> iron);

        // Add an item to the next available slot with a click event
        addItemClickEvent(player -> gold, (player, event) -> {
            player.sendMessage("&aYou clicked the gold!");
            player.closeInventory();
        });
    }
}
```

## Dropper GUI

```java
public class ExampleDropperGUI extends DropperGUI {
    public ExampleDropperGUI() {
        super("&6&lExample Hopper GUI");


        ItemStack diamond = new ItemStack(Material.DIAMOND);
        ItemStack iron = new ItemStack(Material.IRON_INGOT);
        ItemStack gold = new ItemStack(Material.GOLD_INGOT);
        ItemStack bedrock = new ItemStack(Material.BEDROCK);


        // Set an item without a click event
        // The reason why this is a function is because you could do conditional items.
        setItem(0, player -> {
            if (player.hasPermission("myserver.admin")) {
                return bedrock;
            } else {
                return diamond;
            }
        });

        // This is what you would do if you do not want conditional items.
        setItem(0, player -> diamond);

        // Set an item with a click event
        setItemClickEvent(1, player -> diamond, (player, event) -> {
            player.sendMessage("&aYou clicked the diamond!");
            player.closeInventory();
        });

        // Add an item to the next available slot without a click event
        addItem(player -> iron);

        // Add an item to the next available slot with a click event
        addItemClickEvent(player -> gold, (player, event) -> {
            player.sendMessage("&aYou clicked the gold!");
            player.closeInventory();
        });
    }
}
```
