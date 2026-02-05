# game_controller_type.h
<!--Kit: Game Controller Kit-->
<!--Subsystem: Game-->
<!--Owner: @zhaoshuhao123-->
<!--Designer: @wudejun2025-->
<!--Tester: @csp1992-->
<!--Adviser: @luwy2025-->

## 概述

定义GameController模块的通用枚举类型。

**库：** libohgame_controller.z.so

**系统能力：** SystemCapability.Game.GameController

**起始版本：** 21

**相关模块：**[GameController](capi-game-controller.md)


## 汇总


### 类型定义

| 名称 | 描述 | 
| -------- | -------- |
| typedef enum [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) | 此枚举定义游戏控制器的错误码。 | 


### 枚举

| 名称 | 描述 | 
| -------- | -------- |
| [GameController_ErrorCode](capi-game-controller.md#gamecontroller_errorcode) {<br/>GAME_CONTROLLER_SUCCESS = 0,<br/>GAME_CONTROLLER_PARAM_ERROR = 401,<br/>GAME_CONTROLLER_MULTIMODAL_INPUT_ERROR = 32200001,<br/>GAME_CONTROLLER_NO_MEMORY = 32200002<br/>} | 游戏控制器错误码。 | 
