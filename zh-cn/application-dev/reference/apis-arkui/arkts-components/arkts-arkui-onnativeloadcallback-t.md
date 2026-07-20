# OnNativeLoadCallback

```TypeScript
declare type OnNativeLoadCallback = (event?: object) => void
```

当XComponent所持有的surface创建完成后触发。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnNativeLoadCallback = (event?: object) => void--><!--Device-unnamed-declare type OnNativeLoadCallback = (event?: object) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | object | 否 | XComponent对象的context。 context中包含的接口由开发者在native层定义。  |

