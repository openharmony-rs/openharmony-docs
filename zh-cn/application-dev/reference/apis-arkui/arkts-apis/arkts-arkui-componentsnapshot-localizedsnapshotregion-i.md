# LocalizedSnapshotRegion

定义组件截图的矩形区域，start和end的值在布局方向为LTR时指定为left和right，在布局方向为RTL时指定为right和left。 > **说明：** > > 直接使用componentSnapshot可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取 > [UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)实例，并使用[getComponentSnapshot](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md#getcomponentsnapshot) > 获取绑定实例的componentSnapshot。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-componentSnapshot-export interface LocalizedSnapshotRegion--><!--Device-componentSnapshot-export interface LocalizedSnapshotRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom: double
```

截图区域矩形右下角的y轴坐标。 单位：px 取值范围：[0, 组件高度]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalizedSnapshotRegion-bottom: double--><!--Device-LocalizedSnapshotRegion-bottom: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end: double
```

布局方向为LTR时表示截图区域矩形右下角的x轴坐标，布局方向为RTL时表示截图区域矩形左下角的x轴坐标。 单位：px 取值范围：[0, 组件宽度]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalizedSnapshotRegion-end: double--><!--Device-LocalizedSnapshotRegion-end: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: double
```

布局方向为LTR时表示截图区域矩形左上角的x轴坐标，布局方向为RTL时表示截图区域矩形右上角的x轴坐标。 单位：px 取值范围：[0, 组件宽度]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalizedSnapshotRegion-start: double--><!--Device-LocalizedSnapshotRegion-start: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: double
```

布局方向为LTR时表示截图区域矩形左上角的y轴坐标，布局方向为RTL时表示截图区域矩形右上角的y轴坐标。 单位：px 取值范围：[0, 组件高度]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalizedSnapshotRegion-top: double--><!--Device-LocalizedSnapshotRegion-top: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

