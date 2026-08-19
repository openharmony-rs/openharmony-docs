# createFormBindingData

## 导入模块

```TypeScript
```

## createFormBindingData

```TypeScript
function createFormBindingData(obj?: Object | string): FormBindingData
```

创建一个FormBindingData对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [createFormBindingData](arkts-form-formbindingdata-createformbindingdata-f.md)

<!--Device-formBindingData-function createFormBindingData(obj?: Object | string): FormBindingData--><!--Device-formBindingData-function createFormBindingData(obj?: Object | string): FormBindingData-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object \| string | 否 | JS卡片要展示的数据。可以是包含若干键值对的Object或者 json 格式的字符串。其中图片数据以'formImages'作为标识，内容为图片标识与图片文件描 述符的键值对{'formImages': {'key1': fd1, 'key2': fd2}}。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FormBindingData | 根据传入数据创建的FormBindingData对象。 |

**示例**

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

