# createFormBindingData

## Modules to Import

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## createFormBindingData

```TypeScript
function createFormBindingData(obj?: Object | string): FormBindingData
```

Creates a **FormBindingData** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | Object &#124; string | No | Data to be displayed on the widget. The value can be an object containing multiple key-value pairs or a JSON string. The image data is identified by **'formImages'**, and the content is multiple key- value pairs, each of which consists of an image identifier and image file descriptor. The final format is {'formImages': {'key1': fd1, 'key2': fd2}}.<br>**NOTE:** <br>During [widget update](../../../form/arkts-ui-widget-interaction-overview.md), when the widget UI receives widget data through @LocalStorageProp, the **FormBindingData** object is serialized, that is, the widget data is converted into the string type. Since API version 20, if the widget data is updated using shared memory, the total size of the updated data cannot exceed 10 MB, and the number of updated images cannot exceed 20. In API version 19 and earlier versions, the maximum number of image files is 5, and the maximum memory size of each image is 2 MB. Exceeding this 2 MB limit for any image will result in abnormal display. |

**Return value:**

| Type | Description |
| --- | --- |
| [FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | **FormBindingData** object created based on the passed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
import { formBindingData } from '@kit.FormKit';
import { fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  content = this.getUIContext().getHostContext() as common.UIAbilityContext;
  pathDir: string = this.content.filesDir;

  createFormBindingData() {
    let filePath = this.pathDir + "/form.png";
    let fd: number = -1;
    try {
      fd = fileIo.openSync(filePath, fileIo.OpenMode.READ_ONLY).fd;
      let formImagesParam: Record<string, number> = {
        'image': fd
      };
      let createFormBindingDataParam: Record<string, string | Record<string, number>> = {
        'name': '21°',
        'imgSrc': 'image',
        'formImages': formImagesParam
      };
      let formBindingDataObj = formBindingData.createFormBindingData(createFormBindingDataParam);
    } catch (error) {
      console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
    } finally {
      if (fd !== -1) {
        fileIo.closeSync(fd);
      }
    }
  }

  build() {
    Button('createFormBindingData')
      .onClick((event: ClickEvent) => {
        this.createFormBindingData();
      })
  }
}
```
