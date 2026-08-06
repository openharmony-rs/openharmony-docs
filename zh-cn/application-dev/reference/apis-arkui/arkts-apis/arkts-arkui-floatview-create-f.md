# create

## create

```TypeScript
function create(config: FloatViewConfiguration): Promise<FloatViewController>
```

创建标准悬浮窗控制器。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-floatView-function create(config: FloatViewConfiguration): Promise<FloatViewController>--><!--Device-floatView-function create(config: FloatViewConfiguration): Promise<FloatViewController>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 创建标准悬浮窗控制器的参数。该参数以及构造该参数的context不能为null或者undefined，否则抛出401。其他参数异常情况抛出1300016。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FloatViewController&gt; | Promise对象。返回当前创建的标准悬浮窗控制器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible cause: Call the API on unsupported device. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. Possible cause:1. This window context is abnormal.2. System error, such as a null pointer, insufficient memory or a JS engine exception. |
| [1300016](../errorcode-window.md#1300016-参数校验错误) | Parameter error.Possible cause: Invalid template type. |

