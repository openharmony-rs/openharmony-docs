# isFrameType4Supported

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## isFrameType4Supported

```TypeScript
function isFrameType4Supported(): boolean
```

查询当前设备是否支持帧类型4。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-manager-function isFrameType4Supported(): boolean--><!--Device-manager-function isFrameType4Supported(): boolean-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持帧类型4。返回**true**表示设备支持帧类型4，返回**false**表示不支持。 |
