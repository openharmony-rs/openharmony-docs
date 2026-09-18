# WebGL2RenderingContextBase

WebGL 2.0

**Since:** 7

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## beginQuery

```TypeScript
beginQuery(target: webgl.GLenum, query: WebGLQuery): void
```

Begins a query

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| query | [WebGLQuery](arkts-arkgraphics2d-webgl2-webglquery-i.md) | Yes | Query |

## beginTransformFeedback

```TypeScript
beginTransformFeedback(primitiveMode: webgl.GLenum): void
```

Begins transform feedback

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| primitiveMode | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Primitive mode |

## bindBufferBase

```TypeScript
bindBufferBase(target: webgl.GLenum, index: webgl.GLuint, buffer: webgl.WebGLBuffer | null): void
```

Binds buffer base

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Index |
| buffer | [webgl.WebGLBuffer](arkts-arkgraphics2d-webgl-webglbuffer-i.md) &#124; null | Yes | Buffer |

## bindBufferRange

```TypeScript
bindBufferRange(
      target: webgl.GLenum,
      index: webgl.GLuint,
      buffer: webgl.WebGLBuffer | null,
      offset: webgl.GLintptr,
      size: webgl.GLsizeiptr,
    ): void
```

Binds buffer range

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Index |
| buffer | [webgl.WebGLBuffer](arkts-arkgraphics2d-webgl-webglbuffer-i.md) &#124; null | Yes | Buffer |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |
| size | [webgl.GLsizeiptr](arkts-arkgraphics2d-glsizeiptr-t.md) | Yes | Size |

## bindSampler

```TypeScript
bindSampler(unit: webgl.GLuint, sampler: WebGLSampler | null): void
```

Binds a sampler

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unit | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Texture unit |
| sampler | [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) &#124; null | Yes | [Sampler](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-sampler-i.md) |

## bindTransformFeedback

```TypeScript
bindTransformFeedback(target: webgl.GLenum, tf: WebGLTransformFeedback | null): void
```

Binds a transform feedback

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| tf | [WebGLTransformFeedback](arkts-arkgraphics2d-webgl2-webgltransformfeedback-i.md) &#124; null | Yes | Transform feedback |

## bindVertexArray

```TypeScript
bindVertexArray(array: WebGLVertexArrayObject | null): void
```

Binds a vertex array

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| array | [WebGLVertexArrayObject](arkts-arkgraphics2d-webgl2-webglvertexarrayobject-i.md) &#124; null | Yes | Vertex array |

## blitFramebuffer

```TypeScript
blitFramebuffer(
      srcX0: webgl.GLint,
      srcY0: webgl.GLint,
      srcX1: webgl.GLint,
      srcY1: webgl.GLint,
      dstX0: webgl.GLint,
      dstY0: webgl.GLint,
      dstX1: webgl.GLint,
      dstY1: webgl.GLint,
      mask: webgl.GLbitfield,
      filter: webgl.GLenum,
    ): void
```

Blits framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcX0 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Source X0 |
| srcY0 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Source Y0 |
| srcX1 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Source X1 |
| srcY1 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Source Y1 |
| dstX0 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Destination X0 |
| dstY0 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Destination Y0 |
| dstX1 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Destination X1 |
| dstY1 | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Destination Y1 |
| mask | [webgl.GLbitfield](arkts-arkgraphics2d-glbitfield-t.md) | Yes | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) |
| filter | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Filter |

## clearBufferfi

```TypeScript
clearBufferfi(buffer: webgl.GLenum, drawbuffer: webgl.GLint, depth: webgl.GLfloat, stencil: webgl.GLint): void
```

Clears bufferfi

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer |
| drawbuffer | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Draw buffer |
| depth | [webgl.GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Depth |
| stencil | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Stencil |

## clearBufferfv

```TypeScript
clearBufferfv(
      buffer: webgl.GLenum,
      drawbuffer: webgl.GLint,
      values: webgl.Float32List,
      srcOffset?: webgl.GLuint,
    ): void
```

Clears bufferfv

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer |
| drawbuffer | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Draw buffer |
| values | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Values |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |

## clearBufferiv

```TypeScript
clearBufferiv(
      buffer: webgl.GLenum,
      drawbuffer: webgl.GLint,
      values: webgl.Int32List,
      srcOffset?: webgl.GLuint,
    ): void
```

Clears bufferiv

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer |
| drawbuffer | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Draw buffer |
| values | [webgl.Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Values |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |

## clearBufferuiv

```TypeScript
clearBufferuiv(buffer: webgl.GLenum, drawbuffer: webgl.GLint, values: Uint32List, srcOffset?: webgl.GLuint): void
```

Clears bufferuiv

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer |
| drawbuffer | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Draw buffer |
| values | [Uint32List](arkts-arkgraphics2d-uint32list-t.md) | Yes | Values |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |

## clientWaitSync

```TypeScript
clientWaitSync(sync: WebGLSync, flags: webgl.GLbitfield, timeout: GLuint64 ): webgl.GLenum
```

Client waits for sync object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sync | [WebGLSync](arkts-arkgraphics2d-webgl2-webglsync-i.md) | Yes | Sync object |
| flags | [webgl.GLbitfield](arkts-arkgraphics2d-glbitfield-t.md) | Yes | Flags |
| timeout | [GLuint64](arkts-arkgraphics2d-gluint64-t.md) | Yes | Timeout |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Result |

## compressedTexImage3D

```TypeScript
compressedTexImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      border: webgl.GLint,
      imageSize: webgl.GLsizei,
      offset: webgl.GLintptr,
    ): void
```

Compressed texture image 3D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| imageSize | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Image size |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

## compressedTexImage3D

```TypeScript
compressedTexImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      border: webgl.GLint,
      srcData: ArrayBufferView,
      srcOffset?: webgl.GLuint,
      srcLengthOverride?: webgl.GLuint,
    ): void
```

Compressed texture image 3D from ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLengthOverride | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length override |

## compressedTexSubImage3D

```TypeScript
compressedTexSubImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      zoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      format: webgl.GLenum,
      imageSize: webgl.GLsizei,
      offset: webgl.GLintptr,
    ): void
```

Compressed texture sub image 3D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| zoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| imageSize | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Image size |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

## compressedTexSubImage3D

```TypeScript
compressedTexSubImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      zoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      format: webgl.GLenum,
      srcData: ArrayBufferView,
      srcOffset?: webgl.GLuint,
      srcLengthOverride?: webgl.GLuint,
    ): void
```

Compressed texture sub image 3D from ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| zoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLengthOverride | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length override |

## copyBufferSubData

```TypeScript
copyBufferSubData(
      readTarget: webgl.GLenum,
      writeTarget: webgl.GLenum,
      readOffset: webgl.GLintptr,
      writeOffset: webgl.GLintptr,
      size: webgl.GLsizeiptr,
    ): void
```

Copies data from one buffer to another

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| readTarget | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Read buffer target |
| writeTarget | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Write buffer target |
| readOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Read offset |
| writeOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Write offset |
| size | [webgl.GLsizeiptr](arkts-arkgraphics2d-glsizeiptr-t.md) | Yes | Size to copy |

## copyTexSubImage3D

```TypeScript
copyTexSubImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      zoffset: webgl.GLint,
      x: webgl.GLint,
      y: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
    ): void
```

Copies a portion of a 3D texture image

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| zoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z offset |
| x | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |

## createQuery

```TypeScript
createQuery(): WebGLQuery | null
```

Creates a query

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLQuery](arkts-arkgraphics2d-webgl2-webglquery-i.md) &#124; null | The created query |

## createSampler

```TypeScript
createSampler(): WebGLSampler | null
```

Creates a sampler

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) &#124; null | The created sampler |

## createTransformFeedback

```TypeScript
createTransformFeedback(): WebGLTransformFeedback | null
```

Creates a transform feedback object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLTransformFeedback](arkts-arkgraphics2d-webgl2-webgltransformfeedback-i.md) &#124; null | The created transform feedback |

## createVertexArray

```TypeScript
createVertexArray(): WebGLVertexArrayObject | null
```

Creates a vertex array object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLVertexArrayObject](arkts-arkgraphics2d-webgl2-webglvertexarrayobject-i.md) &#124; null | The created vertex array object |

## deleteQuery

```TypeScript
deleteQuery(query: WebGLQuery | null): void
```

Deletes a query

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [WebGLQuery](arkts-arkgraphics2d-webgl2-webglquery-i.md) &#124; null | Yes | Query to delete |

## deleteSampler

```TypeScript
deleteSampler(sampler: WebGLSampler | null): void
```

Deletes a sampler

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sampler | [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) &#124; null | Yes | Sampler to delete |

## deleteSync

```TypeScript
deleteSync(sync: WebGLSync | null): void
```

Deletes a sync object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sync | [WebGLSync](arkts-arkgraphics2d-webgl2-webglsync-i.md) &#124; null | Yes | Sync object to delete |

## deleteTransformFeedback

```TypeScript
deleteTransformFeedback(tf: WebGLTransformFeedback | null): void
```

Deletes a transform feedback object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tf | [WebGLTransformFeedback](arkts-arkgraphics2d-webgl2-webgltransformfeedback-i.md) &#124; null | Yes | Transform feedback to delete |

## deleteVertexArray

```TypeScript
deleteVertexArray(vertexArray: WebGLVertexArrayObject | null): void
```

Deletes a vertex array object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vertexArray | [WebGLVertexArrayObject](arkts-arkgraphics2d-webgl2-webglvertexarrayobject-i.md) &#124; null | Yes | Vertex array to delete |

## drawArraysInstanced

```TypeScript
drawArraysInstanced(
      mode: webgl.GLenum,
      first: webgl.GLint,
      count: webgl.GLsizei,
      instanceCount: webgl.GLsizei,
    ): void
```

Draws arrays instanced

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Mode](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-agent-mode-e.md) |
| first | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | First |
| count | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Count |
| instanceCount | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Instance count |

## drawBuffers

```TypeScript
drawBuffers(buffers: webgl.GLenum[]): void
```

Sets draw buffers

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffers | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)[] | Yes | Buffers |

## drawElementsInstanced

```TypeScript
drawElementsInstanced(
      mode: webgl.GLenum,
      count: webgl.GLsizei,
      type: webgl.GLenum,
      offset: webgl.GLintptr,
      instanceCount: webgl.GLsizei,
    ): void
```

Draws elements instanced

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Mode](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-agent-mode-e.md) |
| count | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Count |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |
| instanceCount | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Instance count |

## drawRangeElements

```TypeScript
drawRangeElements(
      mode: webgl.GLenum,
      start: webgl.GLuint,
      end: webgl.GLuint,
      count: webgl.GLsizei,
      type: webgl.GLenum,
      offset: webgl.GLintptr,
    ): void
```

Draws range elements

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Mode](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-agent-mode-e.md) |
| start | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Start |
| end | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | End |
| count | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Count |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

## endQuery

```TypeScript
endQuery(target: webgl.GLenum): void
```

Ends a query

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |

## endTransformFeedback

```TypeScript
endTransformFeedback(): void
```

Ends transform feedback

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## fenceSync

```TypeScript
fenceSync(condition: webgl.GLenum, flags: webgl.GLbitfield): WebGLSync | null
```

Creates a sync object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| condition | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Condition |
| flags | [webgl.GLbitfield](arkts-arkgraphics2d-glbitfield-t.md) | Yes | Flags |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLSync](arkts-arkgraphics2d-webgl2-webglsync-i.md) &#124; null | The created sync object |

## framebufferTextureLayer

```TypeScript
framebufferTextureLayer(
      target: webgl.GLenum,
      attachment: webgl.GLenum,
      texture: webgl.WebGLTexture | null,
      level: webgl.GLint,
      layer: webgl.GLint,
    ): void
```

Attaches a texture layer to a framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Framebuffer target |
| attachment | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Attachment point |
| texture | [webgl.WebGLTexture](arkts-arkgraphics2d-webgl-webgltexture-i.md) &#124; null | Yes | Texture |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| layer | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Layer |

## getActiveUniformBlockName

```TypeScript
getActiveUniformBlockName(program: webgl.WebGLProgram, uniformBlockIndex: webgl.GLuint): string | null
```

Gets active uniform block name

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| uniformBlockIndex | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Uniform block index |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Uniform block name |

## getActiveUniformBlockParameter

```TypeScript
getActiveUniformBlockParameter(
      program: webgl.WebGLProgram,
      uniformBlockIndex: webgl.GLuint,
      pname: webgl.GLenum,
    ): any
```

Gets active uniform block parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| uniformBlockIndex | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Uniform block index |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getActiveUniforms

```TypeScript
getActiveUniforms(program: webgl.WebGLProgram, uniformIndices: webgl.GLuint[], pname: webgl.GLenum): any
```

Gets active uniforms

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| uniformIndices | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md)[] | Yes | Uniform indices |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getBufferSubData

```TypeScript
getBufferSubData(
      target: webgl.GLenum,
      srcByteOffset: webgl.GLintptr,
      dstBuffer: ArrayBufferView,
      dstOffset?: webgl.GLuint,
      length?: webgl.GLuint,
    ): void
```

Gets buffer sub data

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| srcByteOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Source byte offset |
| dstBuffer | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Destination buffer |
| dstOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Destination offset |
| length | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) |

## getFragDataLocation

```TypeScript
getFragDataLocation(program: webgl.WebGLProgram, name: string): webgl.GLint
```

Gets fragment data location

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| name | string | Yes | [Name](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact-name-c.md) |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Location |

## getIndexedParameter

```TypeScript
getIndexedParameter(target: webgl.GLenum, index: webgl.GLuint): any
```

Gets indexed parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Index |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getInternalformatParameter

```TypeScript
getInternalformatParameter(target: webgl.GLenum, internalformat: webgl.GLenum, pname: webgl.GLenum): any
```

Gets internal format parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getQuery

```TypeScript
getQuery(target: webgl.GLenum, pname: webgl.GLenum): WebGLQuery | null
```

Gets a query

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Target |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLQuery](arkts-arkgraphics2d-webgl2-webglquery-i.md) &#124; null | The query |

## getQueryParameter

```TypeScript
getQueryParameter(query: WebGLQuery, pname: webgl.GLenum): any
```

Gets query parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [WebGLQuery](arkts-arkgraphics2d-webgl2-webglquery-i.md) | Yes | Query |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getSamplerParameter

```TypeScript
getSamplerParameter(sampler: WebGLSampler, pname: webgl.GLenum): any
```

Gets sampler parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sampler | [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) | Yes | [Sampler](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-sampler-i.md) |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getSyncParameter

```TypeScript
getSyncParameter(sync: WebGLSync, pname: webgl.GLenum): any
```

Gets sync parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sync | [WebGLSync](arkts-arkgraphics2d-webgl2-webglsync-i.md) | Yes | Sync object |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | Parameter value |

## getTransformFeedbackVarying

```TypeScript
getTransformFeedbackVarying(program: webgl.WebGLProgram, index: webgl.GLuint): webgl.WebGLActiveInfo | null
```

Gets transform feedback varying

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Index |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.WebGLActiveInfo](arkts-arkgraphics2d-webgl-webglactiveinfo-i.md) &#124; null | Active info |

## getUniformBlockIndex

```TypeScript
getUniformBlockIndex(program: webgl.WebGLProgram, uniformBlockName: string): webgl.GLuint
```

Gets uniform block index

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| uniformBlockName | string | Yes | Uniform block name |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Uniform block index |

## getUniformIndices

```TypeScript
getUniformIndices(program: webgl.WebGLProgram, uniformNames: string[]): webgl.GLuint[] | null
```

Gets uniform indices

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| uniformNames | string[] | Yes | Uniform names |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md)[] &#124; null | Uniform indices |

## invalidateFramebuffer

