# createFormBindingData

## Modules to Import

```TypeScript
```

## createFormBindingData

```TypeScript
function createFormBindingData(obj?: Object | string): FormBindingData
```

Creates a **FormBindingData** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createFormBindingData](arkts-form-formbindingdata-createformbindingdata-f.md)

**System capability:** SystemCapability.Ability.Form

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | Object &#124; string | No | Data to be displayed on the JS widget. The value can be an object containing multiple key-value pairs or a string in JSON format. The image data is identified by **'formImages'**, and the content is multiple key-value pairs, each of which consists of an image identifier and image file descriptor. The final format is {'formImages': {'key1': fd1, 'key2': fd2}}. |

**Return value:**

| Type | Description |
| --- | --- |
| FormBindingData | **FormBindingData** object created based on the passed data. |

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
