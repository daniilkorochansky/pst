# PST-0002: Project Structure and Includes

```text
PST: 0002
Title: Project Structure and Includes
Author: Daniil Korochansky (https://github.com/daniilkorochansky)
Status: Draft
Type: Standards
Created: 20-Jun-2026
```

## 1. Introduction

The traditional way of developing SA-MP/open.mp servers involved writing code within a single, monolithic `.pwn` file. This approach leads to poor code maintainability, breaks team collaboration via Git, and makes testing impossible.

This standard establishes a strict, component-based modular structure for Pawn projects. It separates core initialization, business logic (modules), and configuration files.

## 2. Directory Layout

Every modern Pawn project conforming to PST MUST follow this unified folder structure:

```text
📁 your-project/
  ├── 📁 gamemodes/            # Main entry points
  │    └── 📄 main.pwn         # Minimalistic core compiler entry file
  ├── 📁 modules/            # Feature-based business logic (or "core", "systems")
  │    ├── 📁 core/            # Core systems (database, accounts, players)
  │    │    ├── 📄 database.inc
  │    │    └── 📄 player.inc
  │    └── 📁 vehicles/        # Specific feature module
  │         ├── 📄 callbacks.inc
  │         ├── 📄 commands.inc
  │         └── 📄 core.inc
  ├── 📁 scriptfiles/          # Server runtime assets (data, logs, configs)
  ├── 📄 pawn.json / pawn.yaml # Dependency management configuration (sampctl)
  └── 📄 README.md
```

### Key Rules:
* **The Monolith is Dead**: The `gamemodes/main.pwn` file MUST contain only the compiler configurations, macro definitions, and the master entry point. No heavy business logic should be written there.
* **Feature-Based Modules**: Code must be separated by features (e.g., `vehicles`, `houses`, `factions`), not by type (do not put all commands in one huge file and all callbacks in another).

## 3. Hooking and Event Handling

When working with modular include files, redefining standard callbacks like `OnPlayerConnect` inside includes causes conflicts. 

* PST strongly forbids using standard ALS (Advanced Library System) hooks manually inside feature modules, as they are verbose and error-prone.
* Developers MUST use a modern hooking system, preferably **`y_hooks`** from the YSI library or native open.mp hooks.

```pawn
// CORRECT (Using y_hooks / modern framework approach):
// In modules/vehicles/callbacks.inc
#include <YSI_Coding\y_hooks>

hook OnPlayerConnect(playerid)
{
    // Initialize vehicle-related player variables here smoothly
    return 1;
}
```

## 4. Include Guards

To prevent compilation errors caused by duplicate include statements across different files, every `.inc` file MUST use include guards.

```pawn
// CORRECT:
// In q_modules/core/database.inc
#if defined _MODULE_DATABASE_INCLUDED
    #endinput
#endif
#define _MODULE_DATABASE_INCLUDED

// Module code goes here
```

## 5. Backward Compatibility and Tooling

Adopting a modular structure changes how errors are tracked by the compiler. Because errors will now point to specific lines inside separate `.inc` files rather than one large `.pwn` file.

Modern tooling, specifically the [Spawn IDE](https://github.com/daniilkorochansky/spawn), eliminates this friction:
* **Global Compilation**: Spawn allows you to trigger the project compilation from any opened include file, automatically linking it to the master gamemode.
* **File Management**: The built-in workspace sidebar and tabs make switching between modules faster and more intuitive compared to retro editors.

As the ecosystem evolves, automated tools will further simplify navigation across modular codebases.
