# FeatureAbility

```TypeScript
export declare class FeatureAbility
```

**Since:** 5

**Deprecated since:** 8

**Substitutes:** FeatureAbility

<!--Device-unnamed-export declare class FeatureAbility--><!--Device-unnamed-export declare class FeatureAbility-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## callAbility

```TypeScript
static callAbility(param: CallAbilityParam): Promise<string>
```

Calls an AA.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static callAbility(param: CallAbilityParam): Promise<string>--><!--Device-FeatureAbility-static callAbility(param: CallAbilityParam): Promise<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [CallAbilityParam](arkts-arkui-featureability-callabilityparam-i.md) | Yes | Indicates the request param. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | A Promise object is returned, which contains the result data returned by the AA. The result is a JSON string. |

## continueAbility

```TypeScript
static continueAbility(): Promise<Result>
```

Start FA migration.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static continueAbility(): Promise<Result>--><!--Device-FeatureAbility-static continueAbility(): Promise<Result>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkui-featureability-result-i.md)&gt; | A Promise object is returned, which contains the result data returned by the AA. The result is a JSON string. |

## finishWithResult

```TypeScript
static finishWithResult(param: FinishWithResultParams): Promise<Result>
```

FA call the interface to destroy itself and set the result as parameters.

**Since:** 5

**Deprecated since:** 8

**Substitutes:** terminateSelfWithResult

<!--Device-FeatureAbility-static finishWithResult(param: FinishWithResultParams): Promise<Result>--><!--Device-FeatureAbility-static finishWithResult(param: FinishWithResultParams): Promise<Result>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [FinishWithResultParams](arkts-arkui-featureability-finishwithresultparams-i.md) | Yes | Indicates the request param. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkui-featureability-result-i.md)&gt; | A Promise object is returned, which contains the result whether to callback successfully. |

## getDeviceList

```TypeScript
static getDeviceList(flag: number): Promise<Result>
```

Get device information list.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static getDeviceList(flag: number): Promise<Result>--><!--Device-FeatureAbility-static getDeviceList(flag: number): Promise<Result>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | number | Yes | Default 0, get the information list of all devices in the network. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkui-featureability-result-i.md)&gt; | A Promise object is returned, which contains the result whether the device information list is obtained successfully. |

## sendMsg

```TypeScript
static sendMsg(options: SendMessageOptions): void
```

Sends messages to the destination device.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static sendMsg(options: SendMessageOptions): void--><!--Device-FeatureAbility-static sendMsg(options: SendMessageOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SendMessageOptions](arkts-arkui-featureability-sendmessageoptions-i.md) | Yes | Options. |

## startAbility

```TypeScript
static startAbility(request: RequestParams): Promise<Result>
```

Start a FA without callback result.

**Since:** 5

**Deprecated since:** 8

**Substitutes:** startAbility

<!--Device-FeatureAbility-static startAbility(request: RequestParams): Promise<Result>--><!--Device-FeatureAbility-static startAbility(request: RequestParams): Promise<Result>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [RequestParams](arkts-arkui-featureability-requestparams-i.md) | Yes | Indicates the request param. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkui-featureability-result-i.md)&gt; | A Promise object is returned, which contains the result of whether to call Ability's interface successfully. |

## startAbilityForResult

```TypeScript
static startAbilityForResult(request: RequestParams): Promise<Result>
```

Start a FA with callback result.

**Since:** 5

**Deprecated since:** 8

**Substitutes:** startAbilityForResult

<!--Device-FeatureAbility-static startAbilityForResult(request: RequestParams): Promise<Result>--><!--Device-FeatureAbility-static startAbilityForResult(request: RequestParams): Promise<Result>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [RequestParams](arkts-arkui-featureability-requestparams-i.md) | Yes | Indicates the request param. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkui-featureability-result-i.md)&gt; | A Promise object is returned, which contains the result of the data FA returned. |

## subscribeAbilityEvent

```TypeScript
static subscribeAbilityEvent(param: SubscribeAbilityEventParam, func: Function): Promise<string>
```

Subscribe to events of an AA.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static subscribeAbilityEvent(param: SubscribeAbilityEventParam, func: Function): Promise<string>--><!--Device-FeatureAbility-static subscribeAbilityEvent(param: SubscribeAbilityEventParam, func: Function): Promise<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [SubscribeAbilityEventParam](arkts-arkui-featureability-subscribeabilityeventparam-i.md) | Yes | Indicates the request param. |
| func | Function | Yes | Indicates the event reporting callback. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | A Promise object is returned, which contains the result data returned by the AA. The result is a JSON string. |

## subscribeMsg

```TypeScript
static subscribeMsg(options: SubscribeMessageOptions): void
```

Listens for messages sent from other devices.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static subscribeMsg(options: SubscribeMessageOptions): void--><!--Device-FeatureAbility-static subscribeMsg(options: SubscribeMessageOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeMessageOptions](arkts-arkui-featureability-subscribemessageoptions-i.md) | Yes | Options. |

## unsubscribeAbilityEvent

```TypeScript
static unsubscribeAbilityEvent(param: SubscribeAbilityEventParam): Promise<string>
```

Unsubscribe from events of an AA.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static unsubscribeAbilityEvent(param: SubscribeAbilityEventParam): Promise<string>--><!--Device-FeatureAbility-static unsubscribeAbilityEvent(param: SubscribeAbilityEventParam): Promise<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [SubscribeAbilityEventParam](arkts-arkui-featureability-subscribeabilityeventparam-i.md) | Yes | Indicates the request param. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | A Promise object is returned, which contains the result data returned by the AA. The result is a JSON string. |

## unsubscribeMsg

```TypeScript
static unsubscribeMsg(): void
```

Cancel the listening for messages sent from other devices.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static unsubscribeMsg(): void--><!--Device-FeatureAbility-static unsubscribeMsg(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
