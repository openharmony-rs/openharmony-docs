# AVRecorderConfig

音视频录制的参数。 audioSourceType和videoSourceType参数用于区分纯音频录制、纯视频录制和音视频录制。纯音频录制仅设置audioSourceType。纯视频录制仅设置videoSourceType。音视频录制需同时设置audioSourceType和videoSourceType。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-interface AVRecorderConfig--><!--Device-unnamed-interface AVRecorderConfig-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## metaSourceTypes

```TypeScript
metaSourceTypes?: Array<MetaSourceType>
```

元数据源类型，详见MetaSourceType。

**类型：** Array&lt;MetaSourceType&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-AVRecorderConfig-metaSourceTypes?: Array<MetaSourceType>--><!--Device-AVRecorderConfig-metaSourceTypes?: Array<MetaSourceType>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**系统接口：** 此接口为系统接口。