```TypeScript
invalidateFramebuffer(target: webgl.GLenum, attachments: webgl.GLenum[]): void
```

Invalidates framebuffer attachments

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Framebuffer target |
| attachments | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)[] | Yes | Attachments to invalidate |

## invalidateSubFramebuffer

```TypeScript
invalidateSubFramebuffer(
      target: webgl.GLenum,
      attachments: webgl.GLenum[],
      x: webgl.GLint,
      y: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
    ): void
```

Invalidates sub framebuffer attachments

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Framebuffer target |
| attachments | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)[] | Yes | Attachments to invalidate |
| x | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |

## isQuery

```TypeScript
isQuery(query: WebGLQuery | null): webgl.GLboolean
```

Returns whether a query is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [WebGLQuery](arkts-arkgraphics2d-webgl2-webglquery-i.md) &#124; null | Yes | Query |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the query is valid |

## isSampler

```TypeScript
isSampler(sampler: WebGLSampler | null): webgl.GLboolean
```

Returns whether a sampler is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sampler | [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) &#124; null | Yes | [Sampler](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-sampler-i.md) |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the sampler is valid |

## isSync

```TypeScript
isSync(sync: WebGLSync | null): webgl.GLboolean
```

Returns whether a sync object is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sync | [WebGLSync](arkts-arkgraphics2d-webgl2-webglsync-i.md) &#124; null | Yes | Sync object |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the sync is valid |

## isTransformFeedback

```TypeScript
isTransformFeedback(tf: WebGLTransformFeedback | null): webgl.GLboolean
```

Returns whether a transform feedback is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tf | [WebGLTransformFeedback](arkts-arkgraphics2d-webgl2-webgltransformfeedback-i.md) &#124; null | Yes | Transform feedback |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the transform feedback is valid |

## isVertexArray

```TypeScript
isVertexArray(vertexArray: WebGLVertexArrayObject | null): webgl.GLboolean
```

Returns whether a vertex array is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vertexArray | [WebGLVertexArrayObject](arkts-arkgraphics2d-webgl2-webglvertexarrayobject-i.md) &#124; null | Yes | Vertex array |

**Return value:**

