# isC2PASignatureSupported

## 导入模块

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
```

## isC2PASignatureSupported

```TypeScript
function isC2PASignatureSupported(): boolean
```

检查是否支持C2PA签名。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-cameraPicker-function isC2PASignatureSupported(): boolean--><!--Device-cameraPicker-function isC2PASignatureSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | C2PA签名是否支持的检查结果。**true**表示支持，**false**表示不支持。如果接口调用失败，返回undefined。 |
