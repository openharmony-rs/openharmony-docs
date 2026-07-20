# getAdRequestBody

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

<a id="getadrequestbody"></a>
## getAdRequestBody

```TypeScript
function getAdRequestBody(adParams: AdRequestParams[], adOptions: AdOptions): Promise<string>
```

获取广告请求体，使用Promise异步回调（该接口仅对部分系统预置应用开放）。

**起始版本：** 12

<!--Device-advertising-function getAdRequestBody(adParams: AdRequestParams[], adOptions: AdOptions): Promise<string>--><!--Device-advertising-function getAdRequestBody(adParams: AdRequestParams[], adOptions: AdOptions): Promise<string>-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| adParams | [AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | 是 | 广告请求参数。**说明：** 该接口体的adId参数可以为空。 |
| adOptions | [AdOptions](arkts-ads-advertising-adoptions-i.md) | 是 | 广告配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回字符类型的广告数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Device not supported. |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |

**示例：**

```TypeScript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getAdRequestBody(adRequestParamsArray: advertising.AdRequestParams[]): Promise<void> {
  // 广告配置参数，开发者可根据项目实际情况设置
  const adOptions: advertising.AdOptions = {};
  await advertising.getAdRequestBody(adRequestParamsArray, adOptions).then((data: string) => {
    hilog.info(0x0000, 'testTag', `Succeeded in getting ad request body. Data is ${data}`);
  }).catch((error: BusinessError) => {
    hilog.error(0x0000, 'testTag', `Failed to get ad request body. Code is ${error.code}, message is ${error.message}`);
  });
}

```

