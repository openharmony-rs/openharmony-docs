# showAd

## showAd

```TypeScript
function showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void
```

展示全屏广告。 > **说明：** > > 1. 为了保证广告能正确展示，该接口必须和请求广告接口配套使用。 > > 2. 该接口仅支持展示激励广告和插屏广告。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-advertising-function showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void--><!--Device-advertising-function showAd(ad: Advertisement, options: AdDisplayOptions, context?: common.UIAbilityContext): void-End-->

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ad | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 广告对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 广告展示参数。 |
| context | common.UIAbilityContext | 否 | UIAbility的上下文环境，不设置从api:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中获取。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Invalid input parameter. Possible causes: 1. Mandatory parameters are left unspecified. |
| [21800001](../errorcode-ads.md#21800001-系统内部错误) | System internal error. |
| [21800004](../errorcode-ads.md#21800004-广告展示失败) | Failed to display the ad. |

**示例：**

其中context的获取方式参见[各类Context的获取方式](../../application-models/application-context-stage.md#context的获取方式)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { advertising } from '@kit.AdsKit';

function showAd(ad: advertising.Advertisement, context?: common.UIAbilityContext): void {
  // 广告展示参数，开发者可根据项目实际情况设置
  const adDisplayOptions: advertising.AdDisplayOptions = {};
  // 调用全屏广告展示接口
  advertising.showAd(ad, adDisplayOptions, context);
}
```

