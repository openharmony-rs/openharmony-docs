# Environment

```TypeScript
declare class Environment
```

Provides the capability to query device environment states. It can inject system environment variables (such as the dark/light mode, language, font scale, and layout direction) into AppStorage, enabling applications to perceive and respond to device environment changes. For details about how to use it on the UI, see [Environment: Device Environment Query](../../../ui/state-management/arkts-environment.md).

**Since:** 7

<!--Device-unnamed-declare class Environment--><!--Device-unnamed-declare class Environment-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Built-in Environment Variables

| key | Type | Description |  
| -------------------- | --------------- | ------------------------------------------------------------ |  
| accessibilityEnabled | string | Whether to enable accessibility. If there is no value of **accessibilityEnabled** in the environment variables, the default value passed through APIs such as **envProp** and **envProps** is added to AppStorage.|
| colorMode | [ColorMode](arkts-arkui-colormode-e.md) | Color mode. The options are as follows:<br> - **ColorMode.LIGHT**: light mode.<br> - **ColorMode.DARK**: dark mode. |
| fontScale | number | Font scale. |
| fontWeightScale | number | Font weight ratio. |
| layoutDirection | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | Layout direction. The options are as follows:<br> - **LayoutDirection.LTR**: left to right;<br> - **LayoutDirection.RTL**: right to left;<br> - **LayoutDirection.Auto**: follows the system settings. |
| languageCode | string | Current system language, which is in lowercase letters, for example, **zh**. |

## envProp

```TypeScript
static envProp<S>(key: string, value: S): boolean
```

Stores the built-in environment variable key of [Environment](../../../ui/state-management/arkts-environment.md) into [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of the environment variable key is not found in AppStorage, the default value is used and stored in AppStorage. If the value is successfully stored, **true** is returned. If the value of the environment variable key already exists in AppStorage, **false** is returned.

If **envProp** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Environment-static envProp<S>(key: string, value: S): boolean--><!--Device-Environment-static envProp<S>(key: string, value: S): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Environment variable name. For details about the value range, see [Built-in Environment Variables](#built-in-environment-variables). |
| value | S | Yes | Default value used if the value of the environment variable key is not found in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **false** if the property corresponding to the key exists in AppStorage; creates a property with the key and the default value and returns **true** otherwise. |

**Examples**

For details about how to use envProp, see [Accessing Environment Parameters from the UI](../../../ui/state-management/arkts-environment.md#accessing-environment-parameters-from-the-ui).

## envProps

```TypeScript
static envProps(props: EnvPropsOptions[]): void
```

Works in a way similar to the [envProp](#envprop) API, with the difference that it allows for initialization of multiple properties in batches. If **envProps** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup to store system environment variables in batches into [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Environment-static envProps(props: EnvPropsOptions[]): void--><!--Device-Environment-static envProps(props: EnvPropsOptions[]): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| props | [EnvPropsOptions](arkts-arkui-envpropsoptions-i.md)[] | Yes | Array of key-value pairs consisting of system environment variables and default values. |

**Examples**

```TypeScript
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

## keys

```TypeScript
static keys(): Array<string>
```

Returns the property key array of environment variables.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Environment-static keys(): Array<string>--><!--Device-Environment-static keys(): Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of property keys of environment variables. |

**Examples**

```TypeScript
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.keys(); // keys contains accessibilityEnabled, languageCode, and prop.
```

## EnvProp

```TypeScript
static EnvProp<S>(key: string, value: S): boolean
```

Stores the built-in environment variable key of [Environment](../../../ui/state-management/arkts-environment.md) into [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of the environment variable key is not found in AppStorage, the default value is used and stored in AppStorage. If the value is successfully stored, **true** is returned. If the value of the environment variable key already exists in AppStorage, **false** is returned.

If **EnvProp** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [envProp](#envprop)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Environment-static EnvProp<S>(key: string, value: S): boolean--><!--Device-Environment-static EnvProp<S>(key: string, value: S): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Environment variable name. For details about the value range, see [Built-in Environment Variables](#built-in-environment-variables). |
| value | S | Yes | Default value used if the value of the environment variable key is not found in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **false** if the property corresponding to the key exists in AppStorage; creates a property with the key and the default value and returns **true** otherwise. |

**Examples**

```TypeScript
Environment.EnvProp('accessibilityEnabled', 'default');
```

## EnvProps

```TypeScript
static EnvProps(
    props: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

Works in a way similar to the [EnvProp](#envprop) API, with the difference that it allows for initialization of multiple properties in batches. If **EnvProps** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup to store system environment variables in batches into [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [envProps](#envprops)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Environment-static EnvProps(    props: {      key: string;      defaultValue: any;    }[],  ): void--><!--Device-Environment-static EnvProps(    props: {      key: string;      defaultValue: any;    }[],  ): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| props | {       key: string;       defaultValue: any;     }[] | Yes | Array of key-value pairs consisting of system environment variables and default values. |

**Examples**

```TypeScript
Environment.EnvProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

## Keys

```TypeScript
static Keys(): Array<string>
```

Returns the property key array of environment variables.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [keys](#keys)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Environment-static Keys(): Array<string>--><!--Device-Environment-static Keys(): Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Array of property keys of environment variables. |

**Examples**
