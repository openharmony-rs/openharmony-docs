# FormComponent(系统接口) (System API)

Defines FormComponent Component.

## FormComponent

```TypeScript
FormComponent(value: FormInfo)
```

Set a new value of form info.

**起始版本：** 7

<!--Device-FormComponentInterface-(value: FormInfo): FormComponentAttribute--><!--Device-FormComponentInterface-(value: FormInfo): FormComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FormInfo](arkts-arkui-formcomponent-comp-forminfo-i-sys.md) | 是 |  |

## 汇总

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ErrorInformation](arkts-arkui-formcomponent-comp-errorinformation-i-sys.md) | 卡片错误信息。 |
| [FormCallbackInfo](arkts-arkui-formcomponent-comp-formcallbackinfo-i-sys.md) | 卡片查询或者卸载时获取formId的参数。 |
| [FormInfo](arkts-arkui-formcomponent-comp-forminfo-i-sys.md) | 卡片信息。 |
| [FormSize](arkts-arkui-formcomponent-comp-formsize-i-sys.md) | 卡片大小信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FormColorMode](arkts-arkui-formcomponent-comp-formcolormode-e-sys.md) | 卡片色彩模式枚举。 |
| [FormDimension](arkts-arkui-formcomponent-comp-formdimension-e-sys.md) | 卡片尺寸枚举 |
| [FormRenderingMode](arkts-arkui-formcomponent-comp-formrenderingmode-e-sys.md) | 卡片渲染模式枚举 |
| [FormShape](arkts-arkui-formcomponent-comp-formshape-e-sys.md) | 定义卡片形状枚举。 |
<!--DelEnd-->

<!--Del-->
## 示例

### 示例1（创建卡片并注册事件回调）

该示例创建一张2 * 2尺寸大小的卡片，并注册事件回调，在onAcquired回调中获取卡片标识。



```TypeScript
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

### 示例2（同一应用的不同进程使用相同卡片标识挂载卡片）

从API版本26.1.0开始：同一应用的不同进程可以使用相同卡片标识（id）挂载卡片，多个使用方共享同一卡片实例。该示例中，formId为同一应用其他进程已获取的卡片标识。

```TypeScript
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

<!--DelEnd-->
