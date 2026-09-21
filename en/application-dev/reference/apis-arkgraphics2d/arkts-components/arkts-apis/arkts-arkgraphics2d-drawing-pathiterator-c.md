# PathIterator

```TypeScript
class PathIterator
```

Implements a path operation iterator. You can read path operation instructions by traversing the iterator.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 18.
> 
> - This module uses the physical pixel unit, px.
> 
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor(path: Path)
```

Creates an iterator and binds it with a path.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | Yes | **Path** object bound to the iterator. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
let iter: drawing.PathIterator = new drawing.PathIterator(path);
console.info('PathIterator created successfully');
```

## hasNext

```TypeScript
hasNext(): boolean
```

Checks whether there is any next operation in the path operation iterator.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** means yes; **false** otherwise. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
let iter: drawing.PathIterator = new drawing.PathIterator(path);
let res = iter.hasNext();
```

## next

```TypeScript
next(points: Array<common2D.Point>, offset?: number): PathIteratorVerb
```

Retrieves the next operation in this path and moves the iterator to that operation.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| points | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | Array of coordinate points. The array length must be at least the offset plus 4 to ensure that the array can hold all types of path data. After the operation is executed, this array is overwritten. The number of coordinate points to be filled depends on the operation type. Specifically, for **MOVE**, fill one coordinate; for **LINE**, fill two coordinates; for **QUAD**, fill three coordinates; for **CONIC**, fill three coordinates and one weight value (a total of 3.5 groups); for **CUBIC**, fill four coordinates; for **CLOSE** and **DONE**, do not fill any coordinate points. |
| offset | number | No | Offset from the start of the array where writing begins. The default value is **0**. The value range is [0, size - 4], where **size** is the length of the coordinate point array. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | Path operation type contained in the iterator. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(10, 20);
let iter: drawing.PathIterator = new drawing.PathIterator(path);
let verbStr: Array<string> = ['MOVE', 'LINE', 'QUAD', 'CONIC', 'CUBIC', 'CLOSE', 'DONE'];
let pointCount: Array<number> = [1, 2, 3, 4, 4, 0, 0];
let points: Array<common2D.Point> = [{x: 0, y: 0}, {x: 0, y: 0}, {x: 0, y: 0}, {x: 0, y: 0}];
let offset = 0;
let verb = iter.next(points, offset);
let outputMessage: string = 'pathIteratorNext: ';
outputMessage += 'verb =' + verbStr[verb] + '; has ' + pointCount[verb] + ' pairs: ';
for (let j = 0; j < pointCount[verb] + offset; j++) {
  outputMessage += '[' + points[j].x + ', ' + points[j].y + ']';
}
console.info(outputMessage);
```

## peek

```TypeScript
peek(): PathIteratorVerb
```

Retrieves the next operation in this path, without moving the iterator.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [PathIteratorVerb](arkts-arkgraphics2d-drawing-pathiteratorverb-e.md) | Path operation type contained in the iterator. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
let iter: drawing.PathIterator = new drawing.PathIterator(path);
let res = iter.peek();
```
