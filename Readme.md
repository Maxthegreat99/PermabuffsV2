# PermabuffsV2
Updated version of Permabuffs plugin
- Originally made by [Zaicon](https://github.com/Zaicon).
- `README` created by [moisterrific](https://github.com/moisterrific).
- Updated to `1.4` by [Quinci135](https://github.com/Quinci135).
- Updated to **TShock** `5` by [RenderBr](https://github.com/RenderBr).
- Updated to **TShock** `5.2` by Maxthegreat99.

## Overview
### Features:
- When active, any buff is auto-renewed until the command is turned off.
- This includes player buffs being saved even if the server is shut down.
- Definable buff groups with specific permissions.
- For staff, there is a command to view which permabuffs players have active.
- There are also global buffs, which affect anyone on the server at the time.
- Region buffs can buff everyone in a certain region with a buff that lasts a specified duration once they leave the region.

### Commands:
- `/permabuff [-g] <buff name or id>/[buff group name]`: Activates the specified buff, `-g` parameter can be used to activate the buffs from a specified buff group the player has access to.
- `/buffcheck <player>`: Gives a list of permabuffs that the specified player has active.
- `/gpermabuff <buff name or id> <player>`: Activates/desactivates the specified buff for the specified player.
- `/gpermabuff -g <"list"/buff group name> <player>`: gives the buffs from the specified group to the targetted player, the "list" parameter can be used to list the sender's available buff groups.  
- `/regionbuff <add/del> <region name> <buff name or ID> [duration in seconds]`: adds/deletes the specified buff to the targetted region, the `[duration]` specifies how long the buff will last when given/renewed for the player.
- `/regionbuff -g <add/del> <region name> <group name> [duration in seconds]`: adds/deletes every buff from a specified group for the targetted region, the `[duration]` parameter applies for every buff added to the region within the group.
- `/globalbuff <buff name or id/clearall>`: Activates or deactivates a global buff, the `clearall` parameter can be used to clear all the current globalbuffs active.
- `/clearbuffs <all or */-s> [-pb [duration in ticks]/-all/-x] `: Deactivates all active permabuffs for the target, the `all/*` parameter is used to target every player while the `-s` targets the sender. The command has three parameter specifiers linked to cleaning buff slots, `-all` cleans every slot after disabling permabuffs, `-pb [duration]` cleans the slots with the permabuffs but sets every other buffs to the specified duration, `-x` can be used with `-all` to **not** disable permabuffs and only clean the target's buff slots(ex. `/clearbuffs * -all -x`, doesnt disables permabuffs and cleans removes every buffs the player currently has).
- `/pbreload`: Reloads the config file.

### Config:
- `globalbuffs`: The list of globalbuffs active in the server.
- `buffgroups`:
- - `groupName`: The name of the buff group.
- - `groupPerm`: The permission needed to use permabuffs in this group. (Note that the permission is "pb." + the groupPerm.)
- - `isperma`: If set to false, the buff will still be given, but will not be auto-renewed (useful for "pet" buffs and for use to replace /buff, if players shouldn't have access to every buff).
- - `buffIDs`: The list of buff IDs to include in this group.​
- `regionbuffs`:
- - `regionName`: The name of the region to apply the buffs in.
- - `buffs`: A list of pairs of buff IDs and duration (in seconds).​

## Permissions: 
- `pb.use`: Allows a player to use /permabuff and /clearbuffs (on themselves)
- `pb.check`: Allows a player to use /buffcheck.
- `pb.give`: Allows a player to use /gpermabuff.
- `pb.clear`: Allows a player to deactivate all active buffs for everyone.
- `pb.region`: Allows a player to add/delete region buffs.
- `pb.global`: Allows a player to set global buffs.
- `pb.ignoreglobal`: Makess a player not receive global buffs from the server.
- `pb.setduration`: Allows a player to use the -pb parameter with the /clearbuffs command.
- `pb.reload`: Allows a player to reload the config file.

Players can only use /permabuff on buffs in groups that they have permission to access. To allow a player to permabuff themselves with buffs in a certain group, use pb.<groupPerm>. To allow a player to permabuff themselves with buffs from any group, use pb.useall.

Ex: pb.probuffs, pb.petbuffs, pb.debuffs are the necessary permissions to use buffs in the default groups. 

## Installation Guide:
1. Place Plugin into ServerPlugins folder.
2. Restart server.
3. Open the PermabuffsConfig.json file and make any desired changes.
4. Use /pbreload. 

Source: [Permabuffs | TShock for Terraria](https://tshock.co/xf/index.php?resources/permabuffs.5/)
