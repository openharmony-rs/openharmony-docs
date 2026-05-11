# @ohos.app.ability.PrintExtensionAbility (打印扩展能力)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @RayShih-->

该模块为打印扩展能力的操作API，提供调用打印扩展能力的接口。

> **说明：**  
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
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

**ArkTS-Sta起始版本**：23

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-application-want.md#want) | 是 | 表示调用打印页面需要参数。 |

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCreate(want: Want): void {
        console.info('onCreate');
        // ...
    }
}
```

## PrintExtensionAbility.onStartDiscoverPrinter

onStartDiscoverPrinter(): void

开始发现与设备连接的打印机时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartDiscoverPrinter(): void {
        console.info('onStartDiscoverPrinter enter');
        // ...
    }
}
```

## PrintExtensionAbility.onStopDiscoverPrinter

onStopDiscoverPrinter(): void

停止发现打印机时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStopDiscoverPrinter(): void {
        console.info('onStopDiscoverPrinter enter');
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

**ArkTS-Sta起始版本**：23

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 表示打印机ID。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: number): void {
        console.info('onConnectPrinter enter');
        // ...
    }
}
```

ArkTS-Sta示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onConnectPrinter(printerId: int): void {
        console.info('onConnectPrinter enter');
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

**ArkTS-Sta起始版本**：23

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 表示打印机ID。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: number): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

ArkTS-Sta示例:
```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDisconnectPrinter(printerId: int): void {
        console.info('onDisconnectPrinter enter');
        // ...
    }
}
```

## PrintExtensionAbility.onStartPrintJob<sup>24+</sup>

onStartPrintJob(jobInfo: print.PrintJob): void

开始打印任务时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | 是 | 表示打印任务的信息。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartPrintJob(jobInfo: print.PrintJob): void {
        console.info('onStartPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

ArkTS-Sta示例:
```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onStartPrintJob(jobInfo: print.PrintJob): void {
        console.info('onStartPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

## PrintExtensionAbility.onCancelPrintJob<sup>24+</sup>

onCancelPrintJob(jobInfo: print.PrintJob): void

移除已开始的打印任务时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| jobInfo | [print.PrintJob](js-apis-print.md#printjob24) | 是 | 表示打印任务的信息。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCancelPrintJob(jobInfo: print.PrintJob): void {
        console.info('onCancelPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

ArkTS-Sta示例:
```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onCancelPrintJob(jobInfo: print.PrintJob): void {
        console.info('onCancelPrintJob, jobId is: ' + jobInfo.jobId);
        // ...
    }
}
```

## PrintExtensionAbility.onRequestPrinterCapability<sup>24+</sup>

ArkTS-Dyn: onRequestPrinterCapability(printerId: number): print.PrinterCapability

ArkTS-Sta: onRequestPrinterCapability(printerId: int): print.PrinterCapability

请求打印机能力时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| printerId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 表示打印机ID。 |

**返回值：**
| **类型** | **说明** |
| -------- | -------- |
| [print.PrinterCapability](js-apis-print.md#printercapability24) | 表示打印能力。 |

**示例：**

ArkTS-Dyn示例:
```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPrinterCapability(printerId: number): print.PrinterCapability {
        console.info('onRequestPrinterCapability enter');
        // ...
        let tmp : print.PrinterCapability = {
            colorMode : 1,
            duplexMode : 1,
            pageSize : []
        };
        return tmp;
    }
}
```

ArkTS-Sta示例:
```ts
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPrinterCapability(printerId: int): print.PrinterCapability {
        console.info('onRequestPrinterCapability enter');
        // ...
        let tmp : print.PrinterCapability = {
            colorMode : 1,
            duplexMode : 1,
            pageSize : []
        };
        return tmp;
    }
}
```

## PrintExtensionAbility.onDestroy

onDestroy(): void

结束打印扩展时调用。

**系统能力：** SystemCapability.Print.PrintFramework

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**示例：**

```ts
import { PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onDestroy(): void {
        console.info('onDestroy');
    }
}
```
