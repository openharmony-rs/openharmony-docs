# ArcListInterface

弧形列表由沿弧形排列的一系列列表项组成，适用于圆形屏幕设备。适合连续、多行呈现同类数据，例如图片和文本。 > **说明：** > > - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

**起始版本：** 18

<!--Device-unnamed-export interface ArcListInterface--><!--Device-unnamed-export interface ArcListInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## constructor

```TypeScript
(options?: ArkListOptions): ArcListAttribute
```

创建弧形列表实例，传入弧形列表配置项参数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcListInterface-(options?: ArkListOptions): ArcListAttribute--><!--Device-ArcListInterface-(options?: ArkListOptions): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArkListOptions](arkts-arkui-arkui-arclist-arklistoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |

