# Chrono

用于时间测量和时钟访问的工具类。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export class Chrono--><!--Device-unnamed-export class Chrono-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## getCpuTime

```TypeScript
public static getCpuTime(): long
```

获取当前进程的CPU时间，单位为纳秒。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Chrono-public static getCpuTime(): long--><!--Device-Chrono-public static getCpuTime(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 当前进程消耗的CPU时间，单位为纳秒。 |

## milliNow

```TypeScript
public static milliNow(): double
```

获取当前时间戳，单位为毫秒。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Chrono-public static milliNow(): double--><!--Device-Chrono-public static milliNow(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 自系统启动以来经过的毫秒数。 |

## nanoNow

```TypeScript
public static nanoNow(): long
```

获取当前时间戳，单位为纳秒。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Chrono-public static nanoNow(): long--><!--Device-Chrono-public static nanoNow(): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 自系统启动以来经过的纳秒数。 |

## NS_PER_MS

```TypeScript
public static readonly NS_PER_MS: long = 1000000
```

一毫秒所包含的纳秒数。

**类型：** long

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Chrono-public static readonly NS_PER_MS: long = 1000000--><!--Device-Chrono-public static readonly NS_PER_MS: long = 1000000-End-->

**系统能力：** SystemCapability.Utils.Lang

