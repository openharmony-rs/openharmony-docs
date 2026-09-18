# off (System API)

## Modules to Import

```TypeScript
```

## off('formUninstall')

```TypeScript
function off(type: 'formUninstall', callback?: Callback<string>): void
```

Unsubscribes from widget uninstall events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Widget uninstall is different from widget removal. When an application is uninstalled, the corresponding widget
> is automatically uninstalled.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [off](arkts-form-formhost-off-f-sys.md)

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'formUninstall' | Yes | Event type. The value **'formUninstall'** indicates a widget uninstallation event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | No | Callback used to return the widget ID. If it is left unspecified, it indicates the callback for all the events that have been subscribed.<br> The value must be the same as that in **on('formUninstall')**. |
