# Optional

```TypeScript
declare type Optional<T> = T | undefined
```

定义可选类型，其值可以是undefined。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type Optional<T> = T | undefined--><!--Device-unnamed-declare type Optional<T> = T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| T | The object can be of any custom type. |
| undefined | The object can be **undefined**. |

