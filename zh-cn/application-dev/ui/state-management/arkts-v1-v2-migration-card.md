# 卡片状态变量迁移
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

ArkTS卡片开发支持状态管理V2装饰器（如[\@ComponentV2](./arkts-create-custom-components.md#componentv2)、[\@Local](./arkts-new-local.md)、[\@ObservedV2](./arkts-new-observedV2-and-trace.md)等），建议开发者使用V2装饰器替代V1装饰器进行状态管理，以获得更优的组件渲染性能和状态同步能力。

卡片的状态管理迁移与普通应用页面基本一致，组件内、数据对象等通用场景的迁移可参见[组件内状态变量迁移](./arkts-v1-v2-migration-inner-component.md)和[数据对象状态变量迁移](./arkts-v1-v2-migration-inner-class.md)。本文仅针对卡片独有的差异点进行说明，即卡片提供方与卡片UI之间的数据接收机制。

场景对比表格如下：

| 卡片场景 | V1装饰器 | V2装饰器 |
| -------- | -------- | -------- |
| 卡片入口组件 | [\@Component](./arkts-create-custom-components.md#component) | [\@ComponentV2](./arkts-create-custom-components.md#componentv2) |
| 接收卡片提供方刷新数据 | [\@LocalStorageProp](./arkts-localstorage.md#localstorageprop) | [\@Local](./arkts-new-local.md)、[\@Provider](./arkts-new-provider-and-consumer.md)等 |
| 卡片内部状态变量 | [\@State](./arkts-state.md) | [\@Local](./arkts-new-local.md) |
| 嵌套数据对象 | [\@Observed](./arkts-observed-and-objectlink.md)/[\@ObjectLink](./arkts-observed-and-objectlink.md) | [\@ObservedV2](./arkts-new-observedV2-and-trace.md)/[\@Trace](./arkts-new-observedV2-and-trace.md) |


## 卡片数据接收机制差异

卡片UI（widget页面）运行在系统的卡片渲染服务进程中，与卡片提供方应用（FormExtensionAbility）相互独立。两者之间的数据交互只能通过[updateForm](../../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)接口实现：卡片提供方调用updateForm推送数据，卡片UI接收数据后刷新界面。

V1与V2在数据接收上的核心差异在于匹配规则：

- V1：卡片UI通过[\@LocalStorageProp](./arkts-localstorage.md#localstorageprop)接收刷新数据。匹配依据是\@LocalStorageProp装饰器的入参key值，即`@LocalStorageProp('title')`匹配updateForm数据中key为`'title'`的字段。卡片入口组件需要使用`@Entry(storage)`传入LocalStorage实例。
- V2：卡片UI支持通过\@Local、\@Provider等可被通知的状态装饰器直接接收刷新数据。匹配依据是变量名，即`@Local title`匹配updateForm数据中key为`'title'`的字段。卡片入口组件使用`@Entry`即可，无需再传入LocalStorage实例。

## 限制条件

- 卡片仅支持[ArkTS声明式开发范式](../../form/arkts-ui-widget-page-overview.md)的部分组件、事件、动效、数据管理和状态管理能力。开发时请留意相关接口是否标注"卡片能力"（如：从API version 12开始，该接口支持在ArkTS卡片中使用）。

- 卡片支持的状态管理V2装饰器以接口标注的"卡片能力"为准。若某V2接口未标注支持在ArkTS卡片中使用，则在卡片中不可用。

- 卡片入口组件迁移为[\@ComponentV2](./arkts-create-custom-components.md#componentv2)后，\@ComponentV2不支持LocalStorage相关能力。卡片场景下，支持通过变量名将updateForm刷新数据直接通知到\@Local、\@Provider等V2状态装饰器，因此卡片入口组件无需再使用LocalStorage。

- 更多卡片开发约束请参见[ArkTS卡片概述](../../form/arkts-form-overview.md#约束与限制)。


## 卡片数据接收迁移

**迁移规则：**

- 入口组件由`@Entry(storage) @Component`迁移为`@Entry @ComponentV2`，不再需要创建和传入LocalStorage实例。
- \@LocalStorageProp按需迁移为\@Local（组件内使用）或\@Provider（需跨组件共享）等V2状态装饰器。
- 迁移时需确保V2装饰器的变量名与卡片提供方updateForm推送数据的key值一致。若原V1代码中\@LocalStorageProp的入参key与变量名不同，迁移时应统一为相同名称。
- 卡片提供方FormExtensionAbility的updateForm调用逻辑无需改动。

以卡片主动刷新场景为例：卡片上展示标题和详情信息，点击刷新按钮后通过[postCardAction](../../reference/apis-arkui/js-apis-postCardAction.md#postcardaction-1)触发message事件，FormExtensionAbility在[onFormEvent](../../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonformevent)回调中调用updateForm刷新卡片数据。

**V1实现代码如下：**

卡片入口组件使用`@Entry(storage)`传入LocalStorage，并通过`@LocalStorageProp('title')`、`@LocalStorageProp('detail')`接收刷新数据，匹配依据为装饰器入参key值。

<!-- @[CardMigrationV1](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/widget/pages/WidgetCardV1.ets) -->

``` TypeScript
let storage = new LocalStorage();

// V1卡片入口组件需通过@Entry传入LocalStorage实例，用于接收卡片提供方updateForm推送的数据
@Entry(storage)
@Component
struct WidgetCardV1 {
  // 通过@LocalStorageProp的入参key值匹配updateForm数据中的对应字段
  @LocalStorageProp('title') title: string = 'Default title';
  @LocalStorageProp('detail') detail: string = 'Default detail';

  build() {
    Column() {
      Column() {
        Text(this.title)
          .fontSize(14)
          .margin({ top: '8%', left: '10%' })
        Text(this.detail)
          .fontSize(12)
          .margin({ top: '5%', left: '10%' })
      }
      .width('100%')
      .height('50%')
      .alignItems(HorizontalAlign.Start)

      Button('update')
        .margin({ top: '15%' })
        .onClick(() => {
          postCardAction(this, {
            'action': 'message',
            'params': { 'msgTest': 'messageEvent' }
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

**V1迁移V2：**

入口组件迁移为`@Entry @ComponentV2`，移除LocalStorage实例的创建与传入；\@LocalStorageProp迁移为\@Local，变量名`title`、`detail`分别与updateForm推送数据的key保持一致，系统据此将刷新数据直接通知到对应装饰器。

<!-- @[CardMigrationV2](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/widget/pages/WidgetCard.ets) -->

``` TypeScript
// V2迁移后入口组件使用@ComponentV2，无需再传入LocalStorage实例
@Entry
@ComponentV2
struct WidgetCard {
  // @LocalStorageProp迁移为@Local，系统改为按变量名匹配updateForm数据
  @Local title: string = 'Default title';
  @Local detail: string = 'Default detail';

  build() {
    Column() {
      Column() {
        Text(this.title)
          .fontSize(14)
          .margin({ top: '8%', left: '10%' })
        Text(this.detail)
          .fontSize(12)
          .margin({ top: '5%', left: '10%' })
      }
      .width('100%')
      .height('50%')
      .alignItems(HorizontalAlign.Start)

      Button('update')
        .margin({ top: '15%' })
        .onClick(() => {
          postCardAction(this, {
            'action': 'message',
            'params': { 'msgTest': 'messageEvent' }
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

卡片提供方FormExtensionAbility的实现无需改动，updateForm推送的数据key与V2卡片中的变量名一致即可生效。

<!-- @[CardMigrationFormAbility](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/entryformability/EntryFormAbility.ets) -->

``` TypeScript
onFormEvent(formId: string, message: string) {
  class FormDataClass {
    // 变量名与卡片页面中接收数据的变量名保持一致
    title: string = 'Title Update.';
    detail: string = 'Description update success.';
  }

  let formData = new FormDataClass();
  let formInfo: formBindingData.FormBindingData = formBindingData.createFormBindingData(formData);
  formProvider.updateForm(formId, formInfo).then(() => {
    hilog.info(DOMAIN_NUMBER, TAG, 'FormAbility updateForm success.');
  }).catch((error: BusinessError) => {
    hilog.error(DOMAIN_NUMBER, TAG, `Operation updateForm failed. Cause: ${JSON.stringify(error)}`);
  });
}
```

![card_migration](./figures/card_migration.gif)

## 卡片跨组件数据共享迁移

**迁移规则：**

在V1中，卡片多个组件可通过各自的\@LocalStorageProp读取同一LocalStorage中的数据实现共享。迁移至V2后，卡片入口组件可使用\@Provider接收刷新数据，子组件通过\@Consumer自动同步，无需再依赖LocalStorage。

下例中，`detail`变量需要跨组件共享。

**V1实现代码如下：**

入口组件与子组件均通过\@LocalStorageProp读取LocalStorage中的同一份数据实现共享。

<!-- @[CardMigrationShareV1](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/sharewidget/pages/ShareWidgetCardV1.ets) -->

``` TypeScript
let storage = new LocalStorage();

// V1卡片入口组件需通过@Entry传入LocalStorage实例
@Entry(storage)
@Component
struct ShareWidgetCardV1 {
  // 通过@LocalStorageProp的入参key值匹配updateForm数据
  @LocalStorageProp('title') title: string = 'Default title';
  @LocalStorageProp('detail') detail: string = 'Default detail';

  build() {
    Column() {
      Column() {
        Text(this.title)
          .fontSize(14)
          .margin({ top: '8%', left: '10%' })
        Text(this.detail)
          .fontSize(12)
          .margin({ top: '5%', left: '10%' })
        ChildComp1()
      }
      .width('100%')
      .height('50%')
      .alignItems(HorizontalAlign.Start)

      Button('update')
        .margin({ top: '15%' })
        .onClick(() => {
          postCardAction(this, {
            'action': 'message',
            'params': { 'msgTest': 'messageEvent' }
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct ChildComp1 {
  // 子组件同样通过@LocalStorageProp读取LocalStorage中的共享数据
  @LocalStorageProp('detail') detail: string = 'Default detail';

  build() {
    Text(this.detail)
      .fontSize(12)
      .margin({ top: '3%', left: '10%' })
  }
}
```

**V1迁移V2：**

入口组件移除LocalStorage，仅组件内部使用的`title`迁移为\@Local；需要跨组件共享的`detail`迁移为\@Provider，子组件通过\@Consumer同步数据。updateForm推送数据的key为`detail`，与\@Provider的变量名一致，数据更新后通过[\@Provider](./arkts-new-provider-and-consumer.md)/[\@Consumer](./arkts-new-provider-and-consumer.md)自动同步给子组件。

<!-- @[CardMigrationShareV2](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/StateMigrationProject/entry/src/main/ets/sharewidget/pages/ShareWidgetCard.ets) -->

``` TypeScript
// V2迁移后入口组件使用@ComponentV2，无需再传入LocalStorage实例
@Entry
@ComponentV2
struct ShareWidgetCard {
  // 仅组件内部使用的变量迁移为@Local
  @Local title: string = 'Default title';
  // 需跨组件共享的变量迁移为@Provider，系统按变量名匹配updateForm数据
  @Provider() detail: string = 'Default detail';

  build() {
    Column() {
      Column() {
        Text(this.title)
          .fontSize(14)
          .margin({ top: '8%', left: '10%' })
        Text(this.detail)
          .fontSize(12)
          .margin({ top: '5%', left: '10%' })
        ChildComp()
      }
      .width('100%')
      .height('50%')
      .alignItems(HorizontalAlign.Start)

      Button('update')
        .margin({ top: '15%' })
        .onClick(() => {
          postCardAction(this, {
            'action': 'message',
            'params': { 'msgTest': 'messageEvent' }
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct ChildComp {
  // 子组件通过@Consumer同步@Provider提供的数据
  @Consumer() detail: string = 'Default detail for Consumer';

  build() {
    Text(this.detail)
      .fontSize(12)
      .margin({ top: '3%', left: '10%' })
  }
}
```

![card_migration](./figures/card_migration_share.gif)
