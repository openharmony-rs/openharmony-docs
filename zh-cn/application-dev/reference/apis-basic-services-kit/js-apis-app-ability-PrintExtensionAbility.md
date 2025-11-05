# @ohos.app.ability.PrintExtensionAbility (打印扩展能力)

该模块为打印扩展能力的操作API，提供调用打印扩展能力的接口。

> **说明：**  
> 本模块首批接口从API version 14开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## PrintExtensionAbility.onCreate

onCreate(want: Want): void

初始化扩展能力，会在系统首次连接打印扩展时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：20

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| want | Want | 是 | 表示调用打印页面需要参数。 |

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import Want from '@ohos.app.ability.Want';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCreate(want: Want): void {
        console.log('onCreate');
        // ...
    }
}
```

## PrintExtensionAbility.onStartDiscoverPrinter

onStartDiscoverPrinter(): void

开始发现与设备连接的打印机时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：20

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartDiscoverPrinter(): void {
        console.log('onStartDiscoverPrinter enter');
        // ...
    }
}
```

## PrintExtensionAbility.onStopDiscoverPrinter

onStopDiscoverPrinter(): void

停止发现打印机时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：20

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStopDiscoverPrinter(): void {
        console.log('onStopDiscoverPrinter enter');
        // ...
    }
}
```

## PrintExtensionAbility.onConnectPrinter

ArkTS-Dyn: onConnectPrinter(printerId: number): void

ArkTS-Sta: onConnectPrinter(printerId: int): void

连接到特定打印机时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：20

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| printerId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 表示打印机ID。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: number): void {
        console.log('onConnectPrinter enter');
        // ...
    }
}
```

ArkTS-Sta示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: int): void {
        console.log('onConnectPrinter enter');
        // ...
    }
}
```

## PrintExtensionAbility.onDisconnectPrinter

ArkTS-Dyn: onDisconnectPrinter(printerId: number): void

ArkTS-Sta: onDisconnectPrinter(printerId: int): void

断开与特定打印机的连接时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：20

**参数：**
| **参数名** | **类型** | **必填** | **说明** |
| -------- | -------- | -------- | -------- |
| printerId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 表示打印机ID。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: number): void {
        console.log('onDisconnectPrinter enter');
        // ...
    }
}
```

ArkTS-Sta示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: int): void {
        console.log('onDisconnectPrinter enter');
        // ...
    }
}
```

## PrintExtensionAbility.onDestroy

onDestroy(): void

结束打印扩展时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：20

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDestroy(): void {
        console.log('onDestroy');
    }
}
```
