# FormBindingData

```TypeScript
interface FormBindingData
```

FormBindingData对象的属性定义。

**起始版本：** 9

<!--Device-formBindingData-interface FormBindingData--><!--Device-formBindingData-interface FormBindingData-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## data

```TypeScript
data: Object
```

卡片要展示的数据。可以是包含若干键值对的Object或者JSON格式的字符串。

**类型：** Object

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-FormBindingData-data: Object--><!--Device-FormBindingData-data: Object-End-->

**系统能力：** SystemCapability.Ability.Form

## isSupportMoreImages

```TypeScript
isSupportMoreImages?: boolean
```

是否支持更多图片数据，在卡片数据使用共享内存时，当设置值为false时，最多支持正常显示的图片是20张，当设置为true时，最多支持正常显示的图片是30张。更多图片有数据总量超过10M的风险，导致卡片数据更新失败。默认值：false。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-FormBindingData-isSupportMoreImages?: boolean--><!--Device-FormBindingData-isSupportMoreImages?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

## proxies

```TypeScript
proxies?: Array<ProxyData>
```

卡片代理刷新的订阅信息，配置后会订阅代理刷新消息。默认为空数组，表示不订阅代理刷新消息。当需要使用卡片代理刷新功能时传入此参数，不传入时默认为空数组（不使用代理刷新）。

**类型：** Array&lt;[ProxyData](arkts-form-formbindingdata-proxydata-i.md)&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-FormBindingData-proxies?: Array<ProxyData>--><!--Device-FormBindingData-proxies?: Array<ProxyData>-End-->

**系统能力：** SystemCapability.Ability.Form
