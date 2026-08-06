# KeyOptions

表示按键操作的选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-declare interface KeyOptions--><!--Device-unnamed-declare interface KeyOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## key1

```TypeScript
key1?: int
```

操作期间要按下的第一个键码。 如果未设置，将不会注入任何按键事件。 如果仅设置 key2 而未设置 key1，将会导致业务错误 17000007。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-KeyOptions-key1?: int--><!--Device-KeyOptions-key1?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## key2

```TypeScript
key2?: int
```

操作期间要按下的第一个键码。 如果未设置，将不会注入任何按键事件。 如果仅设置 key2 而未设置 key1，将会导致业务错误 17000007。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-KeyOptions-key2?: int--><!--Device-KeyOptions-key2?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

