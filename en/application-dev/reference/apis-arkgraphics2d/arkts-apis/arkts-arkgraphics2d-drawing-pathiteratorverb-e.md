# PathIteratorVerb

```TypeScript
enum PathIteratorVerb
```

Enumerates the path operation types contained in an iterator. It is used to read path operation instructions.

**Since:** 18

<!--Device-drawing-enum PathIteratorVerb--><!--Device-drawing-enum PathIteratorVerb-End-->

**System capability:** SystemCapability.Graphics.Drawing

## CLOSE

```TypeScript
CLOSE = 5
```

Closes a path.

**Since:** 18

<!--Device-PathIteratorVerb-CLOSE = 5--><!--Device-PathIteratorVerb-CLOSE = 5-End-->

**System capability:** SystemCapability.Graphics.Drawing

## CONIC

```TypeScript
CONIC = 3
```

Adds a conic curve.

**Since:** 18

<!--Device-PathIteratorVerb-CONIC = 3--><!--Device-PathIteratorVerb-CONIC = 3-End-->

**System capability:** SystemCapability.Graphics.Drawing

## CUBIC

```TypeScript
CUBIC = 4
```

Adds a cubic Bezier curve for smooth transitions.

**Since:** 18

<!--Device-PathIteratorVerb-CUBIC = 4--><!--Device-PathIteratorVerb-CUBIC = 4-End-->

**System capability:** SystemCapability.Graphics.Drawing

## DONE

```TypeScript
DONE = CLOSE + 1
```

The path setting is complete.

**Since:** 18

<!--Device-PathIteratorVerb-DONE = CLOSE + 1--><!--Device-PathIteratorVerb-DONE = CLOSE + 1-End-->

**System capability:** SystemCapability.Graphics.Drawing

## LINE

```TypeScript
LINE = 1
```

Adds a line segment.

**Since:** 18

<!--Device-PathIteratorVerb-LINE = 1--><!--Device-PathIteratorVerb-LINE = 1-End-->

**System capability:** SystemCapability.Graphics.Drawing

## MOVE

```TypeScript
MOVE = 0
```

Sets the start point.

**Since:** 18

<!--Device-PathIteratorVerb-MOVE = 0--><!--Device-PathIteratorVerb-MOVE = 0-End-->

**System capability:** SystemCapability.Graphics.Drawing

## QUAD

```TypeScript
QUAD = 2
```

Adds a quadratic Bezier curve for smooth transitions.

**Since:** 18

<!--Device-PathIteratorVerb-QUAD = 2--><!--Device-PathIteratorVerb-QUAD = 2-End-->

**System capability:** SystemCapability.Graphics.Drawing
