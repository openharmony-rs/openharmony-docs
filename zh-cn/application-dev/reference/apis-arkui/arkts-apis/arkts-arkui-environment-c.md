# Environment

Environment具体使用说明，详见[Environment(设备环境查询)](../../../ui/state-management/arkts-environment.md)

## 内置环境变量说明

| key | 类型 | 说明 |  
| -------------------- | --------------- | ------------------------------------------------------------ |  
| accessibilityEnabled | string | 无障碍屏幕朗读是否启用。当无法获取环境变量中的accessibilityEnabled的值时，将通过envProp、envProps等接口传入的开发者指定的默认值添加到AppStorage中。 |  
| colorMode | [ColorMode](arkts-arkui-colormode-e.md) | 深浅色模式，可选值为：<br/>- ColorMode.LIGHT：浅色模式；<br/>- ColorMode.DARK：深色模式。 |  
| fontScale | number | 字体大小比例。 |  
| fontWeightScale | number | 字重比例。 |  
| layoutDirection | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | 布局方向类型，可选值为：<br/>- LayoutDirection.LTR：从左到右；<br/>- LayoutDirection.RTL：从右到左。<br/>- Auto：跟随系统。 |  
| languageCode | string | 当前系统语言，小写字母，例如zh。

**起始版本：** 7

<!--Device-unnamed-declare class Environment--><!--Device-unnamed-declare class Environment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EnvProp

```TypeScript
static EnvProp<S>(key: string, value: S): boolean
```

将[Environment](../../../ui/state-management/arkts-environment.md)的内置环境变量key存入[AppStorage](../../../ui/state-management/arkts-appstorage.md)中。如果系统中未查询到Environment环境变量key的值，则使用默认值value，存入成功，返回true。如果AppStorage中已经有对应的key，则返回false。

所以建议在程序启动的时候调用该接口。

在没有调用EnvProp的情况下，就使用AppStorage读取环境变量是错误的。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [envProp](arkts-arkui-environment-c.md#envprop)

<!--Device-Environment-static EnvProp<S>(key: string, value: S): boolean--><!--Device-Environment-static EnvProp<S>(key: string, value: S): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见[内置环境变量说明](arkts-arkui-environment-c.md)。 |
| value | S | 是 | 查询不到环境变量key，则使用value作为默认值存入AppStorage中。 |

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

和[EnvProp](arkts-arkui-environment-c.md#envprop)类似，不同点在于参数为数组，可以一次性初始化多个数据。建议在应用启动时调用，将系统环境变量批量存入[AppStorage](../../../ui/state-management/arkts-appstorage.md)中。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [envProps](arkts-arkui-environment-c.md#envprops)

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

**废弃版本：** 10

**替代接口：** [keys](arkts-arkui-environment-c.md#keys)

<!--Device-Environment-static Keys(): Array<string>--><!--Device-Environment-static Keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回关联的系统项数组。 |

## envProp

```TypeScript
static envProp<S>(key: string, value: S): boolean
```

将[Environment](../../../ui/state-management/arkts-environment.md)的内置环境变量key存入[AppStorage](../../../ui/state-management/arkts-appstorage.md)中。如果系统中未查询到Environment环境变量key的值，则使用默认值value，存入成功，返回true。如果AppStorage中已经有对应的key，则返回false。

所以建议在程序启动的时候调用该接口。

在没有调用envProp的情况下，就使用AppStorage读取环境变量是错误的。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Environment-static envProp<S>(key: string, value: S): boolean--><!--Device-Environment-static envProp<S>(key: string, value: S): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见[内置环境变量说明](arkts-arkui-environment-c.md)。 |
| value | S | 是 | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

## envProps

```TypeScript
static envProps(props: EnvPropsOptions[]): void
```

和[envProp](arkts-arkui-environment-c.md#envprop)类似，不同点在于参数为数组，可以一次性初始化多个数据。建议在应用启动时调用，将系统环境变量批量存入[AppStorage](../../../ui/state-management/arkts-appstorage.md)中。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Environment-static envProps(props: EnvPropsOptions[]): void--><!--Device-Environment-static envProps(props: EnvPropsOptions[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | [EnvPropsOptions](arkts-arkui-envpropsoptions-i.md)[] | 是 | 系统环境变量和默认值的键值对的数组。 |

## keys

```TypeScript
static keys(): Array<string>
```

返回环境变量的属性key的数组。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Environment-static keys(): Array<string>--><!--Device-Environment-static keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回关联的系统项数组。 |

