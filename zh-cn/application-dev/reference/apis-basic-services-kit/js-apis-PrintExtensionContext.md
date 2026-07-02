# PrintExtensionContext

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->

PrintExtensionContext是PrintExtensionAbility的上下文环境，继承自[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。

PrintExtensionContext可直接作为PrintExtension的上下文环境，提供允许访问特定于PrintExtensionAbility的资源的能力。

> **说明：**
>
> - 本模块接口仅可在Stage模型下使用。
> - 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```
## 使用说明

通过PrintExtensionAbility子类实例来获取。

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class printExtension extends PrintExtensionAbility {

  onCreate(want: Want) {
    let context = this.context;
  }
}
```