# Commands

Our custom command framework allows you to add commands to the server without the need of registering your command in plugin.yml. It also contains some extra features which improves your quality of life when it comes to making commands.

## Information

This is a custom abstract command framework which allows you to build commands relatively quickly and in a more advanced way with more accessibility to certain features in commands and an expansion of the regular command system.

### Highlights

* Registering commands without the need of plugin.yml
* Annotation based command information
  * With the option of using regular method based command information
* SubCommand system to remove boilerplate
* "ShortCommands" similar to essentials' /gamemode creative and /gmc subcommands
* Automatic argument checking
* Tab Completion Editing
* Command method is void so you do not need to return true or false
* Other useful utilities

## Command

Code example

```java
@CommandInfo(
    name = "mycommand", // Main Name of the Command
    aliases = {"alias1", "alias2"}, // List of aliases of the Command
    permission = "my.permission", // Permission node of the Command
    playerOnly = true, // If true, only players can use this Command
    consoleOnly = false, // if true, only console can use this Command
    args = {"player"} // Required arguments, removes boilerplate for checking for argument length
    // Will show off short commands in the subcommand section
)
public class CommandExample extends Command {

    public CommandExample() {
        addSubCommands(
           new SubCommandExample()
        );

        setTabComplete((sender, args) -> {
            if (args.length == 1) {
                if (args[0].equalsIgnoreCase("bob")) {
                    return Collections.singletonList("bob");
                }
               return null;
            }
            return null;
        });
    }

    @Override
    public void onCommand(CommandSender sender, String[] args) {
         // There is no need to check the argument length because we have
         // it stated in the CommandInfo annotation.
         String playerName = args[0]
         // Do stuff with this playerName 
    }
}
```

## SubCommand

Code example:

```java
@CommandInfo(
    name = "mysubcommand", // Main Name of the Command
    aliases = {"alias1", "alias2"}, // List of aliases of the Command
    permission = "my.permission", // Permission node of the Command
    playerOnly = true, // If true, only players can use this Command
    consoleOnly = false, // if true, only console can use this Command
    args = {"player"} // Required arguments, removes boilerplate for checking for argument length
    shortCommands = {"gmc"} // Bascially a short command will turn /mycommand mysubcommand to /gmc without needing to write duplicate code to 
                            // compensate for it
)
public class SubCommandExample extends SubCommand {

    public SubCommandExample() {
        addSubCommands(
            // You can add subcommands to subcommands
        );

   
    }

    @Override
    public void onCommand(CommandSender sender, String[] args) {
         // There is no need to check the argument length because we have
         // it stated in the CommandInfo annotation.
         String playerName = args[0]
         // Do stuff with this playerName 
    }
}
```
