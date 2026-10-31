# FormComponent (系统接口)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

提供卡片组件，实现卡片的显示功能。

>  **说明：**
>
> - 该组件从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件为卡片组件的使用方，对应提供方的使用参考文档[文件组织](../js-service-widget-ui/js-service-widget-file.md)。
>
> - 从API版本26.1.0开始：支持同一应用的不同进程使用相同卡片标识（id）挂载卡片，多个使用方共享同一卡片实例。
>
> - 该组件使用需要具有系统签名。
>
> - 本模块为系统接口。

## 权限

ohos.permission.REQUIRE_FORM, ohos.permission.GET_BUNDLE_INFO_PRIVILEGED


## 子组件

无


## 接口

## FormComponent

加载卡片内容和布局。

### (value: FormInfo)

FormComponent(value: FormInfo)

创建卡片组件，用于显示提供的卡片。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                        | 必填 | 参数描述                                                                |
| --------- | ------------------------------- | ---- | ----------------------------------------------------------------------- |
| value        | [FormInfo](#forminfo12)                 | 是   | 卡片信息。   |

## FormInfo<sup>12+</sup>

卡片信息。

> **说明：**
>
> - temporary参数标识卡片是否为临时卡片，临时卡片与常态卡片的对比详见[临时卡片和常态卡片](../../../form/widget-host-development-guide-sys.md#临时卡片和常态卡片)。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名    | 类型                        | 只读 | 可选 | 说明                                                                |
| --------- | ------------------------------- | ---- |---- |-------|
| id        | number \| string                    | 否   | 否   | 卡片标识（新建卡片填0）。<br/>**说明：**<br>不同使用方不可使用相同id。从API版本26.1.0开始：同一应用的不同进程可以使用相同id，多个使用方共享同一卡片实例。<br/>同一使用方使用相同id时，显示后添加的卡片。<br>id大于等于0小于2^32。                                        |
| name      | string                          |  否   | 否   | 卡片名称。                                                              |
| bundle    | string                          |  否   | 否   | 目标卡片包名。                                                          |
| ability   | string                          |  否   | 否   | 目标卡片Ability名称。                                                   |
| module    | string                          |  否   | 否   | 卡片模块名称。                                                          |
| dimension | [FormDimension](#formdimension) |  否   | 是   | 卡片尺寸，支持2 * 2，4 * 4，2 * 4等类型卡片。<br/>默认值：Dimension_2_2。 |
| temporary | boolean                         |  否   | 是   | 卡片是否为临时卡片，true表示是临时卡片，false表示不是临时卡片。<br/>默认值：false。 |
| renderingMode | [FormRenderingMode](#formrenderingmode11) |  否   | 是   | 卡片渲染模式。取值如下，默认值为 FULL_COLOR。<br>- FULL_COLOR：代表全色模式，卡片框架不会对卡片效果做出修改，保持和卡片开发者设置的效果不变。<br>- SINGLE_COLOR：代表单色模式，卡片框架会把卡片背景设为透明，开发者需按最佳实践设置卡片风格。<br>**说明：**<br/>如果系统不支持统一渲染模式，卡片框架在单色模式下也不会把卡片背景设为透明。 |
| want | [Want](../../../reference/apis-ability-kit/js-apis-app-ability-want.md#want) |  否   | 是   | 卡片传递信息的载体。 |
| shape  | [FormShape](#formshape12)      | 否    | 是    | 卡片的形状。 |
| exemptAppLock<sup>20+</sup> |boolean        |  否   | 是   | 卡片是否豁免应用锁，true表示卡片所属应用添加应用锁时，不受应用锁管控，不显示应用锁蒙层；false表示卡片所属应用添加应用锁时，受应用锁管控，正常展示应用锁蒙层。<br/>默认值：false。 |

## FormCallbackInfo<sup>12+</sup>

卡片查询或者卸载时获取formId的参数。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名    | 类型                        | 只读 | 可选 | 说明              |
| --------- | ------------------------------- | ---- | ---- | ----------------- |
| id        | number                 |   否   |  否   | 卡片标识。<br/>**说明：**<br>如果获取到的id为-1，说明id大于等于2^53，需要使用idString获取。                                        |
| idString      | string            |   否   |  否   | 卡片标识。                             |
| isLocked<sup>22+</sup>      | boolean             |   否   |   否   | 表示卡片是否被锁定，true表示卡片被锁定，false表示卡片没有被锁定。|

## FormSize<sup>18+</sup>

卡片大小信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名    | 类型                        | 只读 | 可选 | 说明    |
| --------- | ------------------------------- | ---- | ---- |---------|
| width        | number                 | 否   | 否   | 卡片宽的尺寸，单位：vp。<br/>**说明：**<br>width的取值范围大于0，小于2^53。如果不在范围内的数值卡片不显示。 |
| height      | number            | 否   | 否   | 卡片高的尺寸，单位：vp。<br/>**说明：**<br>height的取值范围大于0，小于2^53。如果不在范围内的数值卡片不显示。 |

## ErrorInformation<sup>18+</sup>

卡片错误信息。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名    | 类型                        | 只读 | 可选 | 说明                     |
| --------- | ------------------------------- | ---- | ---- | ------------------------------ |
| errcode        | number                 | 否  | 否   | [错误码](../../apis-form-kit/errorcode-form.md)。                                        |
| msg      | string            | 否       | 否   | 错误信息。                             |

## FormDimension

卡片尺寸枚举

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                       | 值     | 说明     |
| -------------------------- | -------- | -------- |
| Dimension_1_2              | 0 | 1*2 卡片 |
| Dimension_2_2              | 1 | 2*2 卡片 |
| Dimension_2_4              | 2 | 2*4 卡片 |
| Dimension_4_4              | 3 | 4*4 卡片 |
| Dimension_2_1<sup>(deprecated)</sup> | 4 | 2*1 卡片 <br>**说明:** 该字段从API version 9开始支持，从API version 20开始废弃。|
| Dimension_1_1<sup>11+</sup> | 6 | 1*1 卡片 |
| Dimension_6_4<sup>12+</sup> | 7 | 6*4 卡片 |
| Dimension_2_3<sup>18+</sup> | 8 | 2*3 卡片为穿戴设备使用 |
| Dimension_3_3<sup>18+</sup> | 9 | 3*3 卡片为穿戴设备使用 |

## FormRenderingMode<sup>11+</sup>

卡片渲染模式枚举

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                       | 值     | 说明     |
| -------------------------- | -------- | -------- |
| FULL_COLOR                 | 0 | 全色模式。|
| SINGLE_COLOR               | 1 | 单色模式。|

## FormColorMode<sup>23+</sup>

卡片色彩模式枚举。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称                       | 值     | 说明      |
| -------------------------- | -------- | -------- |
| MODE_AUTO                  | -1 | 跟随系统。|
| MODE_DARK                  | 0 | 深色模式。|
| MODE_LIGHT                 | 1 |浅色模式。|

## FormShape<sup>12+</sup>

定义卡片形状枚举。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                       | 值     | 说明      |
| -------------------------- | -------- | -------- |
| RECT                  | 1 | 方形卡片。|
| CIRCLE                  | 2 | 圆形卡片。|

## 属性

### size<sup>18+</sup>

size(formSize: FormSize)

设置高宽尺寸。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                      | 必填 | 说明       |
| ------ | --------------------------------------------------------- | ---- | ---------- |
| formSize  | [FormSize](#formsize18) | 是   | 宽高尺寸。 |

### moduleName

moduleName(value: string)

设置卡片模块名称。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| value  | string | 是   | 卡片模块名称。 |

### dimension

dimension(value: FormDimension)

设置卡片尺寸，支持2 * 2，4 * 4，2 * 4等类型卡片。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                            | 必填 | 说明                                 |
| ------ | ------------------------------- | ---- | ------------------------------------ |
| value  | [FormDimension](#formdimension) | 是   | 卡片尺寸。<br/>默认值：Dimension_2_2。 |

### allowUpdate

allowUpdate(value: boolean)

设置是否允许卡片更新。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                |
| ------ | ------- | ---- | ----------------------------------- |
| value  | boolean | 是   | 是否允许卡片更新，true表示允许卡片更新，false表示不允许卡片更新。<br/>默认值：true。 |

### visibility

visibility(value: Visibility)

设置是否允许卡片可见。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                          | 必填 | 说明                                   |
| ------ | --------------------------------------------- | ---- | -------------------------------------- |
| value  | [Visibility](ts-appendix-enums.md#visibility) | 是   | 是否允许卡片可见。<br/>默认值：Visible。 |

### colorMode<sup>23+</sup>

colorMode(value: FormColorMode)

设置卡片深浅色模式。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：** 

| 参数名 | 类型                                          | 必填 | 说明                                   |
| ------ | --------------------------------------------- | ---- | -------------------------------------- |
| value  | [FormColorMode](#formcolormode23) | 是   | 卡片深浅模式。 |

## 事件

### onAcquired

onAcquired(callback:&nbsp;Callback<[FormCallbackInfo](#formcallbackinfo12)>)&nbsp;

获取到卡片后触发的回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                | 必填 | 说明       |
| ------ | ----------------------------------- | ---- | ---------- |
| callback | Callback<[FormCallbackInfo](#formcallbackinfo12)> | 是   | 回调函数，获得FormCallbackInfo对象。 |

### onError

onError(callback: Callback\<ErrorInformation\>)

卡片加载错误触发的回调。 

> **说明：** 
> 
> 从API版本18开始，参数类型从`(info: { errcode: number; msg: string }) => void`变更为`Callback\<ErrorInformation\>`。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                            |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| callback   | Callback<[ErrorInformation](#errorinformation18)> | 是   | errcode:&nbsp;错误码。<br/>msg:&nbsp;错误信息。 |

### onRouter

onRouter(callback: Callback\<object\>)


卡片点击回调。

> **说明：** 
> 
> 从API版本18开始，参数类型从`(info: any) => void`变更为`Callback\<object\>`。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名  | 类型 | 必填 | 说明                                                         |
|------| - | ---- | ------------------------------------------------------------ |
| callback | Callback\<object\>  | 是   | 获得[事件绑定](../js-service-widget-ui/js-service-widget-syntax-hml.md#事件绑定)对象。 |

### onUninstall

onUninstall(callback:&nbsp;Callback<[FormCallbackInfo](#formcallbackinfo12)>)&nbsp;

卡片卸载回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名      | 类型                                | 必填 | 说明       |
|----------| ----------------------------------- | ---- | ---------- |
| callback | Callback<[FormCallbackInfo](#formcallbackinfo12)> | 是   | 回调函数，获得FormCallbackInfo对象。 |

### onLoad<sup>18+</sup>

onLoad(callback: VoidCallback)

卡片加载回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                | 必填 | 说明       |
|----------| ----------------------------------- | ---- | ---------- |
| callback | [VoidCallback](ts-types.md#voidcallback12) | 是   | 无返回值。 |

### onUpdate<sup>18+</sup>

onUpdate(callback:&nbsp;Callback<[FormCallbackInfo](#formcallbackinfo12)>)&nbsp;

卡片内容更新回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                | 必填 | 说明       |
|----------| ----------------------------------- | ---- | ---------- |
| callback | Callback<[FormCallbackInfo](#formcallbackinfo12)> | 是   | 回调函数，获得FormCallbackInfo对象。 |

## 示例

### 示例1（创建卡片并注册事件回调）

该示例创建一张2 * 2尺寸大小的卡片，并注册事件回调，在onAcquired回调中获取卡片标识。

```ts
// card.ets
@Entry
@Component
struct CardExample {
  @State formId: string = '0';
  build() {
    Column() {
      Text('this is a card')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      FormComponent({
        id: this.formId,
        name: "Form1",
        bundle: "com.example.cardexample",
        ability: "FormAbility",
        module: "entry",
        dimension: FormDimension.Dimension_2_2,
        temporary: false
      })
        .allowUpdate(true)
        .size({width:360,height:360})
        .visibility(Visibility.Visible)
        .onAcquired((form: FormCallbackInfo)=>{
          console.info(`form info : ${form?.id}`);
          // Invalid form id
          if (form.id == -1) {
            this.formId = form.idString;
          } else {
            this.formId = form.id.toString();
          }
        })
        .onError((error)=>{
          console.error(`fail to add form, error code: ${error?.errcode}, error message: ${error?.msg}`);
        })
        .onUninstall((form: FormCallbackInfo)=>{
          console.info(`uninstall form success : ${form?.id}`);
          // Invalid form id
          if (form.id == -1) {
            this.formId = form.idString;
          } else {
            this.formId = form.id.toString();
          }
        })
        .onUpdate((form: FormCallbackInfo)=>{
          console.info(`form update done : ${form?.id}`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![Form](figures/form.png)

### 示例2（同一应用的不同进程使用相同卡片标识挂载卡片）

从API版本26.1.0开始：同一应用的不同进程可以使用相同卡片标识（id）挂载卡片，多个使用方共享同一卡片实例。该示例中，formId为同一应用其他进程已获取的卡片标识。

```ts
// card.ets
@Entry
@Component
struct CardExample2 {
  // 已存在的卡片标识（示例值），实际开发中由同一应用的其他进程获取后传递
  @State formId: string = '1747282432568508160';
  build() {
    Column() {
      FormComponent({
        id: this.formId,
        name: "Form1",
        bundle: "com.example.cardexample",
        ability: "FormAbility",
        module: "entry",
        dimension: FormDimension.Dimension_2_2,
        temporary: false
      })
        .allowUpdate(true)
        .size({width:360,height:360})
        .onAcquired((form: FormCallbackInfo)=>{
          console.info(`form info : ${form?.id}`);
          if (form.id == -1) {
            this.formId = form.idString;
          } else {
            this.formId = form.id.toString();
          }
        })
        .onError((error)=>{
          console.error(`fail to add form, error code: ${error?.errcode}, error message: ${error?.msg}`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![Form](figures/form.png)