# GlobalWindowMode

窗口模式。

**起始版本：** 20

<!--Device-window-enum GlobalWindowMode--><!--Device-window-enum GlobalWindowMode-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FULLSCREEN

```TypeScript
FULLSCREEN = 1
```

全屏窗口，二进制从右往左，第一个二进制位为1。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalWindowMode-FULLSCREEN = 1--><!--Device-GlobalWindowMode-FULLSCREEN = 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## SPLIT

```TypeScript
SPLIT = 1 << 1
```

分屏窗口，二进制从右往左，第二个二进制位为1。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalWindowMode-SPLIT = 1 << 1--><!--Device-GlobalWindowMode-SPLIT = 1 << 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FLOAT

```TypeScript
FLOAT = 1 << 2
```

悬浮窗，二进制从右往左，第三个二进制位为1。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalWindowMode-FLOAT = 1 << 2--><!--Device-GlobalWindowMode-FLOAT = 1 << 2-End-->

**系统能力：** SystemCapability.Window.SessionManager

## PIP

```TypeScript
PIP = 1 << 3
```

画中画，二进制从右往左，第四个二进制位为1。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GlobalWindowMode-PIP = 1 << 3--><!--Device-GlobalWindowMode-PIP = 1 << 3-End-->

**系统能力：** SystemCapability.Window.SessionManager

