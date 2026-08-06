# OnGetPreviewBadgeCallback

```TypeScript
declare type OnGetPreviewBadgeCallback = () => boolean | number
```

即将启动多选长按聚拢动画时，触发用于获取选中数量的回调。 返回true表示显示选中数量角标，对应Grid或List显示范围内选中item数量；false表示不显示角标。 返回数字时默认显示角标，该数字表示角标中需要显示的数量。取值范围：[0, 2\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_31\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_-1]，超过取值范围时按返回true处理。 返回浮点数时，向下取整。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnGetPreviewBadgeCallback = () => boolean | number--><!--Device-unnamed-declare type OnGetPreviewBadgeCallback = () => boolean | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

