# Item Builder

Our custom item building framework allows you to build items with ease without the need of boilerplate ItemMeta code and other annoying things that you need to do when you make items.

## Code Example

```java
ItemStack item = new ItemBuilder(Material.STONE).setName("&c&lCool stone").addLoreLine("&7&oThis is a cool stone").build();
```
