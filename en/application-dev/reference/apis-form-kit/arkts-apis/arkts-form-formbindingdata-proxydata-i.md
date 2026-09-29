# ProxyData

```TypeScript
interface ProxyData
```

Defines the form proxy data.

@typedef ProxyData

**Since:** 10

<!--Device-formBindingData-interface ProxyData--><!--Device-formBindingData-interface ProxyData-End-->

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## key

```TypeScript
key: string
```

Key for proxy. The value depends on the data publisher.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ProxyData-key: string--><!--Device-ProxyData-key: string-End-->

**System capability:** SystemCapability.Ability.Form

## subscriberId

```TypeScript
subscriberId?: string
```

SubscriberId. The value depends on the data publisher. The default value is current formId.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ProxyData-subscriberId?: string--><!--Device-ProxyData-subscriberId?: string-End-->

**System capability:** SystemCapability.Ability.Form
