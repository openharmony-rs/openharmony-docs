# InterceptionModeCallback

```TypeScript
declare type InterceptionModeCallback = (mode: NavigationMode) => void
```

Navigation单双栏显示状态发生变更时的拦截回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | NavigationMode | 是 | 导航页的显示模式。 |

