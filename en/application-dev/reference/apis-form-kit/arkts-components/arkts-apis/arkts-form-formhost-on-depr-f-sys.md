# on (System API)

## Modules to Import

```TypeScript
```

## on('formUninstall')

```TypeScript
function on(type: 'formUninstall', callback: Callback<string>): void
```

Subscribes to widget uninstall events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Widget uninstall is different from widget removal. When an application is uninstalled, the corresponding widget
> is automatically uninstalled.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-form-formhost-on-f-sys.md)

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'formUninstall' | Yes | Event type. The value **'formUninstall'** indicates a widget uninstallation event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Callback used to return the widget ID. |
