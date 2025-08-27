# @ohos.app.form.formBindingData (卡片数据绑定类)

<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
卡片数据绑定模块提供卡片数据绑定的能力。包括FormBindingData对象的创建、相关信息的描述。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { formBindingData } from '@kit.FormKit';
```


## ProxyData<sup>10+</sup>

卡片代理刷新订阅数据信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key<sup>10+</sup> | string | 是 | 卡片代理刷新的订阅标识，与数据发布者保持一致。|
| subscriberId<sup>10+</sup> | string | 否 | 卡片代理刷新的订阅条件，默认值为当前卡片的formId。|


## FormBindingData

FormBindingData相关描述。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| data | Object | 是 | 卡片要展示的数据。可以是包含若干键值对的Object或者 json 格式的字符串。|
| proxies<sup>10+</sup> | Array<[ProxyData](#proxydata10)> | 否 | 卡片代理刷新的订阅信息，默认为空数组。<br>**模型约束：** 此接口仅可在Stage模型下使用。<br>|

## formBindingData.createFormBindingData

createFormBindingData(obj?: Object | string): FormBindingData

创建一个FormBindingData对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型           | 必填 | 说明                                                         |
| ------ | -------------- | ---- | ------------------------------------------------------------ |
| obj    | Object\|string | 否   | 卡片要展示的数据。可以是包含若干键值对的Object或者 json 格式的字符串。其中图片数据以'formImages'作为标识，内容为图片标识与图片文件描述符的键值对{'formImages': {'key1': fd1, 'key2': fd2}}。<br>**说明：** 在[卡片刷新](../../form/arkts-ui-widget-interaction-overview.md)过程中，卡片UI通过@LocalStorageProp接收卡片数据时，FormBindingData对象会序列化，即卡片数据会转换成string类型。|


**返回值：**

| 类型                                | 说明                                    |
| ----------------------------------- | --------------------------------------- |
| [FormBindingData](#formbindingdata) | 根据传入数据创建的FormBindingData对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


**示例：**

```ts
import { formBindingData } from '@kit.FormKit';
import { fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';
@Entry
@Component
struct Index {
  content = this.getUIContext().getHostContext() as common.UIAbilityContext;
  pathDir: string = this.content.filesDir;
  createFormBindingData() {
    try {
      let filePath = this.pathDir + "/form.png";
      let file = fileIo.openSync(filePath);
      let formImagesParam: Record<string, number> = {
        'image': file.fd
      };
      let createFormBindingDataParam: Record<string, string | Record<string, number>> = {
        'name': '21°',
        'imgSrc': 'image',
        'formImages': formImagesParam
      };
      formBindingData.createFormBindingData(createFormBindingDataParam);
    } catch (error) {
      console.error(`catch error, error: ${JSON.stringify(error)}`);
    }
  }
  build() {
    Button('createFormBindingData')
      .onClick((event: ClickEvent)=>{
        this.createFormBindingData();
      })
  }
}
```
