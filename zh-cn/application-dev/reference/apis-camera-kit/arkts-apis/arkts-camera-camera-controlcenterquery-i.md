# ControlCenterQuery

控制中心类，用于查询是否支持相机控制器。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-camera-interface ControlCenterQuery--><!--Device-camera-interface ControlCenterQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getSupportedEffectTypes

```TypeScript
getSupportedEffectTypes(): Array<ControlCenterEffectType>
```

查询相机控制器支持的效果类型。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ControlCenterQuery-getSupportedEffectTypes(): Array<ControlCenterEffectType>--><!--Device-ControlCenterQuery-getSupportedEffectTypes(): Array<ControlCenterEffectType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ControlCenterEffectType&gt; | 支持的效果类型。 |

## isControlCenterSupported

```TypeScript
isControlCenterSupported(): boolean
```

查询是否支持相机控制器。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ControlCenterQuery-isControlCenterSupported(): boolean--><!--Device-ControlCenterQuery-isControlCenterSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持相机控制器。true表示支持，false表示不支持。 |

