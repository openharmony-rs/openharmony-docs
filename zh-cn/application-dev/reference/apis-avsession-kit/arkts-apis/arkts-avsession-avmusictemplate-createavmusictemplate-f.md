# createAVMusicTemplate

## createAVMusicTemplate

```TypeScript
function createAVMusicTemplate(accessType: AVMusicTemplateType): AVMusicTemplate
```

创建音频模板，返回音频模板实例。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-function createAVMusicTemplate(accessType: AVMusicTemplateType): AVMusicTemplate--><!--Device-avMusicTemplate-function createAVMusicTemplate(accessType: AVMusicTemplateType): AVMusicTemplate-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accessType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 音频模板类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 音频模板对象，可用于获取会话ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function createAVMusicTemplate can not work correctly due to limited device capabilities. |
| [35000001](../errorcode-avmusictemplate.md#35000001-音频模板创建失败) | Failed to create the AVMusicTemplate. |

