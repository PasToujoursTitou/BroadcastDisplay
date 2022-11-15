# BroadcastDisplay
Here's BroadcastDisplay plugin's source code.


Main.class :



package fr.titou.myplugin;

import org.bukkit.plugin.java.JavaPlugin;

public class Main extends JavaPlugin {
	@Override
	public void onEnable() {
		getCommand("broadcast").setExecutor(new CommandBroadcast());
		
	}
	

	@Override
	public void onDisable() {
		System.out.println("[DiscordDisplay] Actually disabling....");
	}
}


/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////



CommandBroadcast.class :





package fr.titou.myplugin;

import org.bukkit.Bukkit;
import org.bukkit.command.Command;
import org.bukkit.command.CommandExecutor;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;

public class CommandBroadcast implements CommandExecutor {

	@Override
	public boolean onCommand(CommandSender sender, Command cmd, String msg, String[] args) {
			if(sender instanceof Player) {
				
			
				Player player = (Player)sender;
			
				if(cmd.getName().equalsIgnoreCase("broadcast")){
					if(args.length == 0) {
						player.sendMessage("§c[§c§lBroadcastDisplay§c] §cMissing arguments! /broadcast <message>");
					}
				
				
					if(args.length >= 1) {
						StringBuilder bc = new StringBuilder();
						for(String part : args) {
							bc.append(part + " ");
						
						}
					
						Bukkit.broadcastMessage("§c§l[Broadcast]§c " + bc.toString());
					}
				
				}	
				
					return true;
			}
		
			return false;
	}

}
