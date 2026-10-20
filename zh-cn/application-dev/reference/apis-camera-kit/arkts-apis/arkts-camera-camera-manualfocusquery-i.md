# ManualFocusQuery

```TypeScript
interface ManualFocusQuery
```

手动对焦查询对象。

**起始版本：** 24

<!--Device-camera-interface ManualFocusQuery--><!--Device-camera-interface ManualFocusQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isFocusDistanceSupported

```TypeScript
isFocusDistanceSupported(): boolean
```

检测是否支持对焦距离设置。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualFocusQuery-isFocusDistanceSupported(): boolean--><!--Device-ManualFocusQuery-isFocusDistanceSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持对焦距离。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
