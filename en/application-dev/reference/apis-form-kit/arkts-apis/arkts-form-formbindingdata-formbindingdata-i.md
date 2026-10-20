# FormBindingData

```TypeScript
interface FormBindingData
```

Defines the createFormBindingData result interface.

**Since:** 9

<!--Device-formBindingData-interface FormBindingData--><!--Device-formBindingData-interface FormBindingData-End-->

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formBindingData } from '@kit.FormKit';
```

## data

```TypeScript
data: Object
```

Data for updating.

**Type:** Object

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FormBindingData-data: Object--><!--Device-FormBindingData-data: Object-End-->

**System capability:** SystemCapability.Ability.Form

## isSupportMoreImages

```TypeScript
isSupportMoreImages?: boolean
```

Indicates whether to support updating more images if the widget data is updated using shared memory. When set to false , the maximum number of normally displayed images is 20. Default value: false. When set to true, the maximum number of normally displayed images is 30.<br>**NOTE:** <br>The total size of more images may exceed 10 MB, causing the form data update to fail. Default value: false.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-FormBindingData-isSupportMoreImages?: boolean--><!--Device-FormBindingData-isSupportMoreImages?: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## proxies

```TypeScript
proxies?: Array<ProxyData>
```

proxies for updating.

**Type:** Array&lt;[ProxyData](arkts-form-formbindingdata-proxydata-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FormBindingData-proxies?: Array<ProxyData>--><!--Device-FormBindingData-proxies?: Array<ProxyData>-End-->

**System capability:** SystemCapability.Ability.Form
