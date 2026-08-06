# Environment

Environment提供设备环境状态的查询能力，可将系统环境变量（如深浅色模式、语言、字体缩放、布局方向等）注入AppStorage，使应用能够感知和响应设备环境变化。具体UI使用说明，详见 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

## 内置环境变量说明 | key                  | 类型            | 说明                                                         | | -------------------- | --------------- | ------------------------------------------------------------ | | accessibilityEnabled | string          | 无障碍屏幕朗读是否启用。当无法获取环境变量中的accessibilityEnabled的值时，将通过envProp、envProps等接口传入的开发者指定的默认值添加到AppStorage中。 | | colorMode            | [ColorMode](arkts-arkui-colormode-e.md)       | 深浅色模式，可选值为：<br>- **ColorMode.LIGHT：浅色模式**；<br>- **ColorMode.DARK**：深色模式。 | | fontScale            | number          | 字体大小比例。                                               | | fontWeightScale      | number          | 字重比例。                                                   | | layoutDirection      | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | 布局方向类型，可选值为：<br>- **LayoutDirection.LTR**：从左到右；<br>- **LayoutDirection.RTL**：从右到左；<br>- **LayoutDirection.Auto**：跟随系统。 | | languageCode         | string          | 当前系统语言，小写字母，例如zh。                             |

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-declare class Environment--><!--Device-unnamed-declare class Environment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EnvProp

```TypeScript
static EnvProp<S>(key: string, value: S): boolean
```

将\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的内置环境变量key存入 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中。如果系统中未查询到Environment环境变量key的值，则使用默认值value存入 AppStorage并返回true。如果AppStorage中已经有对应的key，则返回false。 在没有调用EnvProp的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环境变量值。建议在应用启动时调用该接口。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [Environment#envProp](arkts-arkui-environment-c.md#envprop)

<!--Device-Environment-static EnvProp<S>(key: string, value: S): boolean--><!--Device-Environment-static EnvProp<S>(key: string, value: S): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见[内置环境变量说明]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| value | S | 是 | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

## EnvProps

```TypeScript
static EnvProps(
    props: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

和[EnvProp]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_功能类似，不同点在于参数为数组，可以一次性初始化多个数据。在没有调用EnvProps的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环 境变量值。建议在应用启动时调用，将系统环境变量批量存入\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [Environment#envProps](arkts-arkui-environment-c.md#envprops)

<!--Device-Environment-static EnvProps(    props: {      key: string;      defaultValue: any;    }[],  ): void--><!--Device-Environment-static EnvProps(    props: {      key: string;      defaultValue: any;    }[],  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | {       key: string;       defaultValue: any;     }[] | 是 |  |

## Keys

```TypeScript
static Keys(): Array<string>
```

返回环境变量的属性key的数组。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [Environment#keys](arkts-arkui-environment-c.md#keys)

<!--Device-Environment-static Keys(): Array<string>--><!--Device-Environment-static Keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回环境变量的属性key的数组。 |

## envProp

```TypeScript
static envProp<S>(key: string, value: S): boolean
```

将\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的内置环境变量key存入 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中。如果系统中未查询到Environment环境变量key的值，则使用默认值value存入 AppStorage并返回true。如果AppStorage中已经有对应的key，则返回false。 在没有调用envProp的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环境变量值。建议在应用启动时调用该接口。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Environment-static envProp<S>(key: string, value: S): boolean--><!--Device-Environment-static envProp<S>(key: string, value: S): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见[内置环境变量说明]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| value | S | 是 | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

## envProps

```TypeScript
static envProps(props: EnvPropsOptions[]): void
```

和[envProp]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_功能类似，不同点在于参数为数组，可以一次性初始化多个数据。在没有调用envProps的情况下，直接使用AppStorage读取环境变量，将无法获取到对应的环 境变量值。建议在应用启动时调用，将系统环境变量批量存入\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Environment-static envProps(props: EnvPropsOptions[]): void--><!--Device-Environment-static envProps(props: EnvPropsOptions[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 是 | 系统环境变量和默认值的键值对的数组。 |

## keys

```TypeScript
static keys(): Array<string>
```

返回环境变量的属性key的数组。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Environment-static keys(): Array<string>--><!--Device-Environment-static keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回环境变量的属性key的数组。 |

