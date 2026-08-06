# PiPController

画中画控制器实例。用于启动、停止画中画以及更新回调注册等。 下列API示例中都需先使用[PiPWindow.create()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法获取到PiPController实例，再通过此实例调用对应方 法。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为26.0.0。

<!--Device-PiPWindow-interface PiPController--><!--Device-PiPWindow-interface PiPController-End-->

**系统能力：** SystemCapability.Window.SessionManager

## isPiPSupported

```TypeScript
isPiPSupported(): boolean
```

判断当前设备是否支持画中画功能。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为26.0.0。

<!--Device-PiPController-isPiPSupported(): boolean--><!--Device-PiPController-isPiPSupported(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 当前设备是否支持画中画功能。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [1300014](../errorcode-window.md#1300014-画中画内部错误) | PiP internal error. |

