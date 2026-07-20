# registerWatermarkCallback

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

<a id="registerwatermarkcallback"></a>
## registerWatermarkCallback

```TypeScript
function registerWatermarkCallback(callback: WatermarkCallback): void
```

注册强制水印处理的监听事件。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_PRINT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function registerWatermarkCallback(callback: WatermarkCallback): void--><!--Device-print-function registerWatermarkCallback(callback: WatermarkCallback): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [WatermarkCallback](arkts-basicservices-print-watermarkcallback-t.md) | 是 | 表示注册强制水印处理的监听事件时使用的回调类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

**示例：**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let watermarkCallback: print.WatermarkCallback = (jobId: string, fd: number) => {
    console.info('Watermark callback triggered, jobId: ' + jobId + ', fd: ' + fd);
}

try {
    print.registerWatermarkCallback(watermarkCallback);
    console.info('registerWatermarkCallback success');
} catch (error) {
    console.error('registerWatermarkCallback error: ' + JSON.stringify(error));
}

```

