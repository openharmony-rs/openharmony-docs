# Environment

Environment具体使用说明，详见[Environment(设备环境查询)](../../../ui/state-management/arkts-environment.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class Environment--><!--Device-unnamed-export declare class Environment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## envProp

```TypeScript
static envProp<T>(key: string, value: T): boolean
```

将[Environment](../../../ui/state-management/arkts-environment.md)的内置环境变量key 存入AppStorage中。 如果系统中未查询到Environment环境变量key的值，则使用默认值value，存入成功，返回true。如果AppStorage中已经有对应的key，则返回false。 所以建议在程序启动的时候调用该接口。 在没有调用envProp的情况下，就使用AppStorage读取环境变量是错误的。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Environment-static envProp<T>(key: string, value: T): boolean--><!--Device-Environment-static envProp<T>(key: string, value: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 环境变量名称，支持的范围详见内置环境变量说明。 |
| value | T | 是 | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

## envProps

```TypeScript
static envProps(props: EnvPropsOptions[]): void
```

和[envProp](#envProp)类似，不同点在于参数为数组，可以一次性初始化多个数据。 建议在应用启动时调用，将系统环境变量批量存入AppStorage中。 需注意的是，如果传入的dafultValue为 ColorMode、 LayoutDirection类型， 或是数字，则需额外指定其具体类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Environment-static envProps(props: EnvPropsOptions[]): void--><!--Device-Environment-static envProps(props: EnvPropsOptions[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | [EnvPropsOptions](arkts-na-environment-envpropsoptions-i.md)[] | 是 | 系统环境变量和默认值的键值对的数组。 |

## keys

```TypeScript
static keys(): Array<string>
```

返回环境变量的属性key的数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Environment-static keys(): Array<string>--><!--Device-Environment-static keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回关联的系统项数组。 |

