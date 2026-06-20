# PST-0001: Code Style Guide
```text
PST: 0001
Title: Code Style Guide
Author: Daniil Korochansky (https://github.com/daniilkorochansky)
Status: Draft
Type: Standards
Created: 20-Jun-2026
```

## 1. Introduction

The purpose of this standard is to make the code for Pawn-based server mods readable, maintainable, and consistent. When all developers follow the same style, newcomers can get up to speed more quickly, and debugging becomes easier.

## 2. Text Formatting and Indents

* **Indentation:** Use only **Tabs**. Spaces for indentation are not allowed. It is recommended that you set the visual tab width in the editor to 4 spaces.
* **String length:** The maximum line length is 120 characters. If a line is longer, it must be wrapped using a line break character (`\`) or split logically.
* **Line endings:** We recommend using the **LF** (Unix) or **CRLF** (Windows) format, but the style should be consistent throughout the project.

*Encoding Declaration:* To ensure seamless transition between legacy and modern projects, PST introduces explicit encoding declarations via source code comments. An IDE or editor should scan the beginning of the file for an encoding declaration:

```pawn
  // -*- coding: utf-8 -*-
  ```
  for older gamemodes:
  ```pawn
  // -*- coding: cp1251 -*-
  ```
  
  If no encoding declaration is present, the IDE must fallback to **UTF-8 without BOM** as the default standard. This prevents compiler errors caused by Byte Order Marks and ensures cross-platform compatibility.

## 3. Braces Style

PST recommends using the **Allman style** (brackets on a new line) for functions, callbacks, loops, and conditions. This style ensures maximum vertical readability in Pawn.

```pawn
// CORRECT:
if (IsPlayerAdmin(playerid))
{
    SetPlayerHealth(playerid, 100.0);
}
else
{
    SendClientMessage(playerid, -1, "You're not an admin!");
}

// INCORRECT (Egyptian brackets):
if (IsPlayerAdmin(playerid)) {
    SetPlayerHealth(playerid, 100.0);
}
```

*Exception:* Single-line conditions can be written without brackets if this does not impair readability:
```pawn
if (!IsPlayerConnected(playerid)) return 1;
```

## 4. Naming Conventions

Magic abbreviations are prohibited. Names must reflect the essence of the variable or function.

* **Callbacks and Hooks:** `PascalCase` is used.
  * *Example:* `ForwardPlayerToCoordinates`, `OnPlayerConnect`.
* **Local and global variables:** `camelCase` is used.
  * *Example:* `localVariable`, `playerTargetVehicle`.
* **Constants and Macros (`#define`):** `UPPER_CASE` with underscores is used.
  * *Example:* `MAX_FACTIONS`, `MAX_ADMIN_LEVEL`.
* **Enumerations (`enum`):** The name of the enumeration itself is written in `PascalCase`, and its elements are written in `UPPER_CASE` with a prefix.
  * *Example:*
    ```pawn
    enum E_PLAYER_DATA
    {
        P_ID,
        P_NAME[MAX_PLAYER_NAME],
        P_MONEY
    }
    ```

## 5. Spaces in expressions

To improve the readability of formulas and conditions, spaces are inserted as follows:

* Regarding assignment, comparison, and arithmetic operators:
  ```pawn
  // CORRECT:
  new score = 10 + 5;
  if (amount >= 100)

  // INCORRECT:
  new score=10+5;
  if(amount>=100)
  ```
* After commas in function arguments (but not before them):
  ```pawn
  // CORRECT:
  GivePlayerMoney(playerid, 5000);
  ```

## 6. Code Comments

* **Documenting Functions:** Each major custom function should be preceded by a brief comment.
* **Line comments:** Use `//` to explain complex or non-obvious sections of logic. Do not comment out obvious code.
  ```pawn
  // CORRECT:
  // We check to see if the player is trying to sell a house to themselves through an ID vulnerability
  if (buyerid == sellerid) return 0; 

  // INCORRECT:
  SetPlayerHealth(playerid, 0.0); // Kill a player
  ```
