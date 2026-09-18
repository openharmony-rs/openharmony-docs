# VertexMode

Enumerates the connection modes for vertex drawing.

**Since:** 23

**System capability:** SystemCapability.Graphics.Drawing

## TRIANGLES_VERTEXMODE

```TypeScript
TRIANGLES_VERTEXMODE = 0
```

Every three vertices come from different triangles.

**Since:** 23

**System capability:** SystemCapability.Graphics.Drawing

## TRIANGLESSTRIP_VERTEXMODE

```TypeScript
TRIANGLESSTRIP_VERTEXMODE = 1
```

Consecutive triangles share one edge. It is efficient for continuous surfaces.

**Since:** 23

**System capability:** SystemCapability.Graphics.Drawing

## TRIANGLESFAN_VERTEXMODE

```TypeScript
TRIANGLESFAN_VERTEXMODE = 2
```

All triangles share one vertex. It is suitable for circles and sectors.

**Since:** 23

**System capability:** SystemCapability.Graphics.Drawing
