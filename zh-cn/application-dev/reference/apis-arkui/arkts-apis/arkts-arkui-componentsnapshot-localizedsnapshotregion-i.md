# LocalizedSnapshotRegion

定义组件截图的矩形区域，start和end的值在布局方向为LTR时指定为left和right，在布局方向为RTL时指定为right和left。 > **说明：** > > 直接使用componentSnapshot可能导致\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的问题，建议使用getUIContext()获取 > [UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_实例，并使用[getComponentSnapshot]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ > 获取绑定实例的componentSnapshot。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

<!--Device-componentSnapshot-interface LocalizedSnapshotRegion--><!--Device-componentSnapshot-interface LocalizedSnapshotRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom: number
```

截图区域矩形右下角的y轴坐标。 单位：px 取值范围：[0, 组件高度]

**类型：** number

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedSnapshotRegion-bottom: number--><!--Device-LocalizedSnapshotRegion-bottom: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end: number
```

布局方向为LTR时表示截图区域矩形右下角的x轴坐标，布局方向为RTL时表示截图区域矩形左下角的x轴坐标。 单位：px 取值范围：[0, 组件宽度]

**类型：** number

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedSnapshotRegion-end: number--><!--Device-LocalizedSnapshotRegion-end: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: number
```

布局方向为LTR时表示截图区域矩形左上角的x轴坐标，布局方向为RTL时表示截图区域矩形右上角的x轴坐标。 单位：px 取值范围：[0, 组件宽度]

**类型：** number

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedSnapshotRegion-start: number--><!--Device-LocalizedSnapshotRegion-start: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: number
```

布局方向为LTR时表示截图区域矩形左上角的y轴坐标，布局方向为RTL时表示截图区域矩形右上角的y轴坐标。 单位：px 取值范围：[0, 组件高度]

**类型：** number

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LocalizedSnapshotRegion-top: number--><!--Device-LocalizedSnapshotRegion-top: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

