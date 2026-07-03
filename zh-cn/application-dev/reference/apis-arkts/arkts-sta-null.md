# Null
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供`Null`类型的运行时占位类。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## Null

export final class Null

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

表示`null`值对应的运行时类型。应用代码通常通过`null`字面量使用该能力，无需直接构造该类。

**示例：**

```ts
const value: null = null;
console.info(value == null); // true
```
