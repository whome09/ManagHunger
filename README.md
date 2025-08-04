# ManagHunger Plugin Wiki

## Introduction

ManagHunger is a Bukkit/Spigot plugin designed to manage player hunger levels after death. It supports customizable hunger retention rules and flexible messaging systems.

------

## Installation

1. 1.Place `ManagHunger.jar` into your server’s `plugins` directory.
2. 2.Restart the server.
3. 3.Verify installation with `/managhunger check`.

------

## Core Features

### 1. Post-Death Hunger Management

- •**Default Behavior**: Reset hunger to `0` after death (configurable).
- •**Retention Mode**: Retains the player’s pre-death hunger if it was higher than the configured value.

### 2. Messaging System

Customizable messages for:

- •Death notifications
- •Retention confirmations
- •Configuration success prompts
- •Permission error alerts

------

## Configuration Guide

yaml

复制

```yaml
# Edit server/plugins/ManagHunger/config.yml  
hunger-after-death: 5       # Default hunger value after death (0-20)  
show-death-message: true    # Enable/disable death messages  

messages:  
  death-message: "&cYour hunger has been reset to {hunger}"  # Supports color codes & placeholders  
  retain-message: "&aRetained hunger: {hunger}"  
```

------

## Commands

|        Command        |      Permission      |            Description             |
| :-------------------: | :------------------: | :--------------------------------: |
| `/managhunger reload` | `managhunger.reload` |  Reload the plugin configuration   |
| `/managhunger set 10` |  `managhunger.set`   | Set post-death hunger value (0-20) |
| `/managhunger check`  |         None         |       View current settings        |

------

## Permissions

|         Node         | Default |       Function       |
| :------------------: | :-----: | :------------------: |
|   `managhunger.*`    |   OP    |     Full access      |
| `managhunger.reload` |   OP    | Reload configuration |
|  `managhunger.set`   |   OP    | Modify hunger values |
| `managhunger.bypass` |  False  | Bypass hunger reset  |

------

## FAQs

**Q1: Configuration changes aren’t working?**
A1: Reload the plugin with `/managhunger reload` or restart the server.

**Q2: Color codes aren’t displaying in messages?**
A2: Ensure valid color codes (e.g., `&cRed`).

**Q3: How to retain pre-death hunger?**
A3: If a player’s hunger before death exceeds the `hunger-after-death` value, it will be retained.
