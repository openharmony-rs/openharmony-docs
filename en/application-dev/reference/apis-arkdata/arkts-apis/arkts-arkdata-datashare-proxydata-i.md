# ProxyData

```TypeScript
interface ProxyData
```

Defines a struct for shared configurations.

**Since:** 20

<!--Device-dataShare-interface ProxyData--><!--Device-dataShare-interface ProxyData-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## allowList

```TypeScript
allowList?: string[]
```

List of apps that are allowed to subscribe to and read the shared configuration. If not specified, an empty string array is used. The maximum length of the array is 256, and elements beyond 256 do not take effect. When the shared configuration is published for the first time, if this parameter is not specified, an empty allowlist is used by default. When the shared configuration is updated, if this parameter is not specified, the allowlist of the shared configuration will not be updated. An empty allowlist indicates that only the publisher can access the shared configuration. Before API version 26.0.0, each element in the array is the [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) of an app. The maximum length of a single appIdentifier is 128 bytes, and an appIdentifier longer than 128 bytes does not take effect. Since API version 26.0.0, the array supports the special string "all" (case-sensitive), which indicates that all apps are allowed to access.

**Type:** string[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyData-allowList?: string[]--><!--Device-ProxyData-allowList?: string[]-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## isMultiValues

```TypeScript
isMultiValues?: boolean
```

Whether this is a multi-value shared configuration that uses values. **true** indicates that the data published this time is of the multi-value type, in which case the value parameter is ignored. **false** indicates a non-multi-value type. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyData-isMultiValues?: boolean--><!--Device-ProxyData-isMultiValues?: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## trustProviders

```TypeScript
trustProviders?: string[]
```

List of apps that can assign values to the multi-value shared configuration. The array can contain up to 256 elements, and elements beyond 256 do not take effect. Each element in the array is the [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) of an app. The maximum length of an appIdentifier is 128 bytes, and the part longer than 128 bytes does not take effect. If this parameter is not set when the shared configuration is published for the first time, the assignment list is empty by default. An empty assignment list indicates that only the publisher can assign values to the multi-value shared configuration. The array supports the special string "all" (case-sensitive), which indicates that all apps are allowed to assign values to the multi-value shared configuration. This parameter takes effect only when isMultiValues is set to **true**.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyData-trustProviders?: string[]--><!--Device-ProxyData-trustProviders?: string[]-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

Unique ID of a shared configuration, fixed at the format of **"datashareproxy://{*bundleName*}/{*path*}"**, in which **bundleName** indicates the bundle name of the publisher application, and **path** can be set to any value but must be unique in the same application. The value is a string with a maximum of 256 bytes.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyData-uri: string--><!--Device-ProxyData-uri: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## value

```TypeScript
value?: ValueType
```

Value of the shared configuration. If not specified, an empty string is used. **Note:** 1. Before API version 26.0.0, the string length does not exceed 4096 bytes. Since API version 26.0.0, the default maximum string length allowed is 4096 bytes, and you can configure maxValueLength in [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) to extend the maximum length to 102400 bytes. 2. When the shared configuration is published for the first time, if this parameter is not specified, an empty string is used by default. When the shared configuration is updated, if this parameter is not specified, the value of the shared configuration will not be updated.

**Type:** [ValueType](arkts-arkdata-valuetype-t.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyData-value?: ValueType--><!--Device-ProxyData-value?: ValueType-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

## values

```TypeScript
values?: Record<number, ValueType>
```

Value of the multi-value type. The first parameter in Record is the key, which is specified by the user and must be unique. The second parameter is the value corresponding to the key. A single app can add up to 10 values under a single URI, and the maximum length of each value is 4096 bytes. In addition, the total length of all values is limited by the maxValueLength field in [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md). This parameter takes effect only when isMultiValues is set to **true**, and it cannot be empty. When isMultiValues is **false**, the default value is undefined.

**Type:** Record&lt;number, [ValueType](arkts-arkdata-valuetype-t.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ProxyData-values?: Record<int, ValueType>--><!--Device-ProxyData-values?: Record<int, ValueType>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer
