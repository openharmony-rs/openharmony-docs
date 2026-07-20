# ModalityType

子窗口模态类型枚举。

**起始版本：** 14

<!--Device-window-enum ModalityType--><!--Device-window-enum ModalityType-End-->

**系统能力：** SystemCapability.Window.SessionManager

## WINDOW_MODALITY

```TypeScript
WINDOW_MODALITY = 0
```

当仅需要其父级窗口不响应用户操作时，可选此参数。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ModalityType-WINDOW_MODALITY = 0--><!--Device-ModalityType-WINDOW_MODALITY = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager

## APPLICATION_MODALITY

```TypeScript
APPLICATION_MODALITY = 1
```

除其父级窗口外还需要该应用其他实例的窗口不响应用户操作时，可选此参数。

该枚举在支持并处于[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态的设备上可正常调用；在支持但不处于[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态的设备及不支持[自由窗口](docroot://windowmanager/window-terminology.md#自由窗口)状态的设备上调用返回801错误码。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ModalityType-APPLICATION_MODALITY = 1--><!--Device-ModalityType-APPLICATION_MODALITY = 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

