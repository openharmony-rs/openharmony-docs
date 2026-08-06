# PrintExtensionContext

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

PrintExtensionContext是PrintExtensionAbility的上下文环境，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。

PrintExtensionContext可直接作为PrintExtensionAbility的上下文环境，用于在打印扩展开发场景中获取和管理打印相关资源，以完成打印任务相关操作。关于PrintExtensionContext的设计逻辑与可访问资源，请参见[PrintExtensionAbility](js-apis-app-ability-PrintExtensionAbility.md)与[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。

> **说明：**
>
> - 本模块接口仅可在Stage模型下使用。
> - **起始版本：** 26.0.0

## 导入模块
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```
## 使用说明

通过PrintExtensionAbility子类实例获取PrintExtensionContext。

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class PrintExtension extends PrintExtensionAbility {

  onCreate(want: Want) {
    let context = this.context; // 获取PrintExtensionContext，后续可通过context访问打印相关资源
  }
}
```
