# Path2D

2D path object for path drawing

**继承/实现关系：** Path2D extends [CanvasPath](canvas-canvaspath-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class Path2D extends CanvasPath--><!--Device-unnamed-export declare class Path2D extends CanvasPath-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addPath

```TypeScript
addPath(path: Path2D, transform?: Matrix2D): void
```

Adds a path according to the specified path variable.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-addPath(path: Path2D, transform?: Matrix2D): void--><!--Device-Path2D-addPath(path: Path2D, transform?: Matrix2D): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Indicates the path object to be added. |
| transform | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Transformation matrix of the new trail. The default value is null. |

## constructor

```TypeScript
constructor()
```

Create an empty path object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-constructor()--><!--Device-Path2D-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(unit: LengthMetricsUnit)
```

Create an empty path object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-constructor(unit: LengthMetricsUnit)--><!--Device-Path2D-constructor(unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the unit mode |

## constructor

```TypeScript
constructor(path: Path2D)
```

Create a copy of a path object

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-constructor(path: Path2D)--><!--Device-Path2D-constructor(path: Path2D)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Path object to be copied |

## constructor

```TypeScript
constructor(path: Path2D, unit: LengthMetricsUnit)
```

Create a copy of a path object

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-constructor(path: Path2D, unit: LengthMetricsUnit)--><!--Device-Path2D-constructor(path: Path2D, unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Path object to be copied |
| unit | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the unit mode |

## constructor

```TypeScript
constructor(d: string)
```

Create a new path according to the description.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-constructor(d: string)--><!--Device-Path2D-constructor(d: string)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| d | string | 是 | Indicates the path string that compiles with the SVG path description specifications. |

## constructor

```TypeScript
constructor(description: string, unit: LengthMetricsUnit)
```

Create a new path according to the description.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Path2D-constructor(description: string, unit: LengthMetricsUnit)--><!--Device-Path2D-constructor(description: string, unit: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string | 是 | Indicates the path string that compiles with the SVG path description specifications. |
| unit | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | the unit mode |

