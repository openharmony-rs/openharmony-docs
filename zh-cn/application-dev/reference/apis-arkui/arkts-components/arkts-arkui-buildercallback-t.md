# BuilderCallback

```TypeScript
declare type BuilderCallback = (...args: Args) => void
```

定义mutableBuilder中使用的回调类型。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | Args | 是 | MutableBuilder的参数。 |

