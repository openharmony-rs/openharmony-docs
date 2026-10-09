# game_controller_type.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @weixin_42784160-->
<!--Designer: @wudejun2025-->
<!--Tester: @fei_0805-->
<!--Adviser: @luwy2025-->

## Overview

Defines common enumeration types for the **GameController** module.

**File to include:** <GameControllerKit/game_controller_type.h>

**Library:** libohgame_controller.z.so

**System capability:** SystemCapability.Game.GameController

**Since:** 21

**Related module:** [GameController](capi-gamecontroller.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [GameController_ErrorCode](#gamecontroller_errorcode) | GameController_ErrorCode | Defines error codes of the game controller.|

## Enum Description

### GameController_ErrorCode

```c
enum GameController_ErrorCode
```

**Description**

Defines error codes of the game controller.

**System capability:** SystemCapability.Game.GameController

**Since:** 21

| Value| Description|
| -- | -- |
| GAME_CONTROLLER_SUCCESS = 0 | Success.<br>**Since:** 21|
| GAME_CONTROLLER_PARAM_ERROR = 401 |  Invalid parameter.<br>**Since:** 21|
| GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR = 32200001 |  Failed to query all device information in multimodal input.<br>**Since:** 21|
| GAME_CONTROLLER_NO_MEMORY = 32200002 |  Insufficient device memory.<br>**Since:** 21|
