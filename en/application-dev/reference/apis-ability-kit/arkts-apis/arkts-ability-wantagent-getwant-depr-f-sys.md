# getWant (System API)

## Modules to Import

```TypeScript
```

## getWant

```TypeScript
function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void
```

Obtains the [Want](arkts-ability-app-ability-want-want-c.md) of an [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getWant](arkts-ability-wantagent-getwant-f-sys.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | Indicates the [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent) whose UID is to be obtained. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Obtain the callback method for Want in WantAgent. |


## getWant

```TypeScript
function getWant(agent: WantAgent): Promise<Want>
```

Obtains the [Want](arkts-ability-app-ability-want-want-c.md) of an [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getWant](arkts-ability-wantagent-getwant-f-sys.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | Indicates the [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent) whose UID is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Returns the [Want](arkts-ability-app-ability-want-want-c.md) of the [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent). |
