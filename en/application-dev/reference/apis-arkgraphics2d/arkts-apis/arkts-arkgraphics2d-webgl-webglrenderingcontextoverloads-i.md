# WebGLRenderingContextOverloads

WebGL 1.0

**Since:** 7

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## bufferData

```TypeScript
bufferData(target: GLenum, size: GLsizeiptr, usage: GLenum): void
```

Sets buffer data

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| size | [GLsizeiptr](arkts-arkgraphics2d-glsizeiptr-t.md) | Yes | Buffer size |
| usage | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer usage |

## bufferData

```TypeScript
bufferData(target: GLenum, data: BufferSource | null, usage: GLenum): void
```

Sets buffer data from BufferSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| data | BufferSource &#124; null | Yes | Buffer data |
| usage | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer usage |

## bufferSubData

```TypeScript
bufferSubData(target: GLenum, offset: GLintptr, data: BufferSource): void
```

Sets buffer sub data

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| offset | [GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |
| data | BufferSource | Yes | Data to set |

## compressedTexImage2D

```TypeScript
compressedTexImage2D(
      target: GLenum,
      level: GLint,
      internalformat: GLenum,
      width: GLsizei,
      height: GLsizei,
      border: GLint,
      data: ArrayBufferView,
    ): void
```

Compressed texture image 2D

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| data | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Compressed image data |

## compressedTexSubImage2D

```TypeScript
compressedTexSubImage2D(
      target: GLenum,
      level: GLint,
      xoffset: GLint,
      yoffset: GLint,
      width: GLsizei,
      height: GLsizei,
      format: GLenum,
      data: ArrayBufferView,
    ): void
```

Compressed texture sub image 2D

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | [Format](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-mindsporelite-format-e.md) |
| data | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) | Yes | Compressed image data |

## readPixels

```TypeScript
readPixels(
      x: GLint,
      y: GLint,
      width: GLsizei,
      height: GLsizei,
      format: GLenum,
      type: GLenum,
      pixels: ArrayBufferView | null,
    ): void
```

Reads pixels from the framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pixels | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Pixel buffer |

## texImage2D

```TypeScript
texImage2D(
      target: GLenum,
      level: GLint,
      internalformat: GLint,
      width: GLsizei,
      height: GLsizei,
      border: GLint,
      format: GLenum,
      type: GLenum,
      pixels: ArrayBufferView | null,
    ): void
```

Sets texture image 2D from pixels

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border |
| format | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pixels | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Pixel data |

## texImage2D

```TypeScript
texImage2D(
      target: GLenum,
      level: GLint,
      internalformat: GLint,
      format: GLenum,
      type: GLenum,
      source: TexImageSource,
    ): void
```

Sets texture image 2D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Internal format |
| format | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| source | [TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

## texSubImage2D

```TypeScript
texSubImage2D(
      target: GLenum,
      level: GLint,
      xoffset: GLint,
      yoffset: GLint,
      width: GLsizei,
      height: GLsizei,
      format: GLenum,
      type: GLenum,
      pixels: ArrayBufferView | null,
    ): void
```

Sets texture sub image 2D from pixels

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| format | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| pixels | [ArrayBufferView](../../apis-default/arkts-apis/arkts-lib-es5-arraybufferview-i.md) &#124; null | Yes | Pixel data |

## texSubImage2D

```TypeScript
texSubImage2D(
      target: GLenum,
      level: GLint,
      xoffset: GLint,
      yoffset: GLint,
      format: GLenum,
      type: GLenum,
      source: TexImageSource,
    ): void
```

Sets texture sub image 2D from TexImageSource

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| xoffset | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X offset |
| yoffset | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y offset |
| format | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel format |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Pixel type |
| source | [TexImageSource](arkts-arkgraphics2d-teximagesource-t.md) | Yes | Image source |

## uniform1fv

```TypeScript
uniform1fv(location: WebGLUniformLocation | null, v: Float32List): void
```

Sets uniform1fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Value array |

## uniform1iv

```TypeScript
uniform1iv(location: WebGLUniformLocation | null, v: Int32List): void
```

Sets uniform1iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Value array |

## uniform2fv

```TypeScript
uniform2fv(location: WebGLUniformLocation | null, v: Float32List): void
```

Sets uniform2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Value array |

## uniform2iv

```TypeScript
uniform2iv(location: WebGLUniformLocation | null, v: Int32List): void
```

Sets uniform2iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Value array |

## uniform3fv

```TypeScript
uniform3fv(location: WebGLUniformLocation | null, v: Float32List): void
```

Sets uniform3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Value array |

## uniform3iv

```TypeScript
uniform3iv(location: WebGLUniformLocation | null, v: Int32List): void
```

Sets uniform3iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Value array |

## uniform4fv

```TypeScript
uniform4fv(location: WebGLUniformLocation | null, v: Float32List): void
```

Sets uniform4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Value array |

## uniform4iv

```TypeScript
uniform4iv(location: WebGLUniformLocation | null, v: Int32List): void
```

Sets uniform4iv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| v | [Int32List](arkts-arkgraphics2d-int32list-t.md) | Yes | Value array |

## uniformMatrix2fv

```TypeScript
uniformMatrix2fv(location: WebGLUniformLocation | null, transpose: GLboolean, value: Float32List): void
```

Sets uniformMatrix2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to transpose |
| value | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Matrix value |

## uniformMatrix3fv

```TypeScript
uniformMatrix3fv(location: WebGLUniformLocation | null, transpose: GLboolean, value: Float32List): void
```

Sets uniformMatrix3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to transpose |
| value | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Matrix value |

## uniformMatrix4fv

```TypeScript
uniformMatrix4fv(location: WebGLUniformLocation | null, transpose: GLboolean, value: Float32List): void
```

Sets uniformMatrix4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| transpose | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to transpose |
| value | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Matrix value |
