# PrintExtensionAbility

该模块提供打印扩展能力的调用接口。PrintExtensionAbility基于生命周期回调机制运行，系统在打印扩展连接、发现打印机、连接/断开打印机、查询打印机能力、启动/取消打印任务等场景下分别调用相应回调方法，开发者需在各回调中实现对应的打印扩展逻辑。

**起始版本：** 14

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { PrintExtensionAbility } from '@kit.BasicServicesKit';
```

## onRequestPreview

```TypeScript
onRequestPreview(jobInfo: print.PrintJob): string
```

系统打印服务在请求预览时回调此方法，开发者需继承PrintExtensionAbility类并实现此方法，将预览结果返回到系统打印服务。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| jobInfo | [print.PrintJob](arkts-basicservices-print-printjob-i.md) | 是 | 表示打印任务信息。 |

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
        let previewResult: string = '';
        return previewResult;
    }
}
```
