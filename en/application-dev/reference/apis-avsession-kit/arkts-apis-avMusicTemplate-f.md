# Functions

<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module applies only to cars running API version 23 or later.

## Modules to Import

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## avMusicTemplate.createAVMusicTemplate

createAVMusicTemplate(accessType: AVMusicTemplateType): AVMusicTemplate

Creates an audio template and returns the audio template instance.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters**

| Name    | Type                                                        | Mandatory| Description              |
| ---------- | ------------------------------------------------------------ | ---- | ------------------ |
| accessType | [AVMusicTemplateType](arkts-apis-avMusicTemplate-e.md#avmusictemplatetype) | Yes  | Audio template type.|

**Return value**

| Type                                                      | Description                            |
| ---------------------------------------------------------- | -------------------------------- |
| [AVMusicTemplate](arkts-apis-avMusicTemplate-AVMusicTemplate.md) | Audio template object, which can be used to obtain the session ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Template Error Codes](errorcode-avmusictemplate.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.function createAVMusicTemplate can not work correctly due to limited device capabilities. |
| 35000001 | Failed to create the AVMusicTemplate.                        |

**Example**

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';

export class TemplateManager {
  private template: avMusicTemplate.AVMusicTemplate | undefined = undefined;
  private static instance: TemplateManager;

  private constructor() {
  }

  /**
   * Obtain a TemplateManager instance.
   *
   * @returns TemplateManager instance.
   */
  public static getInstance(): TemplateManager {
    if (!TemplateManager.instance) {
      TemplateManager.instance = new TemplateManager();
    }
    return TemplateManager.instance;
  };

  /**
   * Create an audio template.
   */
  public createTemplate() {
    if (this.template) {
      console.warn('createTemplate: template already exists');
      return;
    }
    try {
      this.template = avMusicTemplate.createAVMusicTemplate(avMusicTemplate.AVMusicTemplateType.DEFAULT);
      console.info('Succeeded in creating template.');
    } catch (e) {
      console.error(`createTemplate, errCode: ${e?.code}`);
    }
  }
}
```
