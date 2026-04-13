# ArkTS卡片适配常见问题
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

## ArkTS卡片开发是否支持V2装饰器？如何从V1到V2迁移？

ArkTS卡片开发支持V2装饰器语法(如[\@ObservedV2](../ui/state-management/arkts-new-observedV2-and-trace.md)、[\@ComponentV2](../ui/state-management/arkts-create-custom-components.md#componentv2))，建议开发者使用V2装饰器替代V1语法进行状态管理，以获得更优的组件渲染性能和状态同步能力。

完整的语法差异对比、迁移步骤及示例代码，请参见官方文档: [V1->V2迁移指导概述](../ui/state-management/arkts-v1-v2-migration.md)。

<!--RP1--><!--RP1End-->

## ArkTS卡片如何适配深浅色模式？
当前系统存在深浅色两种显示模式，为了给用户更好的使用体验，保障卡片与页面视觉体验一致性，ArkTS卡片支持适配深浅色模式，具体请参考[应用深浅色适配](../ui/ui-dark-light-color-adaptation.md)。

## 导入particleAbility、audio、camera、media、backgroundTaskManager模块导致应用崩溃问题。

### 问题现象

系统会报程序崩溃，FaultLog文件的报错指向particleAbility、audio、camera、media、backgroundTaskManager模块的调用行。
![CrashCode](figures/crash代码行.png)
报错对应的代码行如下：
![CrashMessage](figures/crash信息.png)
### 可能原因

ArkTS卡片的FormExtensionAbility模块不支持加载particleAbility、audio、camera、media、backgroundTaskManager模块，参考[@ohos.app.form.FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md)。强行加载得到的对象是undefined，使用到了就会产生jscrash。

### 解决措施

排查FormExtensionAbility文件中的导入链条，把涉及到particleAbility、audio、camera、media、backgroundTaskManager模块的文件与ArkTS卡片需要使用的文件拆分开，避免会被FormExtensionAbility加载。

