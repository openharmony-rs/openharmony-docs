# CalleeCallback

通用组件服务端注册消息通知的回调函数类型。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## constructor

```TypeScript
(indata: rpc.MessageSequence): rpc.Parcelable
```

定义Callee的回调函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indata | rpc.MessageSequence | 是 | 发送需传递的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| rpc.Parcelable | 返回的数据对象。 |

