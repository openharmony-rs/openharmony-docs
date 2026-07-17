# SnapshotInfo

获取全量绘制结果入参。

**起始版本：** 12

<!--Device-webview-interface SnapshotInfo--><!--Device-webview-interface SnapshotInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id?: string
```

snapshot的id。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotInfo-id?: string--><!--Device-SnapshotInfo-id?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

web绘制的尺寸，最多支持16000px * 16000px，长度单位支持px、vp、%，需保持不同参数传入长度单位一致，默认单位vp，超过规格时返回最大规格。（示例：width:'100px'，height:'200px'。或者 width:'20%'，height:'30%'。只写数字时单位为vp。）

**类型：** SizeOptions

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SnapshotInfo-size?: SizeOptions--><!--Device-SnapshotInfo-size?: SizeOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

