# ColorManagementQuery

色彩管理类，用于查询色彩空间参数。

**起始版本：** 23

<!--Device-camera-interface ColorManagementQuery--><!--Device-camera-interface ColorManagementQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getSupportedColorSpaces

```TypeScript
getSupportedColorSpaces(): Array<colorSpaceManager.ColorSpace>
```

获取支持的色彩空间列表。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ColorManagementQuery-getSupportedColorSpaces(): Array<colorSpaceManager.ColorSpace>--><!--Device-ColorManagementQuery-getSupportedColorSpaces(): Array<colorSpaceManager.ColorSpace>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;colorSpaceManager.ColorSpace&gt; | 支持的色彩空间列表。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage.<br>**适用版本：** 12 - 17 |

