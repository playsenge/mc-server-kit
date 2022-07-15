### Utilities for Spigot Java Development
> by senge1337

<br>

### Modifying Weather

```java
public static enum WeatherType { SUN, RAIN, THUNDER }

public static void setWeather(World w, WeatherType wt) {
	switch(wt) {
		case SUN:
			w.setStorm(false);
			w.setThundering(false);
			break;
		case RAIN:
			w.setStorm(true);
			w.setThundering(false);
			break;
		case THUNDER:
			w.setStorm(true);
			w.setThundering(true);
			break;
	}
}
```

### ItemStack with metadata

```java
public static ItemStack item(Material material, int amount, String name, String... lore) {
		ItemStack result = new ItemStack(material, amount);
		ItemMeta meta = result.getItemMeta();

		String cName = color("&f" + name);
		List<String> cLore = new ArrayList<String>();

		for(String item: lore) {
			cLore.add(color("&f" + item));
		}

		meta.setDisplayName(cName);
		meta.setLore(cLore);

		result.setItemMeta(meta);

		return result;
}
```

### Play Sound

```java
public static void playSound(Player player, Sound sound, float volume, float pitch) {
	player.playSound(player.getLocation(), sound, SoundCategory.MASTER, volume, pitch);
}
```

### Register Listener (events)

```java
public static void registerListener(Listener listener) {
	Bukkit.getPluginManager().registerEvents(listener, Main.instance);
}
```

### Assign Command

```java
public static void assignCommand(String command, CommandExecutor executor) {
	Bukkit.getServer().getPluginCommand(command.substring(1)).setExecutor(executor);
}
```
