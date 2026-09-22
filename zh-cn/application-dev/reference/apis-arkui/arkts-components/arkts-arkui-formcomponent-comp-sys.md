# FormComponent(系统接口) (System API)

Defines FormComponent Component.

## FormComponent

```TypeScript
FormComponent(value: FormInfo)
```

Set a new value of form info.

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FormInfo](arkts-arkui-formcomponent-comp-forminfo-i-sys.md) | 是 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorInformation](arkts-arkui-formcomponent-comp-errorinformation-i-sys.md) | 卡片错误信息。 |
| [FormCallbackInfo](arkts-arkui-formcomponent-comp-formcallbackinfo-i-sys.md) | 卡片查询或者卸载时获取formId的参数。 |
| [FormInfo](arkts-arkui-formcomponent-comp-forminfo-i-sys.md) | 卡片信息。 |
| [FormSize](arkts-arkui-formcomponent-comp-formsize-i-sys.md) | 卡片大小信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FormColorMode](arkts-arkui-formcomponent-comp-formcolormode-e-sys.md) | 卡片色彩模式枚举。 |
| [FormDimension](arkts-arkui-formcomponent-comp-formdimension-e-sys.md) | 卡片尺寸枚举 |
| [FormRenderingMode](arkts-arkui-formcomponent-comp-formrenderingmode-e-sys.md) | 卡片渲染模式枚举 |
| [FormShape](arkts-arkui-formcomponent-comp-formshape-e-sys.md) | 定义卡片形状枚举。 |

## 示例

卡片示例。

该示例创建一张2 * 2尺寸大小的卡片，并注册事件回调。

```TypeScript
// card.ets
@Entry
@Component
struct CardExample {
  @State formId:string = '0';
  build() {
    Column() {
      Text('this is a card')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      FormComponent({
        id:this.formId,
        name:"Form1",
        bundle:"com.example.cardexample",
        ability:"FormAbility",
        module:"entry",
        dimension:FormDimension.Dimension_2_2,
        temporary:false
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
