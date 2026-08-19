# Aperture（系统接口）

物理光圈对象。 Aperture继承自ApertureQuery。

**继承/实现关系：** Aperture extends [ApertureQuery](arkts-camera-camera-aperturequery-i-sys.md)

**起始版本：** 23

<!--Device-camera-interface Aperture--><!--Device-camera-interface Aperture-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getPhysicalAperture

```TypeScript
getPhysicalAperture(): double
```

获取当前物理光圈值。

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Aperture-getPhysicalAperture(): double--><!--Device-Aperture-getPhysicalAperture(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 当前物理光圈值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 23 |

## getVirtualAperture

```TypeScript
getVirtualAperture(): double
```

获取当前设置的虚拟光圈值。

**起始版本：** 23

<!--Device-Aperture-getVirtualAperture(): double--><!--Device-Aperture-getVirtualAperture(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 当前设置的虚拟光圈值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function getVirtualAperture(session: camera.PortraitPhotoSession): number {
  let virtualAperture: number = session.getVirtualAperture();
  return virtualAperture;
}
```

## setPhysicalAperture

```TypeScript
setPhysicalAperture(aperture: double): void
```

设置物理光圈值。需要先通过getSupportedPhysicalApertures接口获取不同焦段支持的可设置光圈值，再通过调整焦段范围，设置支持的物理光圈值。

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Aperture-setPhysicalAperture(aperture: double): void--><!--Device-Aperture-setPhysicalAperture(aperture: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aperture | double | 是 | 物理光圈值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 23 |

## setVirtualAperture

```TypeScript
setVirtualAperture(aperture: double): void
```

设置虚拟光圈。可以先通过getSupportedVirtualApertures获取当前设备所支持的虚拟光圈列表。

**起始版本：** 23

<!--Device-Aperture-setVirtualAperture(aperture: double): void--><!--Device-Aperture-setVirtualAperture(aperture: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aperture | double | 是 | 虚拟光圈值，通过getSupportedVirtualApertures接口获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function setVirtualAperture(session: camera.PortraitPhotoSession, virtualAperture: number): void {
  session.setVirtualAperture(virtualAperture);
}
```