| Type | Description |
| --- | --- |
| [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the vertex array is valid |

## pauseTransformFeedback

```TypeScript
pauseTransformFeedback(): void
```

Pauses transform feedback

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## readBuffer

```TypeScript
readBuffer(src: webgl.GLenum): void
```

Sets the read buffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Read buffer |

## renderbufferStorageMultisample

```TypeScript
renderbufferStorageMultisample(
      target: webgl.GLenum,
      samples: webgl.GLsizei,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
    ): void
```

Sets renderbuffer storage with multisampling

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Renderbuffer target |
| samples | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Number of samples |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |

## resumeTransformFeedback

```TypeScript
resumeTransformFeedback(): void
```

Resumes transform feedback

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## samplerParameterf

```TypeScript
samplerParameterf(sampler: WebGLSampler, pname: webgl.GLenum, param: webgl.GLfloat): void
```

Sets sampler parameterf

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sampler | [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) | Yes | [Sampler](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-sampler-i.md) |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |
| param | [webgl.GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Parameter value |

## samplerParameteri

```TypeScript
samplerParameteri(sampler: WebGLSampler, pname: webgl.GLenum, param: webgl.GLint): void
```

Sets sampler parameteri

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sampler | [WebGLSampler](arkts-arkgraphics2d-webgl2-webglsampler-i.md) | Yes | [Sampler](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-sampler-i.md) |
| pname | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |
| param | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Parameter value |

## texImage3D

```TypeScript
texImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      pboOffset: webgl.GLintptr,
    ): void
```

Sets texture image 3D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| pboOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | PBO offset |

## texImage3D

```TypeScript
texImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      source: webgl.TexImageSource,
    ): void
```

Sets texture image 3D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| source | [webgl.TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

## texImage3D

```TypeScript
texImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      srcData: ArrayBufferView | null,
    ): void
```

Sets texture image 3D from ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Source data |

## texImage3D

```TypeScript
texImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      srcData: ArrayBufferView,
      srcOffset: webgl.GLuint,
    ): void
```

Sets texture image 3D from ArrayBufferView with offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Source offset |

## texStorage2D

```TypeScript
texStorage2D(
      target: webgl.GLenum,
      levels: webgl.GLsizei,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
    ): void
```

Sets texture storage 2D

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| levels | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Number of levels |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |

## texStorage3D

```TypeScript
texStorage3D(
      target: webgl.GLenum,
      levels: webgl.GLsizei,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
    ): void
```

Sets texture storage 3D

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| levels | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Number of levels |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |

## texSubImage3D

```TypeScript
texSubImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      zoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      pboOffset: webgl.GLintptr,
    ): void
```

Sets texture sub image 3D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| zoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| pboOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | PBO offset |

## texSubImage3D

```TypeScript
texSubImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      zoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      source: webgl.TexImageSource,
    ): void
```

Sets texture sub image 3D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| zoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| source | [webgl.TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

## texSubImage3D

```TypeScript
texSubImage3D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      zoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      depth: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      srcData: ArrayBufferView | null,
      srcOffset?: webgl.GLuint,
    ): void
```

Sets texture sub image 3D from ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| zoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| depth | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Depth |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |

## transformFeedbackVaryings

```TypeScript
transformFeedbackVaryings(program: webgl.WebGLProgram, varyings: string[], bufferMode: webgl.GLenum): void
```

Sets transform feedback varyings

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| varyings | string[] | Yes | Varyings |
| bufferMode | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer mode |

## uniform1ui

```TypeScript
uniform1ui(location: webgl.WebGLUniformLocation | null, v0: webgl.GLuint): void
```

Sets uniform1ui value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v0 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Value |

## uniform1uiv

```TypeScript
uniform1uiv(
      location: webgl.WebGLUniformLocation | null,
      data: Uint32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform1uiv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [Uint32List](arkts-arkgraphics2d-uint32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform2ui

```TypeScript
uniform2ui(location: webgl.WebGLUniformLocation | null, v0: webgl.GLuint, v1: webgl.GLuint): void
```

Sets uniform2ui value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v0 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | X value |
| v1 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Y value |

## uniform2uiv

```TypeScript
uniform2uiv(
      location: webgl.WebGLUniformLocation | null,
      data: Uint32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform2uiv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [Uint32List](arkts-arkgraphics2d-uint32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform3ui

```TypeScript
uniform3ui(location: webgl.WebGLUniformLocation | null, v0: webgl.GLuint, v1: webgl.GLuint, v2: webgl.GLuint): void
```

Sets uniform3ui value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v0 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | X value |
| v1 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Y value |
| v2 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Z value |

## uniform3uiv

```TypeScript
uniform3uiv(
      location: webgl.WebGLUniformLocation | null,
      data: Uint32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform3uiv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [Uint32List](arkts-arkgraphics2d-uint32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform4ui

```TypeScript
uniform4ui(
      location: webgl.WebGLUniformLocation | null,
      v0: webgl.GLuint,
      v1: webgl.GLuint,
      v2: webgl.GLuint,
      v3: webgl.GLuint,
    ): void
```

Sets uniform4ui value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v0 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | X value |
| v1 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Y value |
| v2 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Z value |
| v3 | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | W value |

## uniform4uiv

```TypeScript
uniform4uiv(
      location: webgl.WebGLUniformLocation | null,
      data: Uint32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform4uiv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [Uint32List](arkts-arkgraphics2d-uint32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformBlockBinding

```TypeScript
uniformBlockBinding(
      program: webgl.WebGLProgram,
      uniformBlockIndex: webgl.GLuint,
      uniformBlockBinding: webgl.GLuint,
    ): void
```

Sets uniform block binding

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [webgl.WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | Program |
| uniformBlockIndex | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Uniform block index |
| uniformBlockBinding | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Uniform block binding |

## uniformMatrix2x3fv

```TypeScript
uniformMatrix2x3fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix2x3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix2x4fv

```TypeScript
uniformMatrix2x4fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix2x4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix3x2fv

```TypeScript
uniformMatrix3x2fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix3x2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix3x4fv

```TypeScript
uniformMatrix3x4fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix3x4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix4x2fv

```TypeScript
uniformMatrix4x2fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix4x2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix4x3fv

```TypeScript
uniformMatrix4x3fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix4x3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## vertexAttribDivisor

```TypeScript
vertexAttribDivisor(index: webgl.GLuint, divisor: webgl.GLuint): void
```

Sets vertex attrib divisor

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| divisor | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Divisor |

## vertexAttribI4i

```TypeScript
vertexAttribI4i(index: webgl.GLuint, x: webgl.GLint, y: webgl.GLint, z: webgl.GLint, w: webgl.GLint): void
```

Sets vertex attrib I4i value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| x | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X value |
| y | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y value |
| z | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z value |
| w | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | W value |

## vertexAttribI4iv

```TypeScript
vertexAttribI4iv(index: webgl.GLuint, values: webgl.Int32List): void
```

Sets vertex attrib I4iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| values | [webgl.Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Values |

## vertexAttribI4ui

```TypeScript
vertexAttribI4ui(index: webgl.GLuint, x: webgl.GLuint, y: webgl.GLuint, z: webgl.GLuint, w: webgl.GLuint): void
```

Sets vertex attrib I4ui value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| x | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | X value |
| y | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Y value |
| z | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Z value |
| w | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | W value |

## vertexAttribI4uiv

```TypeScript
vertexAttribI4uiv(index: webgl.GLuint, values: Uint32List): void
```

Sets vertex attrib I4uiv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| values | [Uint32List](arkts-arkgraphics2d-uint32list-t.md) | Yes | Values |

## vertexAttribIPointer

```TypeScript
vertexAttribIPointer(
      index: webgl.GLuint,
      size: webgl.GLint,
      type: webgl.GLenum,
      stride: webgl.GLsizei,
      offset: webgl.GLintptr,
    ): void
```

Sets vertex attrib integer pointer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| size | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Size |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type |
| stride | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Stride |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

## waitSync

```TypeScript
waitSync(sync: WebGLSync, flags: webgl.GLbitfield, timeout: GLint64): void
```

Waits for sync object

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sync | [WebGLSync](arkts-arkgraphics2d-webgl2-webglsync-i.md) | Yes | Sync object |
| flags | [webgl.GLbitfield](arkts-arkgraphics2d-glbitfield-t.md) | Yes | Flags |
| timeout | [GLint64](arkts-arkgraphics2d-glint64-t.md) | Yes | Timeout |

## ACTIVE_UNIFORM_BLOCKS

```TypeScript
readonly ACTIVE_UNIFORM_BLOCKS: webgl.GLenum
```

Active Uniform Blocks

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## ALREADY_SIGNALED

```TypeScript
readonly ALREADY_SIGNALED: webgl.GLenum
```

Already Signaled

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## ANY_SAMPLES_PASSED

```TypeScript
readonly ANY_SAMPLES_PASSED: webgl.GLenum
```

Any Samples Passed

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## ANY_SAMPLES_PASSED_CONSERVATIVE

```TypeScript
readonly ANY_SAMPLES_PASSED_CONSERVATIVE: webgl.GLenum
```

Any Samples Passed Conservative

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR

```TypeScript
readonly COLOR: webgl.GLenum
```

Buffer: color

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT1

```TypeScript
readonly COLOR_ATTACHMENT1: webgl.GLenum
```

Color Attachment1

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT10

```TypeScript
readonly COLOR_ATTACHMENT10: webgl.GLenum
```

Color Attachment10

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT11

```TypeScript
readonly COLOR_ATTACHMENT11: webgl.GLenum
```

Color Attachment11

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT12

```TypeScript
readonly COLOR_ATTACHMENT12: webgl.GLenum
```

Color Attachment12

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT13

```TypeScript
readonly COLOR_ATTACHMENT13: webgl.GLenum
```

Color Attachment13

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT14

```TypeScript
readonly COLOR_ATTACHMENT14: webgl.GLenum
```

Color Attachment14

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT15

```TypeScript
readonly COLOR_ATTACHMENT15: webgl.GLenum
```

Color Attachment15

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT2

```TypeScript
readonly COLOR_ATTACHMENT2: webgl.GLenum
```

Color Attachment2

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT3

```TypeScript
readonly COLOR_ATTACHMENT3: webgl.GLenum
```

Color Attachment3

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT4

```TypeScript
readonly COLOR_ATTACHMENT4: webgl.GLenum
```

Color Attachment4

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT5

```TypeScript
readonly COLOR_ATTACHMENT5: webgl.GLenum
```

Color Attachment5

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT6

```TypeScript
readonly COLOR_ATTACHMENT6: webgl.GLenum
```

Color Attachment6

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT7

```TypeScript
readonly COLOR_ATTACHMENT7: webgl.GLenum
```

Color Attachment7

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT8

```TypeScript
readonly COLOR_ATTACHMENT8: webgl.GLenum
```

Color Attachment8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COLOR_ATTACHMENT9

```TypeScript
readonly COLOR_ATTACHMENT9: webgl.GLenum
```

Color Attachment9

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COMPARE_REF_TO_TEXTURE

```TypeScript
readonly COMPARE_REF_TO_TEXTURE: webgl.GLenum
```

Compare Ref To Texture

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## CONDITION_SATISFIED

```TypeScript
readonly CONDITION_SATISFIED: webgl.GLenum
```

Condition Satisfied

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COPY_READ_BUFFER

```TypeScript
readonly COPY_READ_BUFFER: webgl.GLenum
```

Copy Read Buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COPY_READ_BUFFER_BINDING

```TypeScript
readonly COPY_READ_BUFFER_BINDING: webgl.GLenum
```

Copy Read Buffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COPY_WRITE_BUFFER

```TypeScript
readonly COPY_WRITE_BUFFER: webgl.GLenum
```

Copy Write Buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## COPY_WRITE_BUFFER_BINDING

```TypeScript
readonly COPY_WRITE_BUFFER_BINDING: webgl.GLenum
```

Copy Write Buffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## CURRENT_QUERY

```TypeScript
readonly CURRENT_QUERY: webgl.GLenum
```

Current query

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DEPTH

```TypeScript
readonly DEPTH: webgl.GLenum
```

Buffer: depth

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DEPTH24_STENCIL8

```TypeScript
readonly DEPTH24_STENCIL8: webgl.GLenum
```

Depth24 Stencil8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DEPTH32F_STENCIL8

```TypeScript
readonly DEPTH32F_STENCIL8: webgl.GLenum
```

Depth32F Stencil8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DEPTH_COMPONENT24

```TypeScript
readonly DEPTH_COMPONENT24: webgl.GLenum
```

Internal format: depth component24

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DEPTH_COMPONENT32F

```TypeScript
readonly DEPTH_COMPONENT32F: webgl.GLenum
```

Depth Component32F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER0

```TypeScript
readonly DRAW_BUFFER0: webgl.GLenum
```

Draw buffer 0

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER1

```TypeScript
readonly DRAW_BUFFER1: webgl.GLenum
```

Draw buffer 1

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER10

```TypeScript
readonly DRAW_BUFFER10: webgl.GLenum
```

Draw Buffer10

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER11

```TypeScript
readonly DRAW_BUFFER11: webgl.GLenum
```

Draw Buffer11

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER12

```TypeScript
readonly DRAW_BUFFER12: webgl.GLenum
```

Draw Buffer12

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER13

```TypeScript
readonly DRAW_BUFFER13: webgl.GLenum
```

Draw Buffer13

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER14

```TypeScript
readonly DRAW_BUFFER14: webgl.GLenum
```

Draw Buffer14

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER15

```TypeScript
readonly DRAW_BUFFER15: webgl.GLenum
```

Draw Buffer15

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER2

```TypeScript
readonly DRAW_BUFFER2: webgl.GLenum
```

Draw buffer 2

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER3

```TypeScript
readonly DRAW_BUFFER3: webgl.GLenum
```

Draw buffer 3

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER4

```TypeScript
readonly DRAW_BUFFER4: webgl.GLenum
```

Draw buffer 4

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER5

```TypeScript
readonly DRAW_BUFFER5: webgl.GLenum
```

Draw Buffer5

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER6

```TypeScript
readonly DRAW_BUFFER6: webgl.GLenum
```

Draw Buffer6

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER7

```TypeScript
readonly DRAW_BUFFER7: webgl.GLenum
```

Draw Buffer7

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER8

```TypeScript
readonly DRAW_BUFFER8: webgl.GLenum
```

Draw Buffer8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_BUFFER9

```TypeScript
readonly DRAW_BUFFER9: webgl.GLenum
```

Draw Buffer9

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_FRAMEBUFFER

```TypeScript
readonly DRAW_FRAMEBUFFER: webgl.GLenum
```

Draw Framebuffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DRAW_FRAMEBUFFER_BINDING

```TypeScript
readonly DRAW_FRAMEBUFFER_BINDING: webgl.GLenum
```

Draw Framebuffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DYNAMIC_COPY

```TypeScript
readonly DYNAMIC_COPY: webgl.GLenum
```

Buffer usage: dynamic copy

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## DYNAMIC_READ

```TypeScript
readonly DYNAMIC_READ: webgl.GLenum
```

Buffer usage: dynamic read

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_32_UNSIGNED_INT_24_8_REV

```TypeScript
readonly FLOAT_32_UNSIGNED_INT_24_8_REV: webgl.GLenum
```

Float 32 Unsigned Int 24 8 Rev

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_MAT2x3

```TypeScript
readonly FLOAT_MAT2x3: webgl.GLenum
```

Float Mat2X3

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_MAT2x4

```TypeScript
readonly FLOAT_MAT2x4: webgl.GLenum
```

Float Mat2X4

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_MAT3x2

```TypeScript
readonly FLOAT_MAT3x2: webgl.GLenum
```

Float Mat3X2

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_MAT3x4

```TypeScript
readonly FLOAT_MAT3x4: webgl.GLenum
```

Float Mat3X4

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_MAT4x2

```TypeScript
readonly FLOAT_MAT4x2: webgl.GLenum
```

Float Mat4X2

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FLOAT_MAT4x3

```TypeScript
readonly FLOAT_MAT4x3: webgl.GLenum
```

Float Mat4X3

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAGMENT_SHADER_DERIVATIVE_HINT

```TypeScript
readonly FRAGMENT_SHADER_DERIVATIVE_HINT: webgl.GLenum
```

Fragment Shader Derivative Hint

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_ALPHA_SIZE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_ALPHA_SIZE: webgl.GLenum
```

Framebuffer Attachment Alpha Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_BLUE_SIZE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_BLUE_SIZE: webgl.GLenum
```

Framebuffer Attachment Blue Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_COLOR_ENCODING

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_COLOR_ENCODING: webgl.GLenum
```

Framebuffer Attachment Color Encoding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_COMPONENT_TYPE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_COMPONENT_TYPE: webgl.GLenum
```

Framebuffer Attachment Component Type

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_DEPTH_SIZE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_DEPTH_SIZE: webgl.GLenum
```

Framebuffer Attachment Depth Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_GREEN_SIZE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_GREEN_SIZE: webgl.GLenum
```

Framebuffer Attachment Green Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_RED_SIZE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_RED_SIZE: webgl.GLenum
```

Framebuffer Attachment Red Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_STENCIL_SIZE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_STENCIL_SIZE: webgl.GLenum
```

Framebuffer Attachment Stencil Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_ATTACHMENT_TEXTURE_LAYER

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_TEXTURE_LAYER: webgl.GLenum
```

Framebuffer Attachment Texture Layer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_DEFAULT

```TypeScript
readonly FRAMEBUFFER_DEFAULT: webgl.GLenum
```

Framebuffer Default

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## FRAMEBUFFER_INCOMPLETE_MULTISAMPLE

```TypeScript
readonly FRAMEBUFFER_INCOMPLETE_MULTISAMPLE: webgl.GLenum
```

Framebuffer Incomplete Multisample

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## HALF_FLOAT

```TypeScript
readonly HALF_FLOAT: webgl.GLenum
```

Half Float

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INT_2_10_10_10_REV

```TypeScript
readonly INT_2_10_10_10_REV: webgl.GLenum
```

Data type: INT 2_10_10_10_REV

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INT_SAMPLER_2D

```TypeScript
readonly INT_SAMPLER_2D: webgl.GLenum
```

Int Sampler 2D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INT_SAMPLER_2D_ARRAY

```TypeScript
readonly INT_SAMPLER_2D_ARRAY: webgl.GLenum
```

Int Sampler 2D Array

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INT_SAMPLER_3D

```TypeScript
readonly INT_SAMPLER_3D: webgl.GLenum
```

Int Sampler 3D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INT_SAMPLER_CUBE

```TypeScript
readonly INT_SAMPLER_CUBE: webgl.GLenum
```

Int Sampler Cube

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INTERLEAVED_ATTRIBS

```TypeScript
readonly INTERLEAVED_ATTRIBS: webgl.GLenum
```

Interleaved Attribs

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## INVALID_INDEX

```TypeScript
readonly INVALID_INDEX: webgl.GLenum
```

Invalid Index

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX

```TypeScript
readonly MAX: webgl.GLenum
```

Max value

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_3D_TEXTURE_SIZE

```TypeScript
readonly MAX_3D_TEXTURE_SIZE: webgl.GLenum
```

Max 3D texture size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_ARRAY_TEXTURE_LAYERS

```TypeScript
readonly MAX_ARRAY_TEXTURE_LAYERS: webgl.GLenum
```

Max Array Texture Layers

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_CLIENT_WAIT_TIMEOUT_WEBGL

```TypeScript
readonly MAX_CLIENT_WAIT_TIMEOUT_WEBGL: webgl.GLenum
```

Max client wait timeout WebGL

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_COLOR_ATTACHMENTS

```TypeScript
readonly MAX_COLOR_ATTACHMENTS: webgl.GLenum
```

Max Color Attachments

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_COMBINED_FRAGMENT_UNIFORM_COMPONENTS

```TypeScript
readonly MAX_COMBINED_FRAGMENT_UNIFORM_COMPONENTS: webgl.GLenum
```

Max Combined Fragment Uniform Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_COMBINED_UNIFORM_BLOCKS

```TypeScript
readonly MAX_COMBINED_UNIFORM_BLOCKS: webgl.GLenum
```

Max Combined Uniform Blocks

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_COMBINED_VERTEX_UNIFORM_COMPONENTS

```TypeScript
readonly MAX_COMBINED_VERTEX_UNIFORM_COMPONENTS: webgl.GLenum
```

Max Combined Vertex Uniform Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_DRAW_BUFFERS

```TypeScript
readonly MAX_DRAW_BUFFERS: webgl.GLenum
```

Max draw buffers

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_ELEMENT_INDEX

```TypeScript
readonly MAX_ELEMENT_INDEX: webgl.GLenum
```

Max element index

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_ELEMENTS_INDICES

```TypeScript
readonly MAX_ELEMENTS_INDICES: webgl.GLenum
```

Max elements indices

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_ELEMENTS_VERTICES

```TypeScript
readonly MAX_ELEMENTS_VERTICES: webgl.GLenum
```

Max elements vertices

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_FRAGMENT_INPUT_COMPONENTS

```TypeScript
readonly MAX_FRAGMENT_INPUT_COMPONENTS: webgl.GLenum
```

Max Fragment Input Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_FRAGMENT_UNIFORM_BLOCKS

```TypeScript
readonly MAX_FRAGMENT_UNIFORM_BLOCKS: webgl.GLenum
```

Max Fragment Uniform Blocks

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_FRAGMENT_UNIFORM_COMPONENTS

```TypeScript
readonly MAX_FRAGMENT_UNIFORM_COMPONENTS: webgl.GLenum
```

Max Fragment Uniform Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_PROGRAM_TEXEL_OFFSET

```TypeScript
readonly MAX_PROGRAM_TEXEL_OFFSET: webgl.GLenum
```

Max Program Texel Offset

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_SAMPLES

```TypeScript
readonly MAX_SAMPLES: webgl.GLenum
```

Max Samples

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_SERVER_WAIT_TIMEOUT

```TypeScript
readonly MAX_SERVER_WAIT_TIMEOUT: webgl.GLenum
```

Max Server Wait Timeout

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_TEXTURE_LOD_BIAS

```TypeScript
readonly MAX_TEXTURE_LOD_BIAS: webgl.GLenum
```

Max texture LOD bias

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_TRANSFORM_FEEDBACK_INTERLEAVED_COMPONENTS

```TypeScript
readonly MAX_TRANSFORM_FEEDBACK_INTERLEAVED_COMPONENTS: webgl.GLenum
```

Max Transform Feedback Interleaved Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_TRANSFORM_FEEDBACK_SEPARATE_ATTRIBS

```TypeScript
readonly MAX_TRANSFORM_FEEDBACK_SEPARATE_ATTRIBS: webgl.GLenum
```

Max Transform Feedback Separate Attribs

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_TRANSFORM_FEEDBACK_SEPARATE_COMPONENTS

```TypeScript
readonly MAX_TRANSFORM_FEEDBACK_SEPARATE_COMPONENTS: webgl.GLenum
```

Max Transform Feedback Separate Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_UNIFORM_BLOCK_SIZE

```TypeScript
readonly MAX_UNIFORM_BLOCK_SIZE: webgl.GLenum
```

Max Uniform Block Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_UNIFORM_BUFFER_BINDINGS

```TypeScript
readonly MAX_UNIFORM_BUFFER_BINDINGS: webgl.GLenum
```

Max Uniform Buffer Bindings

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_VARYING_COMPONENTS

```TypeScript
readonly MAX_VARYING_COMPONENTS: webgl.GLenum
```

Max Varying Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_VERTEX_OUTPUT_COMPONENTS

```TypeScript
readonly MAX_VERTEX_OUTPUT_COMPONENTS: webgl.GLenum
```

Max Vertex Output Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_VERTEX_UNIFORM_BLOCKS

```TypeScript
readonly MAX_VERTEX_UNIFORM_BLOCKS: webgl.GLenum
```

Max Vertex Uniform Blocks

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MAX_VERTEX_UNIFORM_COMPONENTS

```TypeScript
readonly MAX_VERTEX_UNIFORM_COMPONENTS: webgl.GLenum
```

Max Vertex Uniform Components

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MIN

```TypeScript
readonly MIN: webgl.GLenum
```

Min value

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## MIN_PROGRAM_TEXEL_OFFSET

```TypeScript
readonly MIN_PROGRAM_TEXEL_OFFSET: webgl.GLenum
```

Min Program Texel Offset

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## OBJECT_TYPE

```TypeScript
readonly OBJECT_TYPE: webgl.GLenum
```

Object Type

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PACK_ROW_LENGTH

```TypeScript
readonly PACK_ROW_LENGTH: webgl.GLenum
```

Pack row length

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PACK_SKIP_PIXELS

```TypeScript
readonly PACK_SKIP_PIXELS: webgl.GLenum
```

Pack skip pixels

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PACK_SKIP_ROWS

```TypeScript
readonly PACK_SKIP_ROWS: webgl.GLenum
```

Pack skip rows

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PIXEL_PACK_BUFFER

```TypeScript
readonly PIXEL_PACK_BUFFER: webgl.GLenum
```

Pixel Pack Buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PIXEL_PACK_BUFFER_BINDING

```TypeScript
readonly PIXEL_PACK_BUFFER_BINDING: webgl.GLenum
```

Pixel Pack Buffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PIXEL_UNPACK_BUFFER

```TypeScript
readonly PIXEL_UNPACK_BUFFER: webgl.GLenum
```

Pixel Unpack Buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## PIXEL_UNPACK_BUFFER_BINDING

```TypeScript
readonly PIXEL_UNPACK_BUFFER_BINDING: webgl.GLenum
```

Pixel Unpack Buffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## QUERY_RESULT

```TypeScript
readonly QUERY_RESULT: webgl.GLenum
```

Query result

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## QUERY_RESULT_AVAILABLE

```TypeScript
readonly QUERY_RESULT_AVAILABLE: webgl.GLenum
```

Query result available

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R11F_G11F_B10F

```TypeScript
readonly R11F_G11F_B10F: webgl.GLenum
```

R11F G11F B10F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R16F

```TypeScript
readonly R16F: webgl.GLenum
```

R16F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R16I

```TypeScript
readonly R16I: webgl.GLenum
```

R16I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R16UI

```TypeScript
readonly R16UI: webgl.GLenum
```

R16Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R32F

```TypeScript
readonly R32F: webgl.GLenum
```

R32F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R32I

```TypeScript
readonly R32I: webgl.GLenum
```

R32I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R32UI

```TypeScript
readonly R32UI: webgl.GLenum
```

R32Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R8

```TypeScript
readonly R8: webgl.GLenum
```

R8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R8_SNORM

```TypeScript
readonly R8_SNORM: webgl.GLenum
```

R8 Snorm

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R8I

```TypeScript
readonly R8I: webgl.GLenum
```

R8I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## R8UI

```TypeScript
readonly R8UI: webgl.GLenum
```

R8Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RASTERIZER_DISCARD

```TypeScript
readonly RASTERIZER_DISCARD: webgl.GLenum
```

Rasterizer Discard

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## READ_BUFFER

```TypeScript
readonly READ_BUFFER: webgl.GLenum
```

Read buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## READ_FRAMEBUFFER

```TypeScript
readonly READ_FRAMEBUFFER: webgl.GLenum
```

Read Framebuffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## READ_FRAMEBUFFER_BINDING

```TypeScript
readonly READ_FRAMEBUFFER_BINDING: webgl.GLenum
```

Read Framebuffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RED

```TypeScript
readonly RED: webgl.GLenum
```

Pixel format: red

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RED_INTEGER

```TypeScript
readonly RED_INTEGER: webgl.GLenum
```

Red Integer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RENDERBUFFER_SAMPLES

```TypeScript
readonly RENDERBUFFER_SAMPLES: webgl.GLenum
```

Renderbuffer Samples

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG

```TypeScript
readonly RG: webgl.GLenum
```

Rg

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG16F

```TypeScript
readonly RG16F: webgl.GLenum
```

Rg16F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG16I

```TypeScript
readonly RG16I: webgl.GLenum
```

Rg16I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG16UI

```TypeScript
readonly RG16UI: webgl.GLenum
```

Rg16Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG32F

```TypeScript
readonly RG32F: webgl.GLenum
```

Rg32F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG32I

```TypeScript
readonly RG32I: webgl.GLenum
```

Rg32I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG32UI

```TypeScript
readonly RG32UI: webgl.GLenum
```

Rg32Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG8

```TypeScript
readonly RG8: webgl.GLenum
```

Rg8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG8_SNORM

```TypeScript
readonly RG8_SNORM: webgl.GLenum
```

Rg8 Snorm

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG8I

```TypeScript
readonly RG8I: webgl.GLenum
```

Rg8I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG8UI

```TypeScript
readonly RG8UI: webgl.GLenum
```

Rg8Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RG_INTEGER

```TypeScript
readonly RG_INTEGER: webgl.GLenum
```

Rg Integer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB10_A2

```TypeScript
readonly RGB10_A2: webgl.GLenum
```

Internal format: RGB10_A2

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB10_A2UI

```TypeScript
readonly RGB10_A2UI: webgl.GLenum
```

Internal format: RGB10_A2UI

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB16F

```TypeScript
readonly RGB16F: webgl.GLenum
```

Rgb16F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB16I

```TypeScript
readonly RGB16I: webgl.GLenum
```

Rgb16I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB16UI

```TypeScript
readonly RGB16UI: webgl.GLenum
```

Rgb16Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB32F

```TypeScript
readonly RGB32F: webgl.GLenum
```

Rgb32F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB32I

```TypeScript
readonly RGB32I: webgl.GLenum
```

Rgb32I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB32UI

```TypeScript
readonly RGB32UI: webgl.GLenum
```

Rgb32Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB8

```TypeScript
readonly RGB8: webgl.GLenum
```

Internal format: RGB8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB8_SNORM

```TypeScript
readonly RGB8_SNORM: webgl.GLenum
```

Rgb8 Snorm

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB8I

```TypeScript
readonly RGB8I: webgl.GLenum
```

Rgb8I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB8UI

```TypeScript
readonly RGB8UI: webgl.GLenum
```

Rgb8Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB9_E5

```TypeScript
readonly RGB9_E5: webgl.GLenum
```

Rgb9 E5

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGB_INTEGER

```TypeScript
readonly RGB_INTEGER: webgl.GLenum
```

Rgb Integer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA16F

```TypeScript
readonly RGBA16F: webgl.GLenum
```

Rgba16F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA16I

```TypeScript
readonly RGBA16I: webgl.GLenum
```

Rgba16I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA16UI

```TypeScript
readonly RGBA16UI: webgl.GLenum
```

Rgba16Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA32F

```TypeScript
readonly RGBA32F: webgl.GLenum
```

Rgba32F

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA32I

```TypeScript
readonly RGBA32I: webgl.GLenum
```

Rgba32I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA32UI

```TypeScript
readonly RGBA32UI: webgl.GLenum
```

Rgba32Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA8

```TypeScript
readonly RGBA8: webgl.GLenum
```

Internal format: RGBA8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA8_SNORM

```TypeScript
readonly RGBA8_SNORM: webgl.GLenum
```

Rgba8 Snorm

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA8I

```TypeScript
readonly RGBA8I: webgl.GLenum
```

Rgba8I

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA8UI

```TypeScript
readonly RGBA8UI: webgl.GLenum
```

Rgba8Ui

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## RGBA_INTEGER

```TypeScript
readonly RGBA_INTEGER: webgl.GLenum
```

Rgba Integer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SAMPLER_2D_ARRAY

```TypeScript
readonly SAMPLER_2D_ARRAY: webgl.GLenum
```

Sampler 2D Array

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SAMPLER_2D_ARRAY_SHADOW

```TypeScript
readonly SAMPLER_2D_ARRAY_SHADOW: webgl.GLenum
```

Sampler 2D Array Shadow

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SAMPLER_2D_SHADOW

```TypeScript
readonly SAMPLER_2D_SHADOW: webgl.GLenum
```

Sampler 2D Shadow

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SAMPLER_3D

```TypeScript
readonly SAMPLER_3D: webgl.GLenum
```

Sampler 3D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SAMPLER_BINDING

```TypeScript
readonly SAMPLER_BINDING: webgl.GLenum
```

Sampler Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SAMPLER_CUBE_SHADOW

```TypeScript
readonly SAMPLER_CUBE_SHADOW: webgl.GLenum
```

Sampler Cube Shadow

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SEPARATE_ATTRIBS

```TypeScript
readonly SEPARATE_ATTRIBS: webgl.GLenum
```

Separate Attribs

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SIGNALED

```TypeScript
readonly SIGNALED: webgl.GLenum
```

Signaled

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SIGNED_NORMALIZED

```TypeScript
readonly SIGNED_NORMALIZED: webgl.GLenum
```

Signed Normalized

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SRGB

```TypeScript
readonly SRGB: webgl.GLenum
```

Srgb

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SRGB8

```TypeScript
readonly SRGB8: webgl.GLenum
```

Srgb8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SRGB8_ALPHA8

```TypeScript
readonly SRGB8_ALPHA8: webgl.GLenum
```

Srgb8 Alpha8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## STATIC_COPY

```TypeScript
readonly STATIC_COPY: webgl.GLenum
```

Buffer usage: static copy

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## STATIC_READ

```TypeScript
readonly STATIC_READ: webgl.GLenum
```

Buffer usage: static read

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## STENCIL

```TypeScript
readonly STENCIL: webgl.GLenum
```

Buffer: stencil

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## STREAM_COPY

```TypeScript
readonly STREAM_COPY: webgl.GLenum
```

Buffer usage: stream copy

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## STREAM_READ

```TypeScript
readonly STREAM_READ: webgl.GLenum
```

Buffer usage: stream read

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SYNC_CONDITION

```TypeScript
readonly SYNC_CONDITION: webgl.GLenum
```

Sync Condition

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SYNC_FENCE

```TypeScript
readonly SYNC_FENCE: webgl.GLenum
```

Sync Fence

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SYNC_FLAGS

```TypeScript
readonly SYNC_FLAGS: webgl.GLenum
```

Sync Flags

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SYNC_FLUSH_COMMANDS_BIT

```TypeScript
readonly SYNC_FLUSH_COMMANDS_BIT: webgl.GLenum
```

Sync Flush Commands Bit

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SYNC_GPU_COMMANDS_COMPLETE

```TypeScript
readonly SYNC_GPU_COMMANDS_COMPLETE: webgl.GLenum
```

Sync Gpu Commands Complete

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## SYNC_STATUS

```TypeScript
readonly SYNC_STATUS: webgl.GLenum
```

Sync Status

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_2D_ARRAY

```TypeScript
readonly TEXTURE_2D_ARRAY: webgl.GLenum
```

Texture 2D Array

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_3D

```TypeScript
readonly TEXTURE_3D: webgl.GLenum
```

Texture target: 3D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_BASE_LEVEL

```TypeScript
readonly TEXTURE_BASE_LEVEL: webgl.GLenum
```

Texture base level

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_BINDING_2D_ARRAY

```TypeScript
readonly TEXTURE_BINDING_2D_ARRAY: webgl.GLenum
```

Texture Binding 2D Array

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_BINDING_3D

```TypeScript
readonly TEXTURE_BINDING_3D: webgl.GLenum
```

Texture binding 3D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_COMPARE_FUNC

```TypeScript
readonly TEXTURE_COMPARE_FUNC: webgl.GLenum
```

Texture compare function

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_COMPARE_MODE

```TypeScript
readonly TEXTURE_COMPARE_MODE: webgl.GLenum
```

Texture compare mode

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_IMMUTABLE_FORMAT

```TypeScript
readonly TEXTURE_IMMUTABLE_FORMAT: webgl.GLenum
```

Texture immutable format

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_IMMUTABLE_LEVELS

```TypeScript
readonly TEXTURE_IMMUTABLE_LEVELS: webgl.GLenum
```

Texture immutable levels

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_MAX_LEVEL

```TypeScript
readonly TEXTURE_MAX_LEVEL: webgl.GLenum
```

Texture max level

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_MAX_LOD

```TypeScript
readonly TEXTURE_MAX_LOD: webgl.GLenum
```

Texture max LOD

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_MIN_LOD

```TypeScript
readonly TEXTURE_MIN_LOD: webgl.GLenum
```

Texture min LOD

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TEXTURE_WRAP_R

```TypeScript
readonly TEXTURE_WRAP_R: webgl.GLenum
```

Texture wrap: R

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TIMEOUT_EXPIRED

```TypeScript
readonly TIMEOUT_EXPIRED: webgl.GLenum
```

Timeout Expired

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TIMEOUT_IGNORED

```TypeScript
readonly TIMEOUT_IGNORED: GLint64
```

Timeout ignored

**Type:** [GLint64](arkts-arkgraphics2d-glint64-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK

```TypeScript
readonly TRANSFORM_FEEDBACK: webgl.GLenum
```

Transform feedback target

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_ACTIVE

```TypeScript
readonly TRANSFORM_FEEDBACK_ACTIVE: webgl.GLenum
```

Transform feedback active

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_BINDING

```TypeScript
readonly TRANSFORM_FEEDBACK_BINDING: webgl.GLenum
```

Transform feedback binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_BUFFER

```TypeScript
readonly TRANSFORM_FEEDBACK_BUFFER: webgl.GLenum
```

Transform Feedback Buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_BUFFER_BINDING

```TypeScript
readonly TRANSFORM_FEEDBACK_BUFFER_BINDING: webgl.GLenum
```

Transform Feedback Buffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_BUFFER_MODE

```TypeScript
readonly TRANSFORM_FEEDBACK_BUFFER_MODE: webgl.GLenum
```

Transform Feedback Buffer Mode

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_BUFFER_SIZE

```TypeScript
readonly TRANSFORM_FEEDBACK_BUFFER_SIZE: webgl.GLenum
```

Transform Feedback Buffer Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_BUFFER_START

```TypeScript
readonly TRANSFORM_FEEDBACK_BUFFER_START: webgl.GLenum
```

Transform Feedback Buffer Start

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_PAUSED

```TypeScript
readonly TRANSFORM_FEEDBACK_PAUSED: webgl.GLenum
```

Transform feedback paused

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_PRIMITIVES_WRITTEN

```TypeScript
readonly TRANSFORM_FEEDBACK_PRIMITIVES_WRITTEN: webgl.GLenum
```

Transform Feedback Primitives Written

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## TRANSFORM_FEEDBACK_VARYINGS

```TypeScript
readonly TRANSFORM_FEEDBACK_VARYINGS: webgl.GLenum
```

Transform Feedback Varyings

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_ARRAY_STRIDE

```TypeScript
readonly UNIFORM_ARRAY_STRIDE: webgl.GLenum
```

Uniform Array Stride

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_ACTIVE_UNIFORM_INDICES

```TypeScript
readonly UNIFORM_BLOCK_ACTIVE_UNIFORM_INDICES: webgl.GLenum
```

Uniform Block Active Uniform Indices

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_ACTIVE_UNIFORMS

```TypeScript
readonly UNIFORM_BLOCK_ACTIVE_UNIFORMS: webgl.GLenum
```

Uniform Block Active Uniforms

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_BINDING

```TypeScript
readonly UNIFORM_BLOCK_BINDING: webgl.GLenum
```

Uniform Block Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_DATA_SIZE

```TypeScript
readonly UNIFORM_BLOCK_DATA_SIZE: webgl.GLenum
```

Uniform Block Data Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_INDEX

```TypeScript
readonly UNIFORM_BLOCK_INDEX: webgl.GLenum
```

Uniform Block Index

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_REFERENCED_BY_FRAGMENT_SHADER

```TypeScript
readonly UNIFORM_BLOCK_REFERENCED_BY_FRAGMENT_SHADER: webgl.GLenum
```

Uniform Block Referenced By Fragment Shader

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BLOCK_REFERENCED_BY_VERTEX_SHADER

```TypeScript
readonly UNIFORM_BLOCK_REFERENCED_BY_VERTEX_SHADER: webgl.GLenum
```

Uniform Block Referenced By Vertex Shader

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BUFFER

```TypeScript
readonly UNIFORM_BUFFER: webgl.GLenum
```

Uniform Buffer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BUFFER_BINDING

```TypeScript
readonly UNIFORM_BUFFER_BINDING: webgl.GLenum
```

Uniform Buffer Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BUFFER_OFFSET_ALIGNMENT

```TypeScript
readonly UNIFORM_BUFFER_OFFSET_ALIGNMENT: webgl.GLenum
```

Uniform Buffer Offset Alignment

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BUFFER_SIZE

```TypeScript
readonly UNIFORM_BUFFER_SIZE: webgl.GLenum
```

Uniform Buffer Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_BUFFER_START

```TypeScript
readonly UNIFORM_BUFFER_START: webgl.GLenum
```

Uniform Buffer Start

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_IS_ROW_MAJOR

```TypeScript
readonly UNIFORM_IS_ROW_MAJOR: webgl.GLenum
```

Uniform Is Row Major

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_MATRIX_STRIDE

```TypeScript
readonly UNIFORM_MATRIX_STRIDE: webgl.GLenum
```

Uniform Matrix Stride

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_OFFSET

```TypeScript
readonly UNIFORM_OFFSET: webgl.GLenum
```

Uniform Offset

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_SIZE

```TypeScript
readonly UNIFORM_SIZE: webgl.GLenum
```

Uniform Size

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNIFORM_TYPE

```TypeScript
readonly UNIFORM_TYPE: webgl.GLenum
```

Uniform Type

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNPACK_IMAGE_HEIGHT

```TypeScript
readonly UNPACK_IMAGE_HEIGHT: webgl.GLenum
```

Unpack image height

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNPACK_ROW_LENGTH

```TypeScript
readonly UNPACK_ROW_LENGTH: webgl.GLenum
```

Unpack row length

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNPACK_SKIP_IMAGES

```TypeScript
readonly UNPACK_SKIP_IMAGES: webgl.GLenum
```

Unpack skip images

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNPACK_SKIP_PIXELS

```TypeScript
readonly UNPACK_SKIP_PIXELS: webgl.GLenum
```

Unpack skip pixels

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNPACK_SKIP_ROWS

```TypeScript
readonly UNPACK_SKIP_ROWS: webgl.GLenum
```

Unpack skip rows

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNALED

```TypeScript
readonly UNSIGNALED: webgl.GLenum
```

Unsignaled

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_10F_11F_11F_REV

```TypeScript
readonly UNSIGNED_INT_10F_11F_11F_REV: webgl.GLenum
```

Unsigned Int 10F 11F 11F Rev

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_24_8

```TypeScript
readonly UNSIGNED_INT_24_8: webgl.GLenum
```

Unsigned Int 24 8

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_2_10_10_10_REV

```TypeScript
readonly UNSIGNED_INT_2_10_10_10_REV: webgl.GLenum
```

Data type: unsigned int 2_10_10_10 rev

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_5_9_9_9_REV

```TypeScript
readonly UNSIGNED_INT_5_9_9_9_REV: webgl.GLenum
```

Unsigned Int 5 9 9 9 Rev

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_SAMPLER_2D

```TypeScript
readonly UNSIGNED_INT_SAMPLER_2D: webgl.GLenum
```

Unsigned Int Sampler 2D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_SAMPLER_2D_ARRAY

```TypeScript
readonly UNSIGNED_INT_SAMPLER_2D_ARRAY: webgl.GLenum
```

Unsigned Int Sampler 2D Array

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_SAMPLER_3D

```TypeScript
readonly UNSIGNED_INT_SAMPLER_3D: webgl.GLenum
```

Unsigned Int Sampler 3D

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_SAMPLER_CUBE

```TypeScript
readonly UNSIGNED_INT_SAMPLER_CUBE: webgl.GLenum
```

Unsigned Int Sampler Cube

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_VEC2

```TypeScript
readonly UNSIGNED_INT_VEC2: webgl.GLenum
```

Unsigned Int Vec2

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_VEC3

```TypeScript
readonly UNSIGNED_INT_VEC3: webgl.GLenum
```

Unsigned Int Vec3

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_INT_VEC4

```TypeScript
readonly UNSIGNED_INT_VEC4: webgl.GLenum
```

Unsigned Int Vec4

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## UNSIGNED_NORMALIZED

```TypeScript
readonly UNSIGNED_NORMALIZED: webgl.GLenum
```

Unsigned Normalized

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## VERTEX_ARRAY_BINDING

```TypeScript
readonly VERTEX_ARRAY_BINDING: webgl.GLenum
```

Vertex Array Binding

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## VERTEX_ATTRIB_ARRAY_DIVISOR

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_DIVISOR: webgl.GLenum
```

Vertex Attrib Array Divisor

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## VERTEX_ATTRIB_ARRAY_INTEGER

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_INTEGER: webgl.GLenum
```

Vertex Attrib Array Integer

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

## WAIT_FAILED

```TypeScript
readonly WAIT_FAILED: webgl.GLenum
```

Wait Failed

**Type:** [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2
