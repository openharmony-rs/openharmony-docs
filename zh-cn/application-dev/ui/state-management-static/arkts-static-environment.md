# Environment：设备环境查询

如果开发者需要获取应用程序运行设备的环境参数（如多语言、深浅色模式等）以进行不同的场景判断，可以使用Environment。

Environment是ArkUI框架在应用程序启动时创建的单例对象，提供应用程序运行状态的属性给AppStorage。所有属性都是不可变的简单类型。

Environment提供了读取系统环境变量并将其值写入AppStorage的功能。开发者需要通过AppStorage获取环境变量的值。详细信息请参阅 [Environment 内置参数](#environment内置参数)。

在阅读本文档前，建议提前阅读[AppStorage](./arkts-static-appstorage.md)。

## Environment内置参数

| 键                   | 数据类型        | 描述                                                         |
| -------------------- | --------------- | ------------------------------------------------------------ |
| accessibilityEnabled | boolean         | 是否启用获取无障碍屏幕读取。true表示启用，false表示不启用。  |
| colorMode            | ColorMode       | 色彩模型类型。<br>- ColorMode.LIGHT：浅色。<br>- ColorMode.DARK：深色。 |
| fontScale            | number          | 字体大小比例。开发者需要配置configuration，设置fontSizeScale为"followSystem"，具体配置步骤可参考[configuration](../../quick-start/app-configuration-file.md#configuration标签)使fontScale跟随系统变化。<br>默认值跟随系统默认参数。 |
| fontWeightScale      | number          | 字体粗细程度。在不同的系统或者机型中，fontWeightScale的取值范围可能会有所不同。<br>默认值跟随系统默认参数。 |
| layoutDirection      | LayoutDirection | 布局方向类型：<br>- LayoutDirection.LTR：从左到右。<br>- LayoutDirection.RTL：从右到左。 |
| languageCode         | string          | 当前系统语言值必须为小写字母（例如：zh）。默认值跟随系统默认参数。 |

## 使用场景

### 从UI中访问Environment参数

- 将设备运行的环境变量使用Environment.envProp存入AppStorage中。

  ```ts
  import { Environment } from '@kit.ArkUI';

  // 将设备的语言code存入AppStorage，默认值为en
  Environment.envProp<string>('languageCode', 'en');
  ```

- 可以使用\@StoragePropRef链接到Component中。

  ```ts
  import { StoragePropRef } from '@kit.ArkUI';
  
  @StoragePropRef('languageCode') lang: string = 'en';
  ```

设备环境到Component的更新链：Environment --&gt; AppStorage --&gt; Component。

> **说明：**
>
> \@StoragePropRef关联的环境参数可以在本地更改，但不能同步回AppStorage中，因为应用对环境变量参数是不可写的，只能在Environment中查询。

```ts
'use static'

// 将设备languageCode存入AppStorage中
import { Entry, Text, Row, Column, Component, Button, ClickEvent } from '@kit.ArkUI';
import { Environment, StoragePropRef } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @StoragePropRef('languageCode') languageCode: string = 'en';
  // 在ArkTS-Sta中，全局的逻辑代码不会默认执行。开发者可将需要执行的逻辑代码移至static代码块中，以达到与ArkTS-Dyn一样的效果。
  static {
    Environment.envProp<string>('languageCode', 'en');
  }

  build() {
    Row() {
      Column() {
        // 输出当前设备的languageCode
        Text(this.languageCode)
      }
    }
  }
}
```

## 限制条件

Environment和UIContext相关联，需要在[UIContext](../../reference/apis-arkui/js-apis-arkui-UIContext.md#uicontext)明确的时候才可以调用。可以通过在[runScopedTask](../../reference/apis-arkui/js-apis-arkui-UIContext.md#runscopedtask)里明确上下文。如果没有在UIContext明确的地方调用，将导致无法查询到设备环境数据。

```ts
// EntryAbility.ets
'use static'

import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { Environment } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index');
    let window = windowStage.getMainWindow();
    window.then(window => {
      let uiContext = window.getUIContext();
      uiContext.runScopedTask(() => {
        Environment.envProp('languageCode', 'en');
      });
    });
  }
}
```