# ApertureQuery（系统接口）

物理光圈查询对象。

**起始版本：** 23

<!--Device-camera-interface ApertureQuery--><!--Device-camera-interface ApertureQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getSupportedPhysicalApertures

```TypeScript
getSupportedPhysicalApertures(): Array<PhysicalAperture>
```

获取支持的物理光圈。

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ApertureQuery-getSupportedPhysicalApertures(): Array<PhysicalAperture>--><!--Device-ApertureQuery-getSupportedPhysicalApertures(): Array<PhysicalAperture>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[PhysicalAperture](arkts-camera-camera-physicalaperture-i-sys.md)&gt; | 支持的物理光圈数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 23 |

## getSupportedVirtualApertures

```TypeScript
getSupportedVirtualApertures(): Array<double>
```

获取支持的虚拟光圈列表。

**起始版本：** 23

<!--Device-ApertureQuery-getSupportedVirtualApertures(): Array<double>--><!--Device-ApertureQuery-getSupportedVirtualApertures(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | 支持的虚拟光圈列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function getSupportedVirtualApertures(session: camera.PortraitPhotoSession): Array<number> {
  let virtualApertures: Array<number> = session.getSupportedVirtualApertures();
  return virtualApertures;
}
```

