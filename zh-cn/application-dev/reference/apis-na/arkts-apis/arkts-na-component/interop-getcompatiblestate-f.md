# getCompatibleState

## getCompatibleState

```TypeScript
export declare function getCompatibleState<T>(state: IDecoratedV1Variable<T>): ESValue
```

为ArkTS-Sta的状态变量获取一个ArkTS-Dyn的@State代理对象，用于与ArkTS-Dyn的状态变量进行互操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function getCompatibleState<T>(state: IDecoratedV1Variable<T>): ESValue--><!--Device-unnamed-export declare function getCompatibleState<T>(state: IDecoratedV1Variable<T>): ESValue-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | ArkTS-Sta的状态变量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ESValue | ArkTS-Dyn的 |

