# PrintExtensionAbility（系统接口）

该模块提供打印扩展能力的调用接口。PrintExtensionAbility基于生命周期回调机制运行，系统在打印扩展连接、发现打印机、连接/断开打印机、查询打印机能力、启动/取消打印任务等场景下分别调用相应回调方法，开发者需在各回调中 实现对应的打印扩展逻辑。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class PrintExtensionAbility--><!--Device-unnamed-declare class PrintExtensionAbility-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## onConnectPrinter

```TypeScript
onConnectPrinter(printerId: int): void
```

连接到特定打印机时调用。开发者应在此回调中实现与指定打印机（通过printerId标识）的连接逻辑。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onConnectPrinter(printerId: int): void--><!--Device-PrintExtensionAbility-onConnectPrinter(printerId: int): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | int | 是 | 表示打印机ID，应为已发现的打印机，取值于打印机发现流程上报的有效打印机标识。 |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: number): void {
        console.info('onConnectPrinter enter');
        // ...
    }
}
```

ArkTS-Sta示例:

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: int): void {
        console.info('onConnectPrinter enter');
        // ...
    }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

系统首次连接打印扩展能力时调用。开发者可在此回调中完成打印扩展能力的初始化工作，如初始化必要的资源、状态等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onCreate(want: Want): void--><!--Device-PrintExtensionAbility-onCreate(want: Want): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 表示创建打印扩展时传入的Want意图信息，包含调用方指定的信息（如action、uri等），用于初始化打印扩展能力。 |

## 示例

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate');
        // ...
    }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

结束打印扩展能力时调用。开发者应在此回调中释放相关资源并完成必要的清理工作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onDestroy(): void--><!--Device-PrintExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 示例

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```

## onDisconnectPrinter

```TypeScript
onDisconnectPrinter(printerId: int): void
```

断开与特定打印机的连接时调用。开发者应在此回调中实现断开打印机连接的逻辑并释放相关资源。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onDisconnectPrinter(printerId: int): void--><!--Device-PrintExtensionAbility-onDisconnectPrinter(printerId: int): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | int | 是 | 表示打印机ID，应为已连接的打印机，取值于打印机发现流程上报的有效打印机标识。 |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: number): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

ArkTS-Sta示例:

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: int): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

## onStartDiscoverPrinter

```TypeScript
onStartDiscoverPrinter(): void
```

开始发现打印机时调用。开发者可在此回调中实现自己的打印机发现逻辑，可通过 [addPrinterToDiscovery](arkts-basicservices-print-addprintertodiscovery-f.md#addPrinterToDiscovery) 将发现的打印机 信息上报给系统。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onStartDiscoverPrinter(): void--><!--Device-PrintExtensionAbility-onStartDiscoverPrinter(): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 示例

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartDiscoverPrinter(): void {
        console.info('onStartDiscoverPrinter enter');
        // ...
    }
}
```

## onStopDiscoverPrinter

```TypeScript
onStopDiscoverPrinter(): void
```

停止发现打印机时调用。开发者应在此回调中停止打印机发现流程并释放相关资源。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onStopDiscoverPrinter(): void--><!--Device-PrintExtensionAbility-onStopDiscoverPrinter(): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 示例

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStopDiscoverPrinter(): void {
        console.info('onStopDiscoverPrinter enter');
        // ...
    }
}
```

## context

```TypeScript
context: PrintExtensionContext
```

打印扩展能力上下文。

**类型：** [PrintExtensionContext](arkts-basicservices-printextensioncontext-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-context: PrintExtensionContext--><!--Device-PrintExtensionAbility-context: PrintExtensionContext-End-->

**系统能力：** SystemCapability.Print.PrintFramework

