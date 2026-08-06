# Key

按键。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export declare interface Key--><!--Device-unnamed-export declare interface Key-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## code

```TypeScript
code: KeyCode
```

键值。

**类型：** KeyCode

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Key-code: KeyCode--><!--Device-Key-code: KeyCode-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## deviceId

```TypeScript
deviceId: int
```

输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Key-deviceId: int--><!--Device-Key-deviceId: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## pressedTime

```TypeScript
pressedTime: long
```

按键按下时间，表示系统启动运行至今逝去的微秒数，单位为微秒（μs）。

**类型：** long

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Key-pressedTime: long--><!--Device-Key-pressedTime: long-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

