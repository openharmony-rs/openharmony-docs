# WebGL2RenderingContextOverloads

```TypeScript
interface WebGL2RenderingContextOverloads
```

WebGL 2.0

**Since:** 7

<!--Device-unnamed-interface WebGL2RenderingContextOverloads--><!--Device-unnamed-interface WebGL2RenderingContextOverloads-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

<a id="bufferdata1"></a>

## bufferData

```TypeScript
bufferData(target: webgl.GLenum, size: webgl.GLsizeiptr, usage: webgl.GLenum): void
```

Sets buffer data

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-bufferData(target: webgl.GLenum, size: webgl.GLsizeiptr, usage: webgl.GLenum): void--><!--Device-WebGL2RenderingContextOverloads-bufferData(target: webgl.GLenum, size: webgl.GLsizeiptr, usage: webgl.GLenum): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| size | [webgl.GLsizeiptr](arkts-arkgraphics2d-glsizeiptr-t.md) | Yes | Buffer size |
| usage | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer usage |

<a id="bufferdata2"></a>

## bufferData

```TypeScript
bufferData(target: webgl.GLenum, srcData: BufferSource | null, usage: webgl.GLenum): void
```

Sets buffer data from BufferSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-bufferData(target: webgl.GLenum, srcData: BufferSource | null, usage: webgl.GLenum): void--><!--Device-WebGL2RenderingContextOverloads-bufferData(target: webgl.GLenum, srcData: BufferSource | null, usage: webgl.GLenum): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| srcData | BufferSource &#124; null | Yes | Buffer data |
| usage | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer usage |

<a id="bufferdata3"></a>

## bufferData

```TypeScript
bufferData(
      target: webgl.GLenum,
      srcData: ArrayBufferView,
      usage: webgl.GLenum,
      srcOffset: webgl.GLuint,
      length?: webgl.GLuint,
    ): void
```

Sets buffer data from ArrayBufferView with offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-bufferData(      target: webgl.GLenum,      srcData: ArrayBufferView,      usage: webgl.GLenum,      srcOffset: webgl.GLuint,      length?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-bufferData(      target: webgl.GLenum,      srcData: ArrayBufferView,      usage: webgl.GLenum,      srcOffset: webgl.GLuint,      length?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| usage | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer usage |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Source offset |
| length | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) |

<a id="buffersubdata1"></a>

## bufferSubData

```TypeScript
bufferSubData(target: webgl.GLenum, dstByteOffset: webgl.GLintptr, srcData: BufferSource): void
```

Sets buffer sub data

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-bufferSubData(target: webgl.GLenum, dstByteOffset: webgl.GLintptr, srcData: BufferSource): void--><!--Device-WebGL2RenderingContextOverloads-bufferSubData(target: webgl.GLenum, dstByteOffset: webgl.GLintptr, srcData: BufferSource): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| dstByteOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Destination byte offset |
| srcData | BufferSource | Yes | Source data |

<a id="buffersubdata2"></a>

## bufferSubData

```TypeScript
bufferSubData(
      target: webgl.GLenum,
      dstByteOffset: webgl.GLintptr,
      srcData: ArrayBufferView,
      srcOffset: webgl.GLuint,
      length?: webgl.GLuint,
    ): void
```

Sets buffer sub data with offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-bufferSubData(      target: webgl.GLenum,      dstByteOffset: webgl.GLintptr,      srcData: ArrayBufferView,      srcOffset: webgl.GLuint,      length?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-bufferSubData(      target: webgl.GLenum,      dstByteOffset: webgl.GLintptr,      srcData: ArrayBufferView,      srcOffset: webgl.GLuint,      length?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| dstByteOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Destination byte offset |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Source offset |
| length | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) |

<a id="compressedteximage2d1"></a>

## compressedTexImage2D

```TypeScript
compressedTexImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      border: webgl.GLint,
      imageSize: webgl.GLsizei,
      offset: webgl.GLintptr,
    ): void
```

Compressed texture image 2D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-compressedTexImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLenum,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      imageSize: webgl.GLsizei,      offset: webgl.GLintptr,    ): void--><!--Device-WebGL2RenderingContextOverloads-compressedTexImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLenum,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      imageSize: webgl.GLsizei,      offset: webgl.GLintptr,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| imageSize | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Image size |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

<a id="compressedteximage2d2"></a>

## compressedTexImage2D

```TypeScript
compressedTexImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLenum,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      border: webgl.GLint,
      srcData: ArrayBufferView,
      srcOffset?: webgl.GLuint,
      srcLengthOverride?: webgl.GLuint,
    ): void
```

Compressed texture image 2D from ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-compressedTexImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLenum,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      srcData: ArrayBufferView,      srcOffset?: webgl.GLuint,      srcLengthOverride?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-compressedTexImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLenum,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      srcData: ArrayBufferView,      srcOffset?: webgl.GLuint,      srcLengthOverride?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLengthOverride | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length override |

<a id="compressedtexsubimage2d1"></a>

## compressedTexSubImage2D

```TypeScript
compressedTexSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      imageSize: webgl.GLsizei,
      offset: webgl.GLintptr,
    ): void
```

Compressed texture sub image 2D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-compressedTexSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      imageSize: webgl.GLsizei,      offset: webgl.GLintptr,    ): void--><!--Device-WebGL2RenderingContextOverloads-compressedTexSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      imageSize: webgl.GLsizei,      offset: webgl.GLintptr,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| imageSize | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Image size |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

