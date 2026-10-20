# ManualIsoQuery

```TypeScript
interface ManualIsoQuery
```

提供了查询相机设备是否支持手动ISO设置以及获取设备支持的ISO范围的方法。

**起始版本：** 24

<!--Device-camera-interface ManualIsoQuery--><!--Device-camera-interface ManualIsoQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedIsoRange

```TypeScript
getSupportedIsoRange(): number[]
```

获取支持的标准ISO感光度值数组，标准定义参考ISO 12232:2006。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualIsoQuery-getSupportedIsoRange(): int[]--><!--Device-ManualIsoQuery-getSupportedIsoRange(): int[]-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | ISO感光度值数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
