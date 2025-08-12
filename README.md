# 📘 ManagHunger Plugin Wiki

## 📌 Plugin Overview

*ManagHunger is a highly customizable lightweight plugin designed to precisely control the hunger level of players upon respawning after death.*  
*Supports per-world and per-permission-group hunger configuration, automatically detects all worlds, simple to configure, and ensures data safety.*

### 📥 Quick Installation

Start the server → Automatically generates `config.yml` on first run  
Modify the configuration as needed → Run `/managhunger reload`  
📁 Directory Structure

```
plugins/
└── ManagHunger/
    ├── config.yml         # Main configuration
    └── config_backup.yml  # Automatic backup (in case of errors)
```

## ⚙️ Configuration Details (config.yml)

### 🌍 World & Permission Group Configuration

#### Whether to send hunger change notifications to players

`show-death-message: true`

#### Default permission group (used when a player does not belong to any configured group)

```yaml
default-group: default

worlds:
  world:
    default: 10       # Regular players
    vip: 15           # VIP players
    admin: 20         # Administrators
  world_nether:
    default: 5        # Lower hunger in the Nether
  world_the_end:
    default: 0        # No hunger upon respawning in the End
```

#### World Names: Automatically scanned on plugin startup, no manual addition required.

#### Permission Groups: Compatible with LuckPerms, GroupManager, etc., using `group.<group-name>` permission nodes.

#### Value Range: 0 ~ 20 (0 = empty hunger bar, 20 = full hunger bar).

### 🎨 Custom Messages

```yaml
messages:
  plugin-enabled: "&a✓ ManagHunger enabled with world/group support."
  plugin-disabled: "&c✗ ManagHunger disabled."
  death-message: "&7[&c💀&7] &eYour hunger has been set to &f{hunger}&e."
  retain-message: "&7[&c💀&7] &eYour hunger remains: &f{hunger}&e."
  reload-success: "&a✓ Configuration reloaded!"
  error-permission: "&c❌ You don't have permission."
  error-usage-set: "&c❌ Usage: /managhunger set <world> <group> <0-20>"
  error-number: "&c❌ Invalid number."
  error-range: "&c❌ Enter a value between 0 and 20."
  current-settings: "&7📋 Current: World={world}, Group={group}, Hunger={hunger}"
```

##### *Supports color codes (e.g., &a, &c, &7) and placeholders (e.g., {hunger}, {world}, {group})*

### 🎮 In-Game Commands

| Command                                   | Permission           | Description                                              |
| ----------------------------------------- | -------------------- | -------------------------------------------------------- |
| `/managhunger help`                       | Everyone             | View the help menu                                       |
| `/managhunger check`                      | Everyone             | Display your hunger settings for the current world/group |
| `/managhunger reload`                     | `managhunger.reload` | Reload configuration (automatically backs up)            |
| `/managhunger set <world> <group> <0-20>` | `managhunger.set`    | Set hunger value for a specific world and group          |

Example:  
`/managhunger set world vip 18`  
Sets the respawn hunger value to 18 for the `vip` group in the `world` world.

### 🔐 Permission Nodes

| Node                 | Default                          | Description               |
| -------------------- | -------------------------------- | ------------------------- |
| `managhunger.*`      | OP                               | All permissions           |
| `managhunger.reload` | OP                               | Reload configuration      |
| `managhunger.set`    | OP                               | Modify hunger values      |
| `managhunger.check`  | Everyone                         | View settings             |
| `group.<group-name>` | Inherited from permission plugin | Determines player's group |

## FAQ

### How to back up the configuration?  

`Each /managhunger reload automatically backs up config.yml to config_backup.yml`

### Configuration not taking effect?  

``Check if /managhunger reload shows a success message; verify world and group names for correct capitalization`
