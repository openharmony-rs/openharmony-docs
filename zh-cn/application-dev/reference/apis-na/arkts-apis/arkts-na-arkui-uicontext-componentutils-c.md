# ComponentUtils

class ComponentUtils

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class ComponentUtils--><!--Device-unnamed-export declare class ComponentUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getRectangleById

```TypeScript
getRectangleById(id: string): componentUtils.ComponentInfo
```

Provide the ability to obtain the coordinates and size of component drawing areas.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentUtils-getRectangleById(id: string): componentUtils.ComponentInfo--><!--Device-ComponentUtils-getRectangleById(id: string): componentUtils.ComponentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | ID of the component whose attributes are to be obtained. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| componentUtils.ComponentInfo | the object of ComponentInfo. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | UI execution context not found. |

