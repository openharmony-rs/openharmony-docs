# Counter属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件。

**继承/实现关系：** CounterAttribute extends [CommonMethod<CounterAttribute>](CommonMethod<CounterAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableDec

```TypeScript
enableDec(value: boolean)
```

设置“减少”按钮的禁用或使能。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | “减少”按钮禁用或使能。<br/>默认值：true，true表示使能“减少”按钮，false表示禁用“减少”按钮。 |

## enableInc

```TypeScript
enableInc(value: boolean)
```

设置“增加”按钮的禁用或使能。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | “增加”按钮禁用或使能。<br/>默认值：true，true表示使能“增加”按钮，false表示禁用“增加”按钮。 |

## onDec

```TypeScript
onDec(event: VoidCallback)
```

监听数值减少事件。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | VoidCallback | 是 | Counter数值减少的回调函数。<br>**起始版本：** 18 |

## onInc

```TypeScript
onInc(event: VoidCallback)
```

监听数值增加事件。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | VoidCallback | 是 | Counter数值增加的回调函数。<br>**起始版本：** 18 |

