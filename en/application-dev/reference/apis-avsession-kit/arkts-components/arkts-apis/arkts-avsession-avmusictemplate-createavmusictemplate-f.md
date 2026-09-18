# createAVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## createAVMusicTemplate

```TypeScript
function createAVMusicTemplate(accessType: AVMusicTemplateType): AVMusicTemplate
```

Create an AVMusicTemplate instance.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accessType | [AVMusicTemplateType](arkts-avsession-avmusictemplate-avmusictemplatetype-e.md) | Yes | type of access, default is 'smartCar' |

**Return value:**

| Type | Description |
| --- | --- |
| [AVMusicTemplate](arkts-avsession-avmusictemplate-avmusictemplate-c.md) | an AVMusicTemplate instance |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.function createAVMusicTemplate can not work correctly due to limited device capabilities. |
| [35000001](../errorcode-avmusictemplate.md#35000001-audio-template-creation-failure) | Failed to create the AVMusicTemplate. |
