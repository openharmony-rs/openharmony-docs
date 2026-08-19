# sendMouseEvent

## 导入模块

```TypeScript
```

## sendMouseEvent

```TypeScript
export declare function sendMouseEvent(event: MouseEvent): boolean
```

发送鼠标事件。 此接口仅用于对应用的测试。由于耗时长，不建议使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function sendMouseEvent(event: MouseEvent): boolean--><!--Device-unnamed-export declare function sendMouseEvent(event: MouseEvent): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | MouseEvent | 是 | 鼠标事件，event参数见MouseEvent介绍。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 事件发送失败时返回false，其余情况返回true。 |

