# MediaQueryListener

Implements the media query listener, including the first query result when the listener is applied for. The specified media query condition, for example, **'(width &lt;= 600vp)'**, is compared system information. If related information is not initialized during the first query, **matches** returns **false**.

Inherits from [MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md).

**Inheritance/Implementation:** MediaQueryListener extends [MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { mediaquery } from '@kit.ArkUI';
```

## off('change')

```TypeScript
off(type: 'change', callback?: Callback<MediaQueryResult>): void
```

Deregisters a media query listener, so that no callback is triggered when the media attributes change.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Listener type. The value is fixed at **'change'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md)&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks under this handle are unregistered. |

## on('change')

```TypeScript
on(type: 'change', callback: Callback<MediaQueryResult>): void
```

Registers a media query listener. The callback is triggered when the media attributes change.

> **NOTE:** 
> 
> The **on** or **off** function cannot be called in the registered callback.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Listener type. The value is fixed at **'change'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md)&gt; | Yes | Callback registered with media query. |
