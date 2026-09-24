# CopyOptions

```TypeScript
declare enum CopyOptions
```

剪贴板复制范围。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None = 0
```

不支持复制。

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## InApp

```TypeScript
InApp = 1
```

支持仅在当前应用内复制粘贴。

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LocalDevice

```TypeScript
LocalDevice = 2
```

支持复制后在所有应用内粘贴。

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CROSS_DEVICE

```TypeScript
CROSS_DEVICE = 3
```

支持跨设备复制。

**起始版本：** 11

**废弃版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
