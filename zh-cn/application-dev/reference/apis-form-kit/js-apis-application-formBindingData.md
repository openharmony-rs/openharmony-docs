# @ohos.application.formBindingData (卡片数据绑定类)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
卡片数据绑定模块提供卡片数据绑定的能力，包括FormBindingData对象的创建、相关信息的描述。该模块常用于小体量卡片、数据分享式卡片等场景，解决了卡片数据与UI耦合导致更新维护困难的问题，实现了数据驱动UI的动态更新，降低了开发维护成本。在卡片提供方需要动态更新卡片显示数据的时候，可通过数据包语法将卡片数据传递给卡片框架进行渲染。

> **说明：**
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
从API version 8开始支持，从API version 9开始废弃。建议使用[formBindingData](js-apis-app-form-formBindingData.md)替代。
## 导入模块

```ts
import { formBindingData } from '@kit.FormKit';
```

## FormBindingData

FormBindingData提供卡片数据绑定的能力，用于存储卡片需要展示的数据。

**系统能力：** SystemCapability.Ability.Form

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- |-------- | -------- | -------- |
| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| data | Object | 否 |否 | JS卡片要展示的数据。包含若干键值对的Object。|


## formBindingData.createFormBindingData

createFormBindingData(obj?: Object | string): FormBindingData
创建一个FormBindingData对象。

**错误码：**
创建一个FormBindingData对象。
| 错误码ID | 错误信息 | 说明 |
| --- | --- | --- |
| 401 | Parameter error | 参数错误，请检查参数类型和范围 |
创建一个FormBindingData对象。

**错误码：**

| 错误码ID | 错误信息 | 说明 |
| --- | --- | --- |
| 401 | Parameter error | 参数错误，请检查参数类型和范围 |



**系统能力：** SystemCapability.Ability.Form

**参数：**
**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 参数名 | 类型           | 必填 | 说明                                                         |
| ------ | -------------- | ---- | ------------------------------------------------------------ |
| obj    | Object \| string | 否   | JS卡片要展示的数据，用于绑定卡片需要显示的信息。取值原则：可以是包含若干键值对的Object或者JSON格式的字符串。Object可包含自定义键值对用于数据绑定，图片数据需使用'formImages'作为键名，其值为图片标识与图片文件描述符的键值对，文件描述符通过fileIo.openSync等方法获取。JSON字符串需符合标准JSON格式。示例：{'name': '温度', 'formImages': {'image1': fd1}}。不传时创建空的FormBindingData对象。 |


**返回值：**

| 类型                                | 说明                                    |
| ----------------------------------- | --------------------------------------- |
| [FormBindingData](#formbindingdata) | 根据传入数据创建的FormBindingData对象。 |
**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |


**示例：**

```ts
import { formBindingData } from '@kit.FormKit';
import { fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  pathDir: string = this.content.filesDir;

  createFormBindingData() {
    let filePath = this.pathDir + "/form.png";
    let fd: number = -1;
    try {
// 构建卡片绑定数据参数：包含温度数据和图片文件描述符，通过formImages传递图片数据
let filePath = this.pathDir + "/form.png";
let file = fileIo.openSync(filePath);
let formImagesParam: Record<string, number> = {
  'image': file.fd
};
## 错误码
let createFormBindingDataParam: Record<string, string | Record<string, number>> = {
| 错误码ID | 错误信息 |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
  'name': '21°',
以上错误码由createFormBindingData接口返回。
  'imgSrc': 'image',
  'formImages': formImagesParam
};
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
## 错误码

| 错误码ID | 错误信息 |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

以上错误码由createFormBindingData接口返回。
        this.createFormBindingData();
      })
  }
}
```
