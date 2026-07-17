# GainmapParams（系统接口）

Gainmap（增益图）参数设置选项。

**起始版本：** 26.0.0

<!--Device-image-interface GainmapParams--><!--Device-image-interface GainmapParams-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## isFullSizeGainmap

```TypeScript
isFullSizeGainmap: boolean
```

返回Picture中的Gainmap（增益图）是否使用全尺寸图。

true表示使用全尺寸图，宽高和主图一致；false表示不使用全尺寸图，宽高均为主图的一半。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GainmapParams-isFullSizeGainmap: boolean--><!--Device-GainmapParams-isFullSizeGainmap: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

