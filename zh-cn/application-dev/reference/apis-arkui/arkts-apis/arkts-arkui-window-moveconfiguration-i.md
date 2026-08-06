# MoveConfiguration

窗口移动选项。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-window-interface MoveConfiguration--><!--Device-window-interface MoveConfiguration-End-->

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId?: long
```

目标屏幕ID，该参数应为整数，输入非整数时将向下取整。默认值为undefined。填入该参数时，将移动到相对于目标屏幕左上角的指定位置。此参数不传、传undefined或传入目标屏幕ID不存在时，将移动到相对于当前屏幕左上角的 指定位置。

**类型：** long

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-MoveConfiguration-displayId?: long--><!--Device-MoveConfiguration-displayId?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

