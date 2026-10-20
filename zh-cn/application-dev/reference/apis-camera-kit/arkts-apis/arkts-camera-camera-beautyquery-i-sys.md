# BeautyQuery（系统接口）

```TypeScript
interface BeautyQuery
```

提供获取和设置美颜效果的接口。

**起始版本：** 12

<!--Device-camera-interface BeautyQuery--><!--Device-camera-interface BeautyQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedBeautyRange

```TypeScript
getSupportedBeautyRange(type: BeautyType): Array<number>
```

获取某个美颜类型可设置的等级。不同设备支持的美颜等级不同，下表仅为示例。

| 输入参数 | 示例返回值 | 返回值描述 |  
| ----------------| ---- | ---------|  
| AUTO | [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] | **type** 为 **AUTO** 时支持的美颜等级。值 **0** 表示关闭美颜模式，其他正整数值表示对应的自动美颜等级。 |  
| SKIN_SMOOTH | [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10] | **type** 为 **SKIN_SMOOTH** 时支持的美颜等级。值 **0** 表示关闭磨皮功能，其他正整数值表示对应的磨皮等级。 |  
| FACE_SLENDER | [0, 1, 2, 3, 4, 5] | **type** 为 **FACE_SLENDER** 时支持的美颜等级。值 **0** 表示关闭瘦脸功能，其他正整数值表示对应的瘦脸等级。 |  
| SKIN_TONE | [-1, 16242611] | **type** 为 **SKIN_TONE** 时支持的美颜等级。值**-1**表示关闭肤色美化功能。其他非负值表示以RGB表示的肤色美化等级，<br>例如 16242611，其十六进制为 0xF7D7B3，其中 F7、D7、B3 分别表示 R 通道、G 通道、B 通道的值。 |

**起始版本：** 11

<!--Device-BeautyQuery-getSupportedBeautyRange(type: BeautyType): Array<int>--><!--Device-BeautyQuery-getSupportedBeautyRange(type: BeautyType): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [BeautyType](arkts-camera-camera-beautytype-e-sys.md) | 是 | 美颜类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 支持的等级数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
function getSupportedBeautyRange(portraitPhotoSession: camera.PortraitPhotoSession): Array<number> {
  let beautyTypes: Array<camera.BeautyType> = portraitPhotoSession.getSupportedBeautyTypes();
  if (beautyTypes === undefined || beautyTypes.length <= 0) {
    return [];
  }
  let beautyLevels: Array<number> = portraitPhotoSession.getSupportedBeautyRange(beautyTypes[0]);
  return beautyLevels;
}
```

<!--DelEnd-->

## getSupportedBeautyTypes

```TypeScript
getSupportedBeautyTypes(): Array<BeautyType>
```

获取支持的美颜类型。

**起始版本：** 11

<!--Device-BeautyQuery-getSupportedBeautyTypes(): Array<BeautyType>--><!--Device-BeautyQuery-getSupportedBeautyTypes(): Array<BeautyType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[BeautyType](arkts-camera-camera-beautytype-e-sys.md)&gt; | 支持的美颜类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

```TypeScript
function getSupportedBeautyTypes(portraitPhotoSession: camera.PortraitPhotoSession): Array<camera.BeautyType> {
  let beautyTypes: Array<camera.BeautyType> = portraitPhotoSession.getSupportedBeautyTypes();
  return beautyTypes;
}
```

<!--DelEnd-->

## getSupportedPortraitThemeTypes

```TypeScript
getSupportedPortraitThemeTypes(): Array<PortraitThemeType>
```

获取支持的人像主题类型。

**起始版本：** 14

<!--Device-BeautyQuery-getSupportedPortraitThemeTypes(): Array<PortraitThemeType>--><!--Device-BeautyQuery-getSupportedPortraitThemeTypes(): Array<PortraitThemeType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[PortraitThemeType](arkts-camera-camera-portraitthemetype-e-sys.md)&gt; | 人像主题类型列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## isPortraitThemeSupported

```TypeScript
isPortraitThemeSupported(): boolean
```

查询是否支持人像主题。

**起始版本：** 14

<!--Device-BeautyQuery-isPortraitThemeSupported(): boolean--><!--Device-BeautyQuery-isPortraitThemeSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持人像主题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
