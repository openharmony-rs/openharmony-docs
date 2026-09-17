# game_controller_type.h

## Overview

Defines common enumeration types for the GameController module.

**Library**: libohgame_controller.z.so

**System capability**: SystemCapability.Game.GameController

**Since**: 21

**Related module**: [GameController](capi-gamecontroller.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [GameController_ErrorCode](#gamecontroller_errorcode) | GameController_ErrorCode | Defines error codes of the game controller. |

## Enum type description

### GameController_ErrorCode

```c
enum GameController_ErrorCode
```

**Description**

Defines error codes of the game controller.

**Since**: 21

| Enum item | Description |
| -- | -- |
| GAME_CONTROLLER_SUCCESS = 0 |  |
| GAME_CONTROLLER_PARAM_ERROR = 401 |  Invalid parameter. <br>**Since**: 21 |
| GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR = 32200001 |  Failed to query all game device information in multimodal input. <br>**Since**: 21 |
| GAME_CONTROLLER_NO_MEMORY = 32200002 |  Insufficient game device memory. <br>**Since**: 21 |


