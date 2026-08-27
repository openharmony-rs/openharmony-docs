# ArcAlphabetIndexerInterface

弧形索引条是一种弧形排列、可按字母顺序快速定位的组件，可与容器组件联动，按逻辑结构快速定位至容器显示区域，适用于手表等圆形屏幕设备。

> **说明：**

> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

## [[Call]]

```TypeScript
(info: ArcAlphabetIndexerInitInfo): ArcAlphabetIndexerAttribute
```

创建并初始化弧形索引条组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ArcAlphabetIndexerInitInfo](arkts-arkui-arkui-arcalphabetindexer-arcalphabetindexerinitinfo-i.md) | 是 | 定义弧形字母索引条的初始化参数，包含字母索引字符串数组和初始选中项索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcAlphabetIndexerAttribute](arkts-arkui-arkui-arcalphabetindexer-arcalphabetindexerattribute-c.md) |  |
