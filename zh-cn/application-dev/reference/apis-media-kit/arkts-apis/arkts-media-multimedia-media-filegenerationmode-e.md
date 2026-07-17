# FileGenerationMode

表示创建媒体文件模式的枚举。

**起始版本：** 12

<!--Device-unnamed-enum FileGenerationMode--><!--Device-unnamed-enum FileGenerationMode-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## APP_CREATE

```TypeScript
APP_CREATE = 0
```

由应用自行在沙箱创建媒体文件。

**起始版本：** 12

<!--Device-FileGenerationMode-APP_CREATE = 0--><!--Device-FileGenerationMode-APP_CREATE = 0-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## AUTO_CREATE_CAMERA_SCENE

```TypeScript
AUTO_CREATE_CAMERA_SCENE = 1
```

由系统创建媒体文件，当前仅在相机录制场景下生效，会忽略应用设置的url。

**起始版本：** 12

<!--Device-FileGenerationMode-AUTO_CREATE_CAMERA_SCENE = 1--><!--Device-FileGenerationMode-AUTO_CREATE_CAMERA_SCENE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

