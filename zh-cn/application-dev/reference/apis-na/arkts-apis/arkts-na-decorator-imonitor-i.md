# IMonitor

当监听的变量变化时，状态管理框架侧将回调开发者注册的函数，并传入变化信息。变化信息的类型即为IMonitor类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IMonitor--><!--Device-unnamed-export declare interface IMonitor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value<T>(path?: string): IMonitorValue<T> | undefined
```

获取指定path的变化信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitor-value<T>(path?: string): IMonitorValue<T> | undefined--><!--Device-IMonitor-value<T>(path?: string): IMonitorValue<T> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 否 | 可选，被监听变量的路径。未指定时默认使用变化路径数组dirty中的第一个路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IMonitorValue](arkts-na-decorator-imonitorvalue-i.md)&lt;T&gt; |  |

## dirty

```TypeScript
dirty: Array<string>
```

变化路径的数组。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IMonitor-dirty: Array<string>--><!--Device-IMonitor-dirty: Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

