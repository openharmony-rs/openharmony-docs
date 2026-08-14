# PathIterator

表示路径操作迭代器，可通过遍历迭代器逐段读取路径的操作指令。 迭代器按顺序遍历路径中的操作指令，便于实现对路径的细粒度分析与自定义处理。 > **说明：** > > - 本Class首批接口从API version 18开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-class PathIterator--><!--Device-drawing-class PathIterator-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## constructor

```TypeScript
constructor(path: Path)
```

构造迭代器并绑定路径。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathIterator-constructor(path: Path)--><!--Device-PathIterator-constructor(path: Path)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path | 是 | 迭代器绑定的路径对象，绑定后迭代器将遍历该路径中的操作指令， 可通过next、peek、hasNext等方法读取路径的操作类型和坐标数据。 |

## hasNext

```TypeScript
hasNext(): boolean
```

判断迭代器中是否还有下一个操作。通常与next()或peek()方法配合使用实现路径遍历。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathIterator-hasNext(): boolean--><!--Device-PathIterator-hasNext(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 迭代器是否还有下一个操作可遍历。true表示还有后续路径操作可读取，false表示已遍历至路径末尾，无更多操作。 |

## next

```TypeScript
next(points: Array<common2D.Point>, offset?: number): PathIteratorVerb
```

返回当前路径的下一个操作，并将迭代器推进至该操作，同时将路径坐标点数据按操作类型写入传入的points数组。 若仅需预览下一个操作而不改变迭代器状态，请使用[peek](#peek)。 通常与[hasNext](#hasNext)方法配合使用实现路径遍历。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-PathIterator-next(points: Array<common2D.Point>, offset?: number): PathIteratorVerb--><!--Device-PathIterator-next(points: Array<common2D.Point>, offset?: number): PathIteratorVerb-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| points | Array&lt;common2D.Point&gt; | 是 | 坐标点数组，长度必须至少为偏移量加4，以确保能容纳所有类型的路径数据。操作执行后，该数组会被覆盖。填入的坐标点数量取决于操作类型，其中， MOVE填入1个坐标点，LINE填入2个坐标点，QUAD填入3个坐标点，CONIC填入3个坐标点 + 1个权重值（共3.5组），CUBIC填入4个坐标点，CLOSE和DONE不填入任何点。 |
| offset | number | 否 | 数组中写入位置相对起始点的偏移量，默认为0，取值范围为[0, size-4]，size是指坐标点数组长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | 当前路径段的操作类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## next

```TypeScript
next(points: Array<common2D.Point>, offset?: int): PathIteratorVerb | undefined
```

返回当前路径的下一个操作，并将迭代器推进至该操作，同时将路径坐标点数据按操作类型写入传入的points数组。 若仅需预览下一个操作而不改变迭代器状态，请使用[peek](#peek)。 通常与[hasNext](#hasNext)方法配合使用实现路径遍历。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathIterator-next(points: Array<common2D.Point>, offset?: int): PathIteratorVerb | undefined--><!--Device-PathIterator-next(points: Array<common2D.Point>, offset?: int): PathIteratorVerb | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| points | Array&lt;common2D.Point&gt; | 是 | 坐标点数组，长度必须至少为偏移量加4，以确保能容纳所有类型的路径数据。操作执行后，该数组会被覆盖。填入的坐标点数量取决于操作类型，其中， MOVE填入1个坐标点，LINE填入2个坐标点，QUAD填入3个坐标点，CONIC填入3个坐标点 + 1个权重值（共3.5组），CUBIC填入4个坐标点，CLOSE和DONE不填入任何点。 |
| offset | int | 否 | 数组中写入位置相对起始点的偏移量，默认为0，取值范围为[0, size-4]，size是指坐标点数组长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | 当前路径段的操作类型。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## peek

```TypeScript
peek(): PathIteratorVerb
```

返回当前路径的下一个操作，迭代器保持在原操作。与next不同，peek不会推进迭代器位置。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-PathIterator-peek(): PathIteratorVerb--><!--Device-PathIterator-peek(): PathIteratorVerb-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | 当前路径段的操作类型。 |

## peek

```TypeScript
peek(): PathIteratorVerb | undefined
```

返回当前路径的下一个操作，迭代器保持在原操作。与next不同，peek不会推进迭代器位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathIterator-peek(): PathIteratorVerb | undefined--><!--Device-PathIterator-peek(): PathIteratorVerb | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | 当前路径段的操作类型。创建失败时返回undefined。 |

