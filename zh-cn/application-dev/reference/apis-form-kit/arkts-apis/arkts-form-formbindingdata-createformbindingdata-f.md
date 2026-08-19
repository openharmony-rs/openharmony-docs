# createFormBindingData

## 导入模块

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## createFormBindingData

```TypeScript
function createFormBindingData(obj?: Object | string): FormBindingData
```

创建一个FormBindingData对象。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-formBindingData-function createFormBindingData(obj?: Object | string): FormBindingData--><!--Device-formBindingData-function createFormBindingData(obj?: Object | string): FormBindingData-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object \| string | 否 | 卡片要展示的数据，用于绑定卡片UI显示的内容。当需要向卡片传递数据时传入此参数，可以是包含若干键值对的Object或者JSON格式的字符串。不传入时创建一个空的 FormBindingData对象，卡片将显示默认内容。其中图片数据以'formImages'作为标识，内容为图片标识与图片文件描述符的键值对 `{'formImages': {'key1': fd1, 'key2': fd2}}`。 <br>**说明：** 在[卡片刷新](../../../form/arkts-ui-widget-interaction-overview.md)过程中，卡片UI通过 [@LocalStorageProp](../../../ui/state-management/arkts-localstorage.md#localstorageprop)接收卡片数据时， FormBindingData对象会序列化，即卡片数据会转换成string类型。从API version 20开始，如果卡片刷新的数据通过共享内存更新，刷新数据总大小不超过10MB，刷新图片数量不超过20张，API version 19及之前的版本，图片文件数量上限为5张，每张限制内存2MB，超出限制的图片会显示异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FormBindingData | 根据传入数据创建的FormBindingData对象，用于卡片数据绑定，向卡片提供要展示的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
'use static'

import { formBindingData } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

let file = fileIo.openSync('/path/to/form.png');
try {
  let formImagesParam: Record<string, number> = {
    'image': file.fd
  };
  let createFormBindingDataParam: Record<string, string | Object> = {
    'name': '21°',
    'imgSrc': 'image',
    'formImages': formImagesParam
  };

  formBindingData.createFormBindingData(createFormBindingDataParam);
} catch (e) {
  let code = e.code;
  let message = e.message;
  console.error(`catch error, code: ${code}, message: ${message}`);
} finally {
  fileIo.closeSync(file.fd);
}
```


## createFormBindingData

```TypeScript
function createFormBindingData(obj?: RecordData): FormBindingData
```

Create an FormBindingData instance.

**起始版本：** 23

<!--Device-formBindingData-function createFormBindingData(obj?: RecordData): FormBindingData--><!--Device-formBindingData-function createFormBindingData(obj?: RecordData): FormBindingData-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md) | 否 | Indicates the FormBindingData instance data. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FormBindingData | Returns the FormBindingData. |

