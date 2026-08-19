# PrintExtensionAbility（系统接口）

该模块提供打印扩展能力的调用接口。PrintExtensionAbility基于生命周期回调机制运行，系统在打印扩展连接、发现打印机、连接/断开打印机、查询打印机能力、启动/取消打印任务等场景下分别调用相应回调方法，开发者需在各回调中 实现对应的打印扩展逻辑。

**起始版本：** 23

<!--Device-unnamed-declare class PrintExtensionAbility--><!--Device-unnamed-declare class PrintExtensionAbility-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## onCancelPrintJob

```TypeScript
public onCancelPrintJob(jobInfo: print.PrintJob): void
```

取消已开始的打印任务时调用。开发者应在此回调中实现取消打印任务的逻辑，停止正在进行的打印操作并清理相关资源。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-public onCancelPrintJob(jobInfo: print.PrintJob): void--><!--Device-PrintExtensionAbility-public onCancelPrintJob(jobInfo: print.PrintJob): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobInfo | print.PrintJob | 是 | 表示打印任务的信息，包含任务ID、打印机ID、文档信息等详细配置和状态，需为已通过onStartPrintJob启动的打印任务， 用于取消打印任务时定位目标任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |

## onRequestPreview

```TypeScript
onRequestPreview(jobInfo: print.PrintJob): string
```

系统打印服务在请求预览时回调此方法，开发者需继承PrintExtensionAbility类并实现此方法，将预览结果返回到系统打印服务。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-onRequestPreview(jobInfo: print.PrintJob): string--><!--Device-PrintExtensionAbility-onRequestPreview(jobInfo: print.PrintJob): string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobInfo | print.PrintJob | 是 | 表示打印任务信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回的预览结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application |

**示例**

```TypeScript
import { print, PrintExtensionAbility } from '@kit.BasicServicesKit';

export default class HWPrintExtension extends PrintExtensionAbility {
    onRequestPreview(jobInfo: print.PrintJob): string {
        console.info('onRequestPreview enter');
        // ...
        let tmp : string = '';
        return tmp;
    }
}
```

## onRequestPrinterCapability

```TypeScript
public onRequestPrinterCapability(printerId: int): print.PrinterCapability
```

请求打印机支持的能力特性（如色彩模式、双面打印模式、纸张尺寸等）时调用，例如在打印设置界面中用户选择打印机后，系统需要获取该打印机支持的能力信息时触发此回调。 开发者应在此回调中根据printerId查询并返回对应打印机的能力信息（print.PrinterCapability）。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-public onRequestPrinterCapability(printerId: int): print.PrinterCapability--><!--Device-PrintExtensionAbility-public onRequestPrinterCapability(printerId: int): print.PrinterCapability-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| printerId | int | 是 | 表示打印机ID，应为已连接的打印机，取值于打印机发现流程上报的有效打印机标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| print.PrinterCapability | printer capability. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |

## onStartPrintJob

```TypeScript
public onStartPrintJob(jobInfo: print.PrintJob): void
```

开始打印任务时调用。开发者应在此回调中根据jobInfo中的任务信息处理打印操作，如解析打印任务参数并执行相应的打印流程。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrintExtensionAbility-public onStartPrintJob(jobInfo: print.PrintJob): void--><!--Device-PrintExtensionAbility-public onStartPrintJob(jobInfo: print.PrintJob): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobInfo | print.PrintJob | 是 | 表示打印任务的信息，包含任务ID、打印机ID、文档信息等详细配置和状态，用于指定要开始的打印任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application<br>**适用版本：** 10 - 23 |

