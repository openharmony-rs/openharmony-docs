# FeatureAbility (System API)

```TypeScript
export declare class FeatureAbility
```

**Since:** 5

**Deprecated since:** 8

**Substitutes:** FeatureAbility

<!--Device-unnamed-export declare class FeatureAbility--><!--Device-unnamed-export declare class FeatureAbility-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.

## sendMsg

```TypeScript
static sendMsg(options: SendMessageOptions): void
```

Sends messages to the destination device.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static sendMsg(options: SendMessageOptions): void--><!--Device-FeatureAbility-static sendMsg(options: SendMessageOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SendMessageOptions](arkts-arkui-featureability-sendmessageoptions-i.md) | Yes | Options. |

## subscribeMsg

```TypeScript
static subscribeMsg(options: SubscribeMessageOptions): void
```

Listens for messages sent from other devices.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static subscribeMsg(options: SubscribeMessageOptions): void--><!--Device-FeatureAbility-static subscribeMsg(options: SubscribeMessageOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeMessageOptions](arkts-arkui-featureability-subscribemessageoptions-i.md) | Yes | Options. |

## unsubscribeMsg

```TypeScript
static unsubscribeMsg(): void
```

Cancel the listening for messages sent from other devices.

**Since:** 5

**Deprecated since:** 8

<!--Device-FeatureAbility-static unsubscribeMsg(): void--><!--Device-FeatureAbility-static unsubscribeMsg(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.
