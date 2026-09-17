# configure

## Modules to Import

```TypeScript
```

## configure

```TypeScript
function configure(config: ConfigOption): boolean
```

Configures the application event logging function, such as setting the event logging switch and maximum size of the directory that stores the event logging files.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [configure](arkts-performanceanalysis-hiappevent-configure-f.md)

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | ConfigOption | Yes | Configuration items for application event logging. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the configuration is successful; returns **false** otherwise. |

**Examples**

```TypeScript
// Set the application event logging switch.
let config1: hiAppEvent.ConfigOption = {
  disable: true,
};
hiAppEvent.configure(config1);

// Configure the maximum size of the directory that stores the event logging files.
let config2: hiAppEvent.ConfigOption = {
  maxStorage: '100M',
};
hiAppEvent.configure(config2);
```
