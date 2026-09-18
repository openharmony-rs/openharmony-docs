# showAd

## 导入模块

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## showAd

```TypeScript
function showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void
```

展示全屏广告。

> **说明：** 
> 
> 1. 为了保证广告能正确展示，该接口必须和请求广告接口配套使用。
> 
> 2. 该接口仅支持展示激励广告和插屏广告。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ad | [Advertisement](arkts-ads-advertising-advertisement-t.md) | 是 | 广告对象。 |
| options | [AdDisplayOptions](arkts-ads-advertising-addisplayoptions-i.md) | 是 | 广告展示参数。 |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | 否 | UIAbility的上下文环境，不设置从api: [@ohos.app.ability.common](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ js-apis-app-ability-common)中获取。<br>**适用版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |
| [21800004](../errorcode-ads.md#21800004-广告展示失败) | Failed to display the ad. |

**示例**

```TypeScript
其中context的获取方式参见[各类Context的获取方式](../../../application-models/application-context-stage.md#context的获取方式)。
```
