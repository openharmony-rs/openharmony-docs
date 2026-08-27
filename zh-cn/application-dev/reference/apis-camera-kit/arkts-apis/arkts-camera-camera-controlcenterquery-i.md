# ControlCenterQuery

控制中心类，用于查询是否支持相机控制器。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getSupportedEffectTypes

```TypeScript
getSupportedEffectTypes(): Array<ControlCenterEffectType>
```

查询相机控制器支持的效果类型。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ControlCenterEffectType](arkts-camera-camera-controlcentereffecttype-e.md)&gt; | 支持的效果类型。 |

**示例**

```TypeScript
function getSupportedEffectTypes(videoSession: camera.VideoSession): Array<camera.ControlCenterEffectType> {
    let effectTypes: Array<camera.ControlCenterEffectType> = [];
    effectTypes = videoSession.getSupportedEffectTypes();
    return effectTypes;
}
```

## isControlCenterSupported

```TypeScript
isControlCenterSupported(): boolean
```

查询是否支持相机控制器。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持相机控制器。true表示支持，false表示不支持。 |

**示例**

```TypeScript
function isControlCenterSupported(videoSession: camera.VideoSession): boolean {
    let isSupported: boolean = videoSession.isControlCenterSupported();
    return isSupported;
}
```