<a id="compressedtexsubimage2d2"></a>

## compressedTexSubImage2D

```TypeScript
compressedTexSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      srcData: ArrayBufferView,
      srcOffset?: webgl.GLuint,
      srcLengthOverride?: webgl.GLuint,
    ): void
```

Compressed texture sub image 2D from ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-compressedTexSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      srcData: ArrayBufferView,      srcOffset?: webgl.GLuint,      srcLengthOverride?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-compressedTexSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      srcData: ArrayBufferView,      srcOffset?: webgl.GLuint,      srcLengthOverride?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLengthOverride | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length override |

<a id="readpixels1"></a>

## readPixels

```TypeScript
readPixels(
      x: webgl.GLint,
      y: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      dstData: ArrayBufferView | null,
    ): void
```

Reads pixels from the framebuffer to ArrayBufferView

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-readPixels(      x: webgl.GLint,      y: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      dstData: ArrayBufferView | null,    ): void--><!--Device-WebGL2RenderingContextOverloads-readPixels(      x: webgl.GLint,      y: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      dstData: ArrayBufferView | null,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| dstData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Destination data |

<a id="readpixels2"></a>

## readPixels

```TypeScript
readPixels(
      x: webgl.GLint,
      y: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      offset: webgl.GLintptr,
    ): void
```

Reads pixels from the framebuffer to PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-readPixels(      x: webgl.GLint,      y: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      offset: webgl.GLintptr,    ): void--><!--Device-WebGL2RenderingContextOverloads-readPixels(      x: webgl.GLint,      y: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      offset: webgl.GLintptr,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| offset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

<a id="readpixels3"></a>

## readPixels

```TypeScript
readPixels(
      x: webgl.GLint,
      y: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      dstData: ArrayBufferView,
      dstOffset: webgl.GLuint,
    ): void
```

Reads pixels from the framebuffer to ArrayBufferView with offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-readPixels(      x: webgl.GLint,      y: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      dstData: ArrayBufferView,      dstOffset: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-readPixels(      x: webgl.GLint,      y: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      dstData: ArrayBufferView,      dstOffset: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| dstData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Destination data |
| dstOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Destination offset |

<a id="teximage2d1"></a>

## texImage2D

```TypeScript
texImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      pixels: ArrayBufferView | null,
    ): void
```

Sets texture image 2D from pixels

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      pixels: ArrayBufferView | null,    ): void--><!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      pixels: ArrayBufferView | null,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pixels | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Pixel data |

<a id="teximage2d2"></a>

## texImage2D

```TypeScript
texImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      source: webgl.TexImageSource,
    ): void
```

Sets texture image 2D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void--><!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| source | [webgl.TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

<a id="teximage2d3"></a>

## texImage2D

```TypeScript
texImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      pboOffset: webgl.GLintptr,
    ): void
```

Sets texture image 2D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      pboOffset: webgl.GLintptr,    ): void--><!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      pboOffset: webgl.GLintptr,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pboOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | PBO offset |

<a id="teximage2d4"></a>

## texImage2D

```TypeScript
texImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      source: webgl.TexImageSource,
    ): void
```

Sets texture image 2D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void--><!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| source | [webgl.TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

<a id="teximage2d5"></a>

## texImage2D

```TypeScript
texImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      internalformat: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      border: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      srcData: ArrayBufferView,
      srcOffset: webgl.GLuint,
    ): void
```

Sets texture image 2D from ArrayBufferView with offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      srcData: ArrayBufferView,      srcOffset: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-texImage2D(      target: webgl.GLenum,      level: webgl.GLint,      internalformat: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      border: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      srcData: ArrayBufferView,      srcOffset: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Source offset |

<a id="texsubimage2d1"></a>

## texSubImage2D

```TypeScript
texSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      pixels: ArrayBufferView | null,
    ): void
```

Sets texture sub image 2D from pixels

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      pixels: ArrayBufferView | null,    ): void--><!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      pixels: ArrayBufferView | null,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pixels | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Pixel data |

<a id="texsubimage2d2"></a>

## texSubImage2D

```TypeScript
texSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      format: webgl.GLenum,
      type: webgl.GLenum,
      source: webgl.TexImageSource,
    ): void
```

Sets texture sub image 2D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void--><!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| source | [webgl.TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

<a id="texsubimage2d3"></a>

## texSubImage2D

```TypeScript
texSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      pboOffset: webgl.GLintptr,
    ): void
```

Sets texture sub image 2D from PBO offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      pboOffset: webgl.GLintptr,    ): void--><!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      pboOffset: webgl.GLintptr,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pboOffset | [webgl.GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | PBO offset |

<a id="texsubimage2d4"></a>

## texSubImage2D

```TypeScript
texSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      source: webgl.TexImageSource,
    ): void
```

Sets texture sub image 2D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void--><!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      source: webgl.TexImageSource,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| source | [webgl.TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

<a id="texsubimage2d5"></a>

## texSubImage2D

```TypeScript
texSubImage2D(
      target: webgl.GLenum,
      level: webgl.GLint,
      xoffset: webgl.GLint,
      yoffset: webgl.GLint,
      width: webgl.GLsizei,
      height: webgl.GLsizei,
      format: webgl.GLenum,
      type: webgl.GLenum,
      srcData: ArrayBufferView,
      srcOffset: webgl.GLuint,
    ): void
```

Sets texture sub image 2D from ArrayBufferView with offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      srcData: ArrayBufferView,      srcOffset: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-texSubImage2D(      target: webgl.GLenum,      level: webgl.GLint,      xoffset: webgl.GLint,      yoffset: webgl.GLint,      width: webgl.GLsizei,      height: webgl.GLsizei,      format: webgl.GLenum,      type: webgl.GLenum,      srcData: ArrayBufferView,      srcOffset: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [webgl.GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [webgl.GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [webgl.GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| srcData | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Source data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Source offset |

## uniform1fv

```TypeScript
uniform1fv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform1fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform1fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform1fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform1iv

```TypeScript
uniform1iv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Int32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform1iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform1iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform1iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform2fv

```TypeScript
uniform2fv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform2fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform2fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform2iv

```TypeScript
uniform2iv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Int32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform2iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform2iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform2iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform3fv

```TypeScript
uniform3fv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform3fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform3fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform3iv

```TypeScript
uniform3iv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Int32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform3iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform3iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform3iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform4fv

```TypeScript
uniform4fv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform4fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform4fv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniform4iv

```TypeScript
uniform4iv(
      location: webgl.WebGLUniformLocation | null,
      data: webgl.Int32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniform4iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniform4iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniform4iv(      location: webgl.WebGLUniformLocation | null,      data: webgl.Int32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| data | [webgl.Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix2fv

```TypeScript
uniformMatrix2fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniformMatrix2fv(      location: webgl.WebGLUniformLocation | null,      transpose: webgl.GLboolean,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniformMatrix2fv(      location: webgl.WebGLUniformLocation | null,      transpose: webgl.GLboolean,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix3fv

```TypeScript
uniformMatrix3fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniformMatrix3fv(      location: webgl.WebGLUniformLocation | null,      transpose: webgl.GLboolean,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniformMatrix3fv(      location: webgl.WebGLUniformLocation | null,      transpose: webgl.GLboolean,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |

## uniformMatrix4fv

```TypeScript
uniformMatrix4fv(
      location: webgl.WebGLUniformLocation | null,
      transpose: webgl.GLboolean,
      data: webgl.Float32List,
      srcOffset?: webgl.GLuint,
      srcLength?: webgl.GLuint,
    ): void
```

Sets uniformMatrix4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-WebGL2RenderingContextOverloads-uniformMatrix4fv(      location: webgl.WebGLUniformLocation | null,      transpose: webgl.GLboolean,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void--><!--Device-WebGL2RenderingContextOverloads-uniformMatrix4fv(      location: webgl.WebGLUniformLocation | null,      transpose: webgl.GLboolean,      data: webgl.Float32List,      srcOffset?: webgl.GLuint,      srcLength?: webgl.GLuint,    ): void-End-->

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL2

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [webgl.WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [webgl.GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Transpose |
| data | [webgl.Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Data |
| srcOffset | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source offset |
| srcLength | [webgl.GLuint](arkts-arkgraphics2d-gluint-t.md) | No | Source length |
