# getOAID

## 导入模块

```TypeScript
import { identifier } from '@kit.AdsKit';
```

<a id="getoaid"></a>
## getOAID

```TypeScript
function getOAID(callback: AsyncCallback<string>): void
```

获取开放匿名设备标识符（OAID）。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.APP_TRACKING_CONSENT

<!--Device-identifier-function getOAID(callback: AsyncCallback<string>): void--><!--Device-identifier-function getOAID(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Advertising.OAID

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回开放匿名设备标识符（OAID）。1.如应用已配置ohos.permission.APP_TRACKING_CONSENT权限，且“跨应用关联访问权限”为“允许”，则返回OAID。2.如应用已配置ohos.permission.APP_TRACKING_CONSENT权限，且“跨应用关联访问权限”为“禁止”，则返回00000000-0000-0000-0000-000000000000。3.如应用未配置ohos.permission.APP_TRACKING_CONSENT权限，则返回00000000-0000-0000-0000-000000000000。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17300001](../errorcode-oaid.md#17300001-系统内部错误) | System internal error. |

**示例：**

```TypeScript
import { identifier } from '@kit.AdsKit';
import { BusinessError } from '@kit.BasicServicesKit';

identifier.getOAID((err: BusinessError, data: string) => {
  if (err.code) {
    return;
  }
  const oaid: string = data;
});

```


<a id="getoaid-1"></a>
## getOAID

```TypeScript
function getOAID(): Promise<string>
```

获取开放匿名设备标识符（OAID）。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.APP_TRACKING_CONSENT

<!--Device-identifier-function getOAID(): Promise<string>--><!--Device-identifier-function getOAID(): Promise<string>-End-->

**系统能力：** SystemCapability.Advertising.OAID

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回开放匿名设备标识符（OAID）。1.如应用已配置ohos.permission.APP_TRACKING_CONSENT权限，且跨应用关联访问权限为“允许”，则返回OAID。2.如应用已配置ohos.permission.APP_TRACKING_CONSENT权限，且跨应用关联访问权限为“禁止”，则返回00000000-0000-0000-0000-000000000000。3.如应用未配置ohos.permission.APP_TRACKING_CONSENT权限，则返回00000000-0000-0000-0000-000000000000。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17300001](../errorcode-oaid.md#17300001-系统内部错误) | System internal error. |

**示例：**

```TypeScript
import { identifier } from '@kit.AdsKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

void identifier.getOAID().then((data: string) => {
  const oaid: string = data;
}).catch((error: BusinessError) => {
  hilog.error(0x0000, 'testTag', `Failed to get oaid. Code is ${error.code}, message is ${error.message}`);
});

```

