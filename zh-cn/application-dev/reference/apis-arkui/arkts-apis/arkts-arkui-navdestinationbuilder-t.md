# NavDestinationBuilder

```TypeScript
export type NavDestinationBuilder = (name: string, param?: Object) => void
```

用于创建NavDestination组件内容的构建器类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 否 | NavDestination页面详细参数。默认值为空。 |
