# Environment

Environment提供设备环境状态的查询能力，可将系统环境变量（如深浅色模式、语言、字体缩放、布局方向等）注入AppStorage，使应用能够感知和响应设备环境变化。具体UI使用说明，详见 [Environment：设备环境查询](../../../ui/state-management/arkts-environment.md)。

## 内置环境变量说明

| key | 类型 | 说明 | | -------------------- | --------------- | ------------------------------------------------------------ | | accessibilityEnabled | string | 无障碍屏幕朗读是否启用。当无法获取环境变量中的accessibilityEnabled的值时，将通过envProp、envProps等接口传入的开发者指定的默认值添加到AppStorage中。 | | colorMode | ColorMode | 深浅色模式，可选值为：  
- **ColorMode.LIGHT：浅色模式**；  
- **ColorMode.DARK**：深色模式。 | | fontScale | number | 字体大小比例。 | | fontWeightScale | number | 字重比例。 | | layoutDirection | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | 布局方向类型，可选值为：  
- **LayoutDirection.LTR**：从左到右；  
- **LayoutDirection.RTL**：从右到左；  
- **LayoutDirection.Auto**：跟随系统。 | | languageCode | string | 当前系统语言，小写字母，例如zh。 |

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## EnvProp

```TypeScript
static EnvProp<S>(key: string, value: S): boolean
```

将[Environment](../../../ui/state-management/arkts-environment.md)的内置环境变量key存入 [AppStorage](../../../ui/state-management/arkts-appstorage.md)中。如果系统中未查询到Environment环境变量key的值，则使用默认值value存入 AppStorage并返回true。如果AppStorage中已经有对应的key，则返回false。在没有调用EnvProp的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环境变量值。建议在应用启动时调用该接口。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [envProp](#envprop)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见[内置环境变量说明](#内置环境变量说明)。 |
| value | S | 是 | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

**示例**

```TypeScript
Environment.EnvProp('accessibilityEnabled', 'default');
```

## envProp

```TypeScript
static envProp<S>(key: string, value: S): boolean
```

将[Environment](../../../ui/state-management/arkts-environment.md)的内置环境变量key存入 [AppStorage](../../../ui/state-management/arkts-appstorage.md)中。如果系统中未查询到Environment环境变量key的值，则使用默认值value存入 AppStorage并返回true。如果AppStorage中已经有对应的key，则返回false。在没有调用envProp的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环境变量值。建议在应用启动时调用该接口。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见[内置环境变量说明](#内置环境变量说明)。 |
| value | S | 是 | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

**示例**

envProp具体使用，详见[从UI中访问Environment参数](../../../ui/state-management/arkts-environment.md#从ui中访问environment参数)。

## EnvProps

```TypeScript
static EnvProps(
    props: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

和[EnvProp](#envprop)功能类似，不同点在于参数为数组，可以一次性初始化多个数据。在没有调用EnvProps的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环 境变量值。建议在应用启动时调用，将系统环境变量批量存入[AppStorage](../../../ui/state-management/arkts-appstorage.md)中。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [envProps](#envprops)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | {       key: string;       defaultValue: any;     }[] | 是 |  |

**示例**

```TypeScript
Environment.EnvProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

## envProps

```TypeScript
static envProps(props: EnvPropsOptions[]): void
```

和[envProp](#envprop)功能类似，不同点在于参数为数组，可以一次性初始化多个数据。在没有调用envProps的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环 境变量值。建议在应用启动时调用，将系统环境变量批量存入[AppStorage](../../../ui/state-management/arkts-appstorage.md)中。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | [EnvPropsOptions](arkts-arkui-envpropsoptions-i.md)[] | 是 | 系统环境变量和默认值的键值对的数组。 |

**示例**

```TypeScript
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

## Keys

```TypeScript
static Keys(): Array<string>
```

返回环境变量的属性key的数组。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [keys](#keys)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回环境变量的属性key的数组。 |

**示例**

```TypeScript
let keys: Array<string> = PersistentStorage.Keys();
```

```TypeScript
Environment.EnvProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.Keys(); // keys 包含 accessibilityEnabled、languageCode、prop
```

## keys

```TypeScript
static keys(): Array<string>
```

返回环境变量的属性key的数组。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回环境变量的属性key的数组。 |

**示例**

```TypeScript
let keys: Array<string> = PersistentStorage.keys();
```

```TypeScript
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.keys(); // keys 包含 accessibilityEnabled、languageCode、prop
```
