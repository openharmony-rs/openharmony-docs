# createFormBindingDataEx

## 导入模块

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## createFormBindingDataEx

```TypeScript
function createFormBindingDataEx(obj?: Object | string): FormBindingData
```

创建一个FormBindingData对象

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-formBindingData-function createFormBindingDataEx(obj?: Object | string): FormBindingData--><!--Device-formBindingData-function createFormBindingDataEx(obj?: Object | string): FormBindingData-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object &#124; string | 否 | 卡片要展示的数据。可以是包含若干键值对的Object或者JSON格式的字符串。其中图片数据以'formImages'作为标识，内容为图片标识与图片文件描述符的键值对{'formImages': {'key1': fd1, 'key2': fd2}}。<br>**说明：** 在[卡片刷新](../../../form/arkts-ui-widget-interaction-overview.md)过程中，卡片UI通过@LocalStorageProp接收卡片数据时，FormBindingData对象会序列化，即卡片数据会转换成string类型。如果卡片刷新的数据通过共享内存更新，刷新数据总大小不超过10MB，刷新图片数量不超过30张，超出限制的图片会显示异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | 基于传入的参数数据创建FormBindingData对象 |
