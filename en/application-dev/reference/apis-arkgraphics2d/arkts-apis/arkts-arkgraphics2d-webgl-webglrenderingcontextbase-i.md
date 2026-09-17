# WebGLRenderingContextBase

WebGL 1.0

**Since:** 7

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## activeTexture

```TypeScript
activeTexture(texture: GLenum): void
```

Selects active texture unit

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| texture | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture unit to activate |

## attachShader

```TypeScript
attachShader(program: WebGLProgram, shader: WebGLShader): void
```

Attaches a shader to a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program to attach the shader to |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader to attach |

## bindAttribLocation

```TypeScript
bindAttribLocation(program: WebGLProgram, index: GLuint, name: string): void
```

Binds a generic vertex index to a named attribute variable

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program to bind the attribute location |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the generic vertex attribute |
| name | string | Yes | The name of the attribute variable |

## bindBuffer

```TypeScript
bindBuffer(target: GLenum, buffer: WebGLBuffer | null): void
```

Binds a buffer to a target

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The target to bind the buffer to |
| buffer | [WebGLBuffer](arkts-arkgraphics2d-webgl-webglbuffer-i.md) &#124; null | Yes | The buffer to bind |

## bindFramebuffer

```TypeScript
bindFramebuffer(target: GLenum, framebuffer: WebGLFramebuffer | null): void
```

Binds a framebuffer to a target

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The target to bind the framebuffer to |
| framebuffer | [WebGLFramebuffer](arkts-arkgraphics2d-webgl-webglframebuffer-i.md) &#124; null | Yes | The framebuffer to bind |

## bindRenderbuffer

```TypeScript
bindRenderbuffer(target: GLenum, renderbuffer: WebGLRenderbuffer | null): void
```

Binds a renderbuffer to a target

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The target to bind the renderbuffer to |
| renderbuffer | [WebGLRenderbuffer](arkts-arkgraphics2d-webgl-webglrenderbuffer-i.md) &#124; null | Yes | The renderbuffer to bind |

## bindTexture

```TypeScript
bindTexture(target: GLenum, texture: WebGLTexture | null): void
```

Binds a texture to a target

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The target to bind the texture to |
| texture | [WebGLTexture](arkts-arkgraphics2d-webgl-webgltexture-i.md) &#124; null | Yes | The texture to bind |

## blendColor

```TypeScript
blendColor(red: GLclampf, green: GLclampf, blue: GLclampf, alpha: GLclampf): void
```

Sets the blend color

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| red | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Red component |
| green | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Green component |
| blue | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Blue component |
| alpha | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Alpha component |

## blendFunc

```TypeScript
blendFunc(sfactor: GLenum, dfactor: GLenum): void
```

Sets the blend function

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sfactor | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Source blend factor |
| dfactor | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Destination blend factor |

## blendFuncSeparate

```TypeScript
blendFuncSeparate(srcRGB: GLenum, dstRGB: GLenum, srcAlpha: GLenum, dstAlpha: GLenum): void
```

Sets the blend function for RGB and alpha separately

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcRGB | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Source RGB blend factor |
| dstRGB | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Destination RGB blend factor |
| srcAlpha | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Source alpha blend factor |
| dstAlpha | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Destination alpha blend factor |

## checkFramebufferStatus

```TypeScript
checkFramebufferStatus(target: GLenum): GLenum
```

Returns the framebuffer status

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The target framebuffer |

**Return value:**

| Type | Description |
| --- | --- |
| [GLenum](arkts-arkgraphics2d-glenum-t.md) | The framebuffer status |

## clear

```TypeScript
clear(mask: GLbitfield): void
```

Clears buffers

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mask | [GLbitfield](arkts-arkgraphics2d-glbitfield-t.md) | Yes | Which buffers to clear |

## clearColor

```TypeScript
clearColor(red: GLclampf, green: GLclampf, blue: GLclampf, alpha: GLclampf): void
```

Sets the clear color

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| red | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Red component |
| green | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Green component |
| blue | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Blue component |
| alpha | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Alpha component |

## clearDepth

```TypeScript
clearDepth(depth: GLclampf): void
```

Sets the clear depth

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| depth | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Depth clear value |

## clearStencil

```TypeScript
clearStencil(s: GLint): void
```

Sets the clear stencil

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| s | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Stencil clear value |

## colorMask

```TypeScript
colorMask(red: GLboolean, green: GLboolean, blue: GLboolean, alpha: GLboolean): void
```

Sets the color mask

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| red | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to write red |
| green | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to write green |
| blue | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to write blue |
| alpha | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to write alpha |

## compileShader

```TypeScript
compileShader(shader: WebGLShader): void
```

Compiles a shader

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader to compile |

## copyTexImage2D

```TypeScript
copyTexImage2D(
      target: GLenum,
      level: GLint,
      internalformat: GLenum,
      x: GLint,
      y: GLint,
      width: GLsizei,
      height: GLsizei,
      border: GLint,
    ): void
```

Copies pixels from the framebuffer into a 2D texture image

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |
| internalformat | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |
| border | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Border width |

## copyTexSubImage2D

```TypeScript
copyTexSubImage2D(
      target: GLenum,
      level: GLint,
      xoffset: GLint,
      yoffset: GLint,
      x: GLint,
      y: GLint,
      width: GLsizei,
      height: GLsizei,
    ): void
```

Copies a portion of a texture image

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
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X coordinate |
| y | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y coordinate |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |

## createBuffer

```TypeScript
createBuffer(): WebGLBuffer | null
```

Creates a buffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLBuffer](arkts-arkgraphics2d-webgl-webglbuffer-i.md) &#124; null | The created buffer |

## createFramebuffer

```TypeScript
createFramebuffer(): WebGLFramebuffer | null
```

Creates a framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLFramebuffer](arkts-arkgraphics2d-webgl-webglframebuffer-i.md) &#124; null | The created framebuffer |

## createProgram

```TypeScript
createProgram(): WebGLProgram | null
```

Creates a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) &#124; null | The created program |

## createRenderbuffer

```TypeScript
createRenderbuffer(): WebGLRenderbuffer | null
```

Creates a renderbuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLRenderbuffer](arkts-arkgraphics2d-webgl-webglrenderbuffer-i.md) &#124; null | The created renderbuffer |

## createShader

```TypeScript
createShader(type: GLenum): WebGLShader | null
```

Creates a shader

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Shader type |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) &#124; null | The created shader |

## createTexture

```TypeScript
createTexture(): WebGLTexture | null
```

Creates a texture

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLTexture](arkts-arkgraphics2d-webgl-webgltexture-i.md) &#124; null | The created texture |

## cullFace

```TypeScript
cullFace(mode: GLenum): void
```

Sets the cull face mode

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Cull face mode |

## deleteBuffer

```TypeScript
deleteBuffer(buffer: WebGLBuffer | null): void
```

Deletes a buffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [WebGLBuffer](arkts-arkgraphics2d-webgl-webglbuffer-i.md) &#124; null | Yes | The buffer to delete |

## deleteFramebuffer

```TypeScript
deleteFramebuffer(framebuffer: WebGLFramebuffer | null): void
```

Deletes a framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| framebuffer | [WebGLFramebuffer](arkts-arkgraphics2d-webgl-webglframebuffer-i.md) &#124; null | Yes | The framebuffer to delete |

## deleteProgram

```TypeScript
deleteProgram(program: WebGLProgram | null): void
```

Deletes a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) &#124; null | Yes | The program to delete |

## deleteRenderbuffer

```TypeScript
deleteRenderbuffer(renderbuffer: WebGLRenderbuffer | null): void
```

Deletes a renderbuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| renderbuffer | [WebGLRenderbuffer](arkts-arkgraphics2d-webgl-webglrenderbuffer-i.md) &#124; null | Yes | The renderbuffer to delete |

## deleteShader

```TypeScript
deleteShader(shader: WebGLShader | null): void
```

Deletes a shader

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) &#124; null | Yes | The shader to delete |

## deleteTexture

```TypeScript
deleteTexture(texture: WebGLTexture | null): void
```

Deletes a texture

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| texture | [WebGLTexture](arkts-arkgraphics2d-webgl-webgltexture-i.md) &#124; null | Yes | The texture to delete |

## depthFunc

```TypeScript
depthFunc(func: GLenum): void
```

Sets the depth function

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| func | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Depth function |

## depthMask

```TypeScript
depthMask(flag: GLboolean): void
```

Sets the depth mask

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to write to depth buffer |

## depthRange

```TypeScript
depthRange(zNear: GLclampf, zFar: GLclampf): void
```

Sets the depth range

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zNear | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Near depth |
| zFar | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Far depth |

## detachShader

```TypeScript
detachShader(program: WebGLProgram, shader: WebGLShader): void
```

Detaches a shader from a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader to detach |

## disable

```TypeScript
disable(cap: GLenum): void
```

Disables a capability

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cap | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The capability to disable |

## disableVertexAttribArray

```TypeScript
disableVertexAttribArray(index: GLuint): void
```

Disables a vertex attribute array

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the vertex attribute |

## drawArrays

```TypeScript
drawArrays(mode: GLenum, first: GLint, count: GLsizei): void
```

Draws arrays

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Drawing mode |
| first | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Starting index |
| count | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Number of indices |

## drawElements

```TypeScript
drawElements(mode: GLenum, count: GLsizei, type: GLenum, offset: GLintptr): void
```

Draws elements

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Drawing mode |
| count | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Number of indices |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Type of indices |
| offset | [GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset in the buffer |

## enable

```TypeScript
enable(cap: GLenum): void
```

Enables a capability

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cap | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The capability to enable |

## enableVertexAttribArray

```TypeScript
enableVertexAttribArray(index: GLuint): void
```

Enables a vertex attribute array

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the vertex attribute |

## finish

```TypeScript
finish(): void
```

Signals the completion of GL rendering

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## flush

```TypeScript
flush(): void
```

Forces all pending GL commands to be executed

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## framebufferRenderbuffer

```TypeScript
framebufferRenderbuffer(
      target: GLenum,
      attachment: GLenum,
      renderbuffertarget: GLenum,
      renderbuffer: WebGLRenderbuffer | null,
    ): void
```

Attaches a renderbuffer to a framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Framebuffer target |
| attachment | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Attachment point |
| renderbuffertarget | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Renderbuffer target |
| renderbuffer | [WebGLRenderbuffer](arkts-arkgraphics2d-webgl-webglrenderbuffer-i.md) &#124; null | Yes | The renderbuffer to attach |

## framebufferTexture2D

```TypeScript
framebufferTexture2D(
      target: GLenum,
      attachment: GLenum,
      textarget: GLenum,
      texture: WebGLTexture | null,
      level: GLint,
    ): void
```

Attaches a texture to a framebuffer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Framebuffer target |
| attachment | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Attachment point |
| textarget | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| texture | [WebGLTexture](arkts-arkgraphics2d-webgl-webgltexture-i.md) &#124; null | Yes | The texture to attach |
| level | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Mipmap level |

## frontFace

```TypeScript
frontFace(mode: GLenum): void
```

Sets the front face direction

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Front face mode |

## generateMipmap

```TypeScript
generateMipmap(target: GLenum): void
```

Generates mipmaps for a texture

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |

## getActiveAttrib

```TypeScript
getActiveAttrib(program: WebGLProgram, index: GLuint): WebGLActiveInfo | null
```

Returns information about an active attribute

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the attribute |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLActiveInfo](arkts-arkgraphics2d-webgl-webglactiveinfo-i.md) &#124; null | Information about the active attribute |

## getActiveUniform

```TypeScript
getActiveUniform(program: WebGLProgram, index: GLuint): WebGLActiveInfo | null
```

Returns information about an active uniform

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the uniform |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLActiveInfo](arkts-arkgraphics2d-webgl-webglactiveinfo-i.md) &#124; null | Information about the active uniform |

## getAttachedShaders

```TypeScript
getAttachedShaders(program: WebGLProgram): WebGLShader[] | null
```

Returns the shaders attached to a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md)[] &#124; null | Array of attached shaders |

## getAttribLocation

```TypeScript
getAttribLocation(program: WebGLProgram, name: string): GLint
```

Returns the location of an attribute variable

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| name | string | Yes | The name of the attribute |

**Return value:**

| Type | Description |
| --- | --- |
| [GLint](arkts-arkgraphics2d-glint-t.md) | The location of the attribute |

## getBufferParameter

```TypeScript
getBufferParameter(target: GLenum, pname: GLenum): any
```

Returns a buffer parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Buffer target |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The buffer parameter value |

## getContextAttributes

```TypeScript
getContextAttributes(): WebGLContextAttributes | null
```

Returns the WebGLContextAttributes for the current context

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLContextAttributes](arkts-arkgraphics2d-webgl-webglcontextattributes-i.md) &#124; null | The WebGLContextAttributes object |

## getError

```TypeScript
getError(): GLenum
```

Returns the error code

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| [GLenum](arkts-arkgraphics2d-glenum-t.md) | The error code |

## getExtension

```TypeScript
getExtension(name: string): any
```

Enables a WebGL extension

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The name of the extension |

**Return value:**

| Type | Description |
| --- | --- |
| any | The extension object if available |

## getFramebufferAttachmentParameter

```TypeScript
getFramebufferAttachmentParameter(target: GLenum, attachment: GLenum, pname: GLenum): any
```

Returns a framebuffer attachment parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Framebuffer target |
| attachment | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Attachment point |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The attachment parameter value |

## getParameter

```TypeScript
getParameter(pname: GLenum): any
```

Returns a parameter value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The parameter value |

## getProgramInfoLog

```TypeScript
getProgramInfoLog(program: WebGLProgram): string | null
```

Returns the program info log

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | The program info log |

## getProgramParameter

```TypeScript
getProgramParameter(program: WebGLProgram, pname: GLenum): any
```

Returns a program parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The program parameter value |

## getRenderbufferParameter

```TypeScript
getRenderbufferParameter(target: GLenum, pname: GLenum): any
```

Returns a renderbuffer parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Renderbuffer target |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The renderbuffer parameter value |

## getShaderInfoLog

```TypeScript
getShaderInfoLog(shader: WebGLShader): string | null
```

Returns the shader info log

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | The shader info log |

## getShaderParameter

```TypeScript
getShaderParameter(shader: WebGLShader, pname: GLenum): any
```

Returns a shader parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The shader parameter value |

## getShaderPrecisionFormat

```TypeScript
getShaderPrecisionFormat(shadertype: GLenum, precisiontype: GLenum): WebGLShaderPrecisionFormat | null
```

Returns the shader precision format

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shadertype | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Shader type |
| precisiontype | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Precision type |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLShaderPrecisionFormat](arkts-arkgraphics2d-webgl-webglshaderprecisionformat-i.md) &#124; null | The precision format |

## getShaderSource

```TypeScript
getShaderSource(shader: WebGLShader): string | null
```

Returns the shader source

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | The shader source |

## getSupportedExtensions

```TypeScript
getSupportedExtensions(): string[] | null
```

Returns a list of supported extensions

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| string[] &#124; null | List of supported extensions |

## getTexParameter

```TypeScript
getTexParameter(target: GLenum, pname: GLenum): any
```

Returns a texture parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The texture parameter value |

## getUniform

```TypeScript
getUniform(program: WebGLProgram, location: WebGLUniformLocation): any
```

Returns the value of a uniform

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) | Yes | The uniform location |

**Return value:**

| Type | Description |
| --- | --- |
| any | The uniform value |

## getUniformLocation

```TypeScript
getUniformLocation(program: WebGLProgram, name: string): WebGLUniformLocation | null
```

Returns the location of a uniform variable

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program |
| name | string | Yes | The name of the uniform |

**Return value:**

| Type | Description |
| --- | --- |
| [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | The uniform location |

## getVertexAttrib

```TypeScript
getVertexAttrib(index: GLuint, pname: GLenum): any
```

Returns a vertex attribute parameter

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the vertex attribute |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| any | The vertex attribute parameter value |

## getVertexAttribOffset

```TypeScript
getVertexAttribOffset(index: GLuint, pname: GLenum): GLintptr
```

Returns the offset of a vertex attribute

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | The index of the vertex attribute |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |

**Return value:**

| Type | Description |
| --- | --- |
| [GLintptr](arkts-arkgraphics2d-glintptr-t.md) | The vertex attribute offset |

## hint

```TypeScript
hint(target: GLenum, mode: GLenum): void
```

Sets a hint

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Hint target |
| mode | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Hint mode |

## isBuffer

```TypeScript
isBuffer(buffer: WebGLBuffer | null): GLboolean
```

Returns whether a buffer is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | [WebGLBuffer](arkts-arkgraphics2d-webgl-webglbuffer-i.md) &#124; null | Yes | The buffer |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the buffer is valid |

## isContextLost

```TypeScript
isContextLost(): boolean
```

Returns whether the context is lost

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the context is lost |

## isEnabled

```TypeScript
isEnabled(cap: GLenum): GLboolean
```

Returns whether a capability is enabled

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cap | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | The capability |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the capability is enabled |

## isFramebuffer

```TypeScript
isFramebuffer(framebuffer: WebGLFramebuffer | null): GLboolean
```

Returns whether a framebuffer is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| framebuffer | [WebGLFramebuffer](arkts-arkgraphics2d-webgl-webglframebuffer-i.md) &#124; null | Yes | The framebuffer |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the framebuffer is valid |

## isProgram

```TypeScript
isProgram(program: WebGLProgram | null): GLboolean
```

Returns whether a program is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) &#124; null | Yes | The program |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the program is valid |

## isRenderbuffer

```TypeScript
isRenderbuffer(renderbuffer: WebGLRenderbuffer | null): GLboolean
```

Returns whether a renderbuffer is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| renderbuffer | [WebGLRenderbuffer](arkts-arkgraphics2d-webgl-webglrenderbuffer-i.md) &#124; null | Yes | The renderbuffer |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the renderbuffer is valid |

## isShader

```TypeScript
isShader(shader: WebGLShader | null): GLboolean
```

Returns whether a shader is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) &#124; null | Yes | The shader |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the shader is valid |

## isTexture

```TypeScript
isTexture(texture: WebGLTexture | null): GLboolean
```

Returns whether a texture is valid

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| texture | [WebGLTexture](arkts-arkgraphics2d-webgl-webgltexture-i.md) &#124; null | Yes | The texture |

**Return value:**

| Type | Description |
| --- | --- |
| [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Whether the texture is valid |

## lineWidth

```TypeScript
lineWidth(width: GLfloat): void
```

Sets the line width

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Line width |

## linkProgram

```TypeScript
linkProgram(program: WebGLProgram): void
```

Links a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program to link |

## pixelStorei

```TypeScript
pixelStorei(pname: GLenum, param: GLint | GLboolean): void
```

Sets pixel storage parameters

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |
| param | [GLint](arkts-arkgraphics2d-glint-t.md) &#124; [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Parameter value |

## polygonOffset

```TypeScript
polygonOffset(factor: GLfloat, units: GLfloat): void
```

Sets the polygon offset

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| factor | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Scale factor |
| units | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Units |

## renderbufferStorage

```TypeScript
renderbufferStorage(target: GLenum, internalformat: GLenum, width: GLsizei, height: GLsizei): void
```

Sets the renderbuffer storage

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Renderbuffer target |
| internalformat | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Internal format |
| width | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Width |
| height | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Height |

## sampleCoverage

```TypeScript
sampleCoverage(value: GLclampf, invert: GLboolean): void
```

Sets the sample coverage

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GLclampf](arkts-arkgraphics2d-glclampf-t.md) | Yes | Coverage value |
| invert | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Invert coverage |

## scissor

```TypeScript
scissor(x: GLint, y: GLint, width: GLsizei, height: GLsizei): void
```

Sets the scissor box

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

## shaderSource

```TypeScript
shaderSource(shader: WebGLShader, source: string): void
```

Sets the shader source

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shader | [WebGLShader](arkts-arkgraphics2d-webgl-webglshader-i.md) | Yes | The shader |
| source | string | Yes | The source code |

## stencilFunc

```TypeScript
stencilFunc(func: GLenum, ref: GLint, mask: GLuint): void
```

Sets the stencil function

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| func | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Stencil function |
| ref | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Reference value |
| mask | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) |

## stencilFuncSeparate

```TypeScript
stencilFuncSeparate(face: GLenum, func: GLenum, ref: GLint, mask: GLuint): void
```

Sets the stencil function separately for front and back faces

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| face | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Face mode |
| func | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Stencil function |
| ref | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Reference value |
| mask | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) |

## stencilMask

```TypeScript
stencilMask(mask: GLuint): void
```

Sets the stencil mask

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mask | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Stencil mask |

## stencilMaskSeparate

```TypeScript
stencilMaskSeparate(face: GLenum, mask: GLuint): void
```

Sets the stencil mask separately for front and back faces

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| face | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Face mode |
| mask | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Stencil mask |

## stencilOp

```TypeScript
stencilOp(fail: GLenum, zfail: GLenum, zpass: GLenum): void
```

Sets the stencil operation

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fail | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Operation when stencil test fails |
| zfail | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Operation when depth test fails |
| zpass | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Operation when depth test passes |

## stencilOpSeparate

```TypeScript
stencilOpSeparate(face: GLenum, fail: GLenum, zfail: GLenum, zpass: GLenum): void
```

Sets the stencil operation separately for front and back faces

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| face | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Face mode |
| fail | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Operation when stencil test fails |
| zfail | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Operation when depth test fails |
| zpass | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Operation when depth test passes |

## texParameterf

```TypeScript
texParameterf(target: GLenum, pname: GLenum, param: GLfloat): void
```

Sets a texture parameter (float)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |
| param | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Parameter value |

## texParameteri

```TypeScript
texParameteri(target: GLenum, pname: GLenum, param: GLint): void
```

Sets a texture parameter (int)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Texture target |
| pname | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Parameter name |
| param | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Parameter value |

## uniform1f

```TypeScript
uniform1f(location: WebGLUniformLocation | null, x: GLfloat): void
```

Sets a uniform1f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |

## uniform1i

```TypeScript
uniform1i(location: WebGLUniformLocation | null, x: GLint): void
```

Sets a uniform1i value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X value |

## uniform2f

```TypeScript
uniform2f(location: WebGLUniformLocation | null, x: GLfloat, y: GLfloat): void
```

Sets a uniform2f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |
| y | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Y value |

## uniform2i

```TypeScript
uniform2i(location: WebGLUniformLocation | null, x: GLint, y: GLint): void
```

Sets a uniform2i value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X value |
| y | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y value |

## uniform3f

```TypeScript
uniform3f(location: WebGLUniformLocation | null, x: GLfloat, y: GLfloat, z: GLfloat): void
```

Sets a uniform3f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |
| y | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Y value |
| z | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Z value |

## uniform3i

```TypeScript
uniform3i(location: WebGLUniformLocation | null, x: GLint, y: GLint, z: GLint): void
```

Sets a uniform3i value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X value |
| y | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y value |
| z | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z value |

## uniform4f

```TypeScript
uniform4f(location: WebGLUniformLocation | null, x: GLfloat, y: GLfloat, z: GLfloat, w: GLfloat): void
```

Sets a uniform4f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |
| y | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Y value |
| z | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Z value |
| w | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | W value |

## uniform4i

```TypeScript
uniform4i(location: WebGLUniformLocation | null, x: GLint, y: GLint, z: GLint, w: GLint): void
```

Sets a uniform4i value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| location | [WebGLUniformLocation](arkts-arkgraphics2d-webgl-webgluniformlocation-i.md) &#124; null | Yes | Uniform location |
| x | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | X value |
| y | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Y value |
| z | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Z value |
| w | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | W value |

## useProgram

```TypeScript
useProgram(program: WebGLProgram | null): void
```

Uses a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) &#124; null | Yes | The program to use |

## validateProgram

```TypeScript
validateProgram(program: WebGLProgram): void
```

Validates a program

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| program | [WebGLProgram](arkts-arkgraphics2d-webgl-webglprogram-i.md) | Yes | The program to validate |

## vertexAttrib1f

```TypeScript
vertexAttrib1f(index: GLuint, x: GLfloat): void
```

Sets a vertex attrib1f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |

## vertexAttrib1fv

```TypeScript
vertexAttrib1fv(index: GLuint, values: Float32List): void
```

Sets a vertex attrib1fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| values | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Values |

## vertexAttrib2f

```TypeScript
vertexAttrib2f(index: GLuint, x: GLfloat, y: GLfloat): void
```

Sets a vertex attrib2f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |
| y | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Y value |

## vertexAttrib2fv

```TypeScript
vertexAttrib2fv(index: GLuint, values: Float32List): void
```

Sets a vertex attrib2fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| values | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Values |

## vertexAttrib3f

```TypeScript
vertexAttrib3f(index: GLuint, x: GLfloat, y: GLfloat, z: GLfloat): void
```

Sets a vertex attrib3f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |
| y | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Y value |
| z | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Z value |

## vertexAttrib3fv

```TypeScript
vertexAttrib3fv(index: GLuint, values: Float32List): void
```

Sets a vertex attrib3fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| values | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Values |

## vertexAttrib4f

```TypeScript
vertexAttrib4f(index: GLuint, x: GLfloat, y: GLfloat, z: GLfloat, w: GLfloat): void
```

Sets a vertex attrib4f value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| x | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | X value |
| y | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Y value |
| z | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | Z value |
| w | [GLfloat](arkts-arkgraphics2d-glfloat-t.md) | Yes | W value |

## vertexAttrib4fv

```TypeScript
vertexAttrib4fv(index: GLuint, values: Float32List): void
```

Sets a vertex attrib4fv value

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| values | [Float32List](arkts-arkgraphics2d-float32list-t.md) | Yes | Values |

## vertexAttribPointer

```TypeScript
vertexAttribPointer(
      index: GLuint,
      size: GLint,
      type: GLenum,
      normalized: GLboolean,
      stride: GLsizei,
      offset: GLintptr,
    ): void
```

Sets vertex attrib pointer

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | [GLuint](arkts-arkgraphics2d-gluint-t.md) | Yes | Vertex attribute index |
| size | [GLint](arkts-arkgraphics2d-glint-t.md) | Yes | Number of components |
| type | [GLenum](arkts-arkgraphics2d-glenum-t.md) | Yes | Data type |
| normalized | [GLboolean](arkts-arkgraphics2d-glboolean-t.md) | Yes | Whether to normalize |
| stride | [GLsizei](arkts-arkgraphics2d-glsizei-t.md) | Yes | Stride |
| offset | [GLintptr](arkts-arkgraphics2d-glintptr-t.md) | Yes | Offset |

## viewport

```TypeScript
viewport(x: GLint, y: GLint, width: GLsizei, height: GLsizei): void
```

Sets the viewport

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

## ACTIVE_ATTRIBUTES

```TypeScript
readonly ACTIVE_ATTRIBUTES: GLenum
```

Active Attributes

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ACTIVE_TEXTURE

```TypeScript
readonly ACTIVE_TEXTURE: GLenum
```

Active texture

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ACTIVE_UNIFORMS

```TypeScript
readonly ACTIVE_UNIFORMS: GLenum
```

Active Uniforms

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ALIASED_LINE_WIDTH_RANGE

```TypeScript
readonly ALIASED_LINE_WIDTH_RANGE: GLenum
```

Aliased line width range

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ALIASED_POINT_SIZE_RANGE

```TypeScript
readonly ALIASED_POINT_SIZE_RANGE: GLenum
```

Aliased point size range

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ALPHA

```TypeScript
readonly ALPHA: GLenum
```

Pixel format: alpha

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ALPHA_BITS

```TypeScript
readonly ALPHA_BITS: GLenum
```

Alpha bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ALWAYS

```TypeScript
readonly ALWAYS: GLenum
```

Comparison function: always

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ARRAY_BUFFER

```TypeScript
readonly ARRAY_BUFFER: GLenum
```

Buffer target: array buffer

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ARRAY_BUFFER_BINDING

```TypeScript
readonly ARRAY_BUFFER_BINDING: GLenum
```

Array buffer binding point

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ATTACHED_SHADERS

```TypeScript
readonly ATTACHED_SHADERS: GLenum
```

Attached Shaders

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BACK

```TypeScript
readonly BACK: GLenum
```

Face mode: back

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND

```TypeScript
readonly BLEND: GLenum
```

Enable cap: blend

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_COLOR

```TypeScript
readonly BLEND_COLOR: GLenum
```

Blend color

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_DST_ALPHA

```TypeScript
readonly BLEND_DST_ALPHA: GLenum
```

Destination alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_DST_RGB

```TypeScript
readonly BLEND_DST_RGB: GLenum
```

Destination RGB blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_EQUATION

```TypeScript
readonly BLEND_EQUATION: GLenum
```

Blend equation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_EQUATION_ALPHA

```TypeScript
readonly BLEND_EQUATION_ALPHA: GLenum
```

Blend equation for alpha

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_EQUATION_RGB

```TypeScript
readonly BLEND_EQUATION_RGB: GLenum
```

Blend equation for RGB

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_SRC_ALPHA

```TypeScript
readonly BLEND_SRC_ALPHA: GLenum
```

Source alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLEND_SRC_RGB

```TypeScript
readonly BLEND_SRC_RGB: GLenum
```

Source RGB blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BLUE_BITS

```TypeScript
readonly BLUE_BITS: GLenum
```

Blue bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BOOL

```TypeScript
readonly BOOL: GLenum
```

Uniform type: bool

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BOOL_VEC2

```TypeScript
readonly BOOL_VEC2: GLenum
```

Uniform type: bool vec2

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BOOL_VEC3

```TypeScript
readonly BOOL_VEC3: GLenum
```

Uniform type: bool vec3

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BOOL_VEC4

```TypeScript
readonly BOOL_VEC4: GLenum
```

Uniform type: bool vec4

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BROWSER_DEFAULT_WEBGL

```TypeScript
readonly BROWSER_DEFAULT_WEBGL: GLenum
```

Browser default WebGL

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BUFFER_SIZE

```TypeScript
readonly BUFFER_SIZE: GLenum
```

Buffer parameter: buffer size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BUFFER_USAGE

```TypeScript
readonly BUFFER_USAGE: GLenum
```

Buffer parameter: buffer usage

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## BYTE

```TypeScript
readonly BYTE: GLenum
```

Data type: byte

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## canvas

```TypeScript
readonly canvas: HTMLCanvasElement | OffscreenCanvas
```

The canvas element

**Type:** HTMLCanvasElement &#124; OffscreenCanvas

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CCW

```TypeScript
readonly CCW: GLenum
```

Front face: counter-clockwise

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CLAMP_TO_EDGE

```TypeScript
readonly CLAMP_TO_EDGE: GLenum
```

Texture wrap: clamp to edge

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## COLOR_ATTACHMENT0

```TypeScript
readonly COLOR_ATTACHMENT0: GLenum
```

Color Attachment0

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## COLOR_BUFFER_BIT

```TypeScript
readonly COLOR_BUFFER_BIT: GLenum
```

Color buffer clear value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## COLOR_CLEAR_VALUE

```TypeScript
readonly COLOR_CLEAR_VALUE: GLenum
```

Color clear value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## COLOR_WRITEMASK

```TypeScript
readonly COLOR_WRITEMASK: GLenum
```

Color write mask

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## COMPILE_STATUS

```TypeScript
readonly COMPILE_STATUS: GLenum
```

Compile status

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## COMPRESSED_TEXTURE_FORMATS

```TypeScript
readonly COMPRESSED_TEXTURE_FORMATS: GLenum
```

Compressed texture formats

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CONSTANT_ALPHA

```TypeScript
readonly CONSTANT_ALPHA: GLenum
```

Constant alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CONSTANT_COLOR

```TypeScript
readonly CONSTANT_COLOR: GLenum
```

Constant color blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CONTEXT_LOST_WEBGL

```TypeScript
readonly CONTEXT_LOST_WEBGL: GLenum
```

Context lost WebGL

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CULL_FACE

```TypeScript
readonly CULL_FACE: GLenum
```

Enable cap: cull face

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CULL_FACE_MODE

```TypeScript
readonly CULL_FACE_MODE: GLenum
```

Cull face mode

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CURRENT_PROGRAM

```TypeScript
readonly CURRENT_PROGRAM: GLenum
```

Current Program

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CURRENT_VERTEX_ATTRIB

```TypeScript
readonly CURRENT_VERTEX_ATTRIB: GLenum
```

Current vertex attribute

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## CW

```TypeScript
readonly CW: GLenum
```

Front face: clockwise

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DECR

```TypeScript
readonly DECR: GLenum
```

Stencil operation: decrement

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DECR_WRAP

```TypeScript
readonly DECR_WRAP: GLenum
```

Stencil operation: decrement wrap

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DELETE_STATUS

```TypeScript
readonly DELETE_STATUS: GLenum
```

Delete Status

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_ATTACHMENT

```TypeScript
readonly DEPTH_ATTACHMENT: GLenum
```

Depth Attachment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_BITS

```TypeScript
readonly DEPTH_BITS: GLenum
```

Depth bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_BUFFER_BIT

```TypeScript
readonly DEPTH_BUFFER_BIT: GLenum
```

Depth buffer clear value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_CLEAR_VALUE

```TypeScript
readonly DEPTH_CLEAR_VALUE: GLenum
```

Depth clear value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_COMPONENT

```TypeScript
readonly DEPTH_COMPONENT: GLenum
```

Pixel format: depth component

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_COMPONENT16

```TypeScript
readonly DEPTH_COMPONENT16: GLenum
```

Renderbuffer internal format: depth component16

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_FUNC

```TypeScript
readonly DEPTH_FUNC: GLenum
```

Depth function

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_RANGE

```TypeScript
readonly DEPTH_RANGE: GLenum
```

Depth range

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_STENCIL

```TypeScript
readonly DEPTH_STENCIL: GLenum
```

Renderbuffer internal format: depth stencil

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_STENCIL_ATTACHMENT

```TypeScript
readonly DEPTH_STENCIL_ATTACHMENT: GLenum
```

Depth Stencil Attachment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DEPTH_TEST

```TypeScript
readonly DEPTH_TEST: GLenum
```

Enable cap: depth test

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Test API:** This API is used only in automated test scripts.

## DEPTH_WRITEMASK

```TypeScript
readonly DEPTH_WRITEMASK: GLenum
```

Depth write mask

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DITHER

```TypeScript
readonly DITHER: GLenum
```

Enable cap: dither

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DONT_CARE

```TypeScript
readonly DONT_CARE: GLenum
```

Hint: don't care

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## drawingBufferHeight

```TypeScript
readonly drawingBufferHeight: GLsizei
```

Drawing buffer height

**Type:** [GLsizei](arkts-arkgraphics2d-glsizei-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## drawingBufferWidth

```TypeScript
readonly drawingBufferWidth: GLsizei
```

Drawing buffer width

**Type:** [GLsizei](arkts-arkgraphics2d-glsizei-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DST_ALPHA

```TypeScript
readonly DST_ALPHA: GLenum
```

Destination alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DST_COLOR

```TypeScript
readonly DST_COLOR: GLenum
```

Destination color blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## DYNAMIC_DRAW

```TypeScript
readonly DYNAMIC_DRAW: GLenum
```

Buffer usage: dynamic draw

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ELEMENT_ARRAY_BUFFER

```TypeScript
readonly ELEMENT_ARRAY_BUFFER: GLenum
```

Buffer target: element array buffer

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ELEMENT_ARRAY_BUFFER_BINDING

```TypeScript
readonly ELEMENT_ARRAY_BUFFER_BINDING: GLenum
```

Element array buffer binding point

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## EQUAL

```TypeScript
readonly EQUAL: GLenum
```

Comparison function: equal

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FASTEST

```TypeScript
readonly FASTEST: GLenum
```

Hint: fastest

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT

```TypeScript
readonly FLOAT: GLenum
```

Data type: float

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT_MAT2

```TypeScript
readonly FLOAT_MAT2: GLenum
```

Uniform type: float mat2

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT_MAT3

```TypeScript
readonly FLOAT_MAT3: GLenum
```

Uniform type: float mat3

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT_MAT4

```TypeScript
readonly FLOAT_MAT4: GLenum
```

Uniform type: float mat4

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT_VEC2

```TypeScript
readonly FLOAT_VEC2: GLenum
```

Uniform type: float vec2

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT_VEC3

```TypeScript
readonly FLOAT_VEC3: GLenum
```

Uniform type: float vec3

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FLOAT_VEC4

```TypeScript
readonly FLOAT_VEC4: GLenum
```

Uniform type: float vec4

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAGMENT_SHADER

```TypeScript
readonly FRAGMENT_SHADER: GLenum
```

Shader type: fragment shader

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER

```TypeScript
readonly FRAMEBUFFER: GLenum
```

Framebuffer target

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_ATTACHMENT_OBJECT_NAME

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_OBJECT_NAME: GLenum
```

Framebuffer attachment parameter: object name

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_ATTACHMENT_OBJECT_TYPE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_OBJECT_TYPE: GLenum
```

Framebuffer attachment parameter: object type

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_ATTACHMENT_TEXTURE_CUBE_MAP_FACE

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_TEXTURE_CUBE_MAP_FACE: GLenum
```

Framebuffer Attachment Texture Cube Map Face

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_ATTACHMENT_TEXTURE_LEVEL

```TypeScript
readonly FRAMEBUFFER_ATTACHMENT_TEXTURE_LEVEL: GLenum
```

Framebuffer Attachment Texture Level

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_BINDING

```TypeScript
readonly FRAMEBUFFER_BINDING: GLenum
```

Framebuffer binding

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_COMPLETE

```TypeScript
readonly FRAMEBUFFER_COMPLETE: GLenum
```

Framebuffer Complete

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_INCOMPLETE_ATTACHMENT

```TypeScript
readonly FRAMEBUFFER_INCOMPLETE_ATTACHMENT: GLenum
```

Framebuffer status: incomplete attachment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_INCOMPLETE_DIMENSIONS

```TypeScript
readonly FRAMEBUFFER_INCOMPLETE_DIMENSIONS: GLenum
```

Framebuffer status: incomplete dimensions

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_INCOMPLETE_MISSING_ATTACHMENT

```TypeScript
readonly FRAMEBUFFER_INCOMPLETE_MISSING_ATTACHMENT: GLenum
```

Framebuffer status: incomplete missing attachment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRAMEBUFFER_UNSUPPORTED

```TypeScript
readonly FRAMEBUFFER_UNSUPPORTED: GLenum
```

Framebuffer status: unsupported

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRONT

```TypeScript
readonly FRONT: GLenum
```

Face mode: front

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRONT_AND_BACK

```TypeScript
readonly FRONT_AND_BACK: GLenum
```

Face mode: front and back

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FRONT_FACE

```TypeScript
readonly FRONT_FACE: GLenum
```

Front face mode

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FUNC_ADD

```TypeScript
readonly FUNC_ADD: GLenum
```

Blend equation: add

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FUNC_REVERSE_SUBTRACT

```TypeScript
readonly FUNC_REVERSE_SUBTRACT: GLenum
```

Blend equation: reverse subtract

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## FUNC_SUBTRACT

```TypeScript
readonly FUNC_SUBTRACT: GLenum
```

Blend equation: subtract

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## GENERATE_MIPMAP_HINT

```TypeScript
readonly GENERATE_MIPMAP_HINT: GLenum
```

Generate mipmap hint

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## GEQUAL

```TypeScript
readonly GEQUAL: GLenum
```

Comparison function: greater or equal

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## GREATER

```TypeScript
readonly GREATER: GLenum
```

Comparison function: greater

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## GREEN_BITS

```TypeScript
readonly GREEN_BITS: GLenum
```

Green bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## HIGH_FLOAT

```TypeScript
readonly HIGH_FLOAT: GLenum
```

Precision: high float

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## HIGH_INT

```TypeScript
readonly HIGH_INT: GLenum
```

Precision: high int

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## IMPLEMENTATION_COLOR_READ_FORMAT

```TypeScript
readonly IMPLEMENTATION_COLOR_READ_FORMAT: GLenum
```

Implementation color read format

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## IMPLEMENTATION_COLOR_READ_TYPE

```TypeScript
readonly IMPLEMENTATION_COLOR_READ_TYPE: GLenum
```

Implementation color read type

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INCR

```TypeScript
readonly INCR: GLenum
```

Stencil operation: increment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INCR_WRAP

```TypeScript
readonly INCR_WRAP: GLenum
```

Stencil operation: increment wrap

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INT

```TypeScript
readonly INT: GLenum
```

Data type: int

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INT_VEC2

```TypeScript
readonly INT_VEC2: GLenum
```

Uniform type: int vec2

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INT_VEC3

```TypeScript
readonly INT_VEC3: GLenum
```

Uniform type: int vec3

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INT_VEC4

```TypeScript
readonly INT_VEC4: GLenum
```

Uniform type: int vec4

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INVALID_ENUM

```TypeScript
readonly INVALID_ENUM: GLenum
```

Error code: invalid enum

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INVALID_FRAMEBUFFER_OPERATION

```TypeScript
readonly INVALID_FRAMEBUFFER_OPERATION: GLenum
```

Error code: invalid framebuffer operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INVALID_OPERATION

```TypeScript
readonly INVALID_OPERATION: GLenum
```

Error code: invalid operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INVALID_VALUE

```TypeScript
readonly INVALID_VALUE: GLenum
```

Error code: invalid value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## INVERT

```TypeScript
readonly INVERT: GLenum
```

Stencil operation: invert

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## KEEP

```TypeScript
readonly KEEP: GLenum
```

Stencil operation: keep

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LEQUAL

```TypeScript
readonly LEQUAL: GLenum
```

Comparison function: less or equal

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LESS

```TypeScript
readonly LESS: GLenum
```

Comparison function: less

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINE_LOOP

```TypeScript
readonly LINE_LOOP: GLenum
```

Primitive type: line strip

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINE_STRIP

```TypeScript
readonly LINE_STRIP: GLenum
```

Primitive type: line strip

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINE_WIDTH

```TypeScript
readonly LINE_WIDTH: GLenum
```

Line width

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINEAR

```TypeScript
readonly LINEAR: GLenum
```

Filter: linear

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINEAR_MIPMAP_LINEAR

```TypeScript
readonly LINEAR_MIPMAP_LINEAR: GLenum
```

Mipmap filter: linear mipmap linear

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINEAR_MIPMAP_NEAREST

```TypeScript
readonly LINEAR_MIPMAP_NEAREST: GLenum
```

Mipmap filter: linear mipmap nearest

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINES

```TypeScript
readonly LINES: GLenum
```

Primitive type: lines

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LINK_STATUS

```TypeScript
readonly LINK_STATUS: GLenum
```

Link Status

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LOW_FLOAT

```TypeScript
readonly LOW_FLOAT: GLenum
```

Precision: low float

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LOW_INT

```TypeScript
readonly LOW_INT: GLenum
```

Precision: low int

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LUMINANCE

```TypeScript
readonly LUMINANCE: GLenum
```

Pixel format: luminance

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## LUMINANCE_ALPHA

```TypeScript
readonly LUMINANCE_ALPHA: GLenum
```

Pixel format: luminance alpha

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_COMBINED_TEXTURE_IMAGE_UNITS

```TypeScript
readonly MAX_COMBINED_TEXTURE_IMAGE_UNITS: GLenum
```

Max combined texture image units

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_CUBE_MAP_TEXTURE_SIZE

```TypeScript
readonly MAX_CUBE_MAP_TEXTURE_SIZE: GLenum
```

Max cube map texture size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_FRAGMENT_UNIFORM_VECTORS

```TypeScript
readonly MAX_FRAGMENT_UNIFORM_VECTORS: GLenum
```

Max Fragment Uniform Vectors

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_RENDERBUFFER_SIZE

```TypeScript
readonly MAX_RENDERBUFFER_SIZE: GLenum
```

Max renderbuffer size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_TEXTURE_IMAGE_UNITS

```TypeScript
readonly MAX_TEXTURE_IMAGE_UNITS: GLenum
```

Max Texture Image Units

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_TEXTURE_SIZE

```TypeScript
readonly MAX_TEXTURE_SIZE: GLenum
```

Max texture size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_VARYING_VECTORS

```TypeScript
readonly MAX_VARYING_VECTORS: GLenum
```

Max varying vectors

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_VERTEX_ATTRIBS

```TypeScript
readonly MAX_VERTEX_ATTRIBS: GLenum
```

Max vertex attribs

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_VERTEX_TEXTURE_IMAGE_UNITS

```TypeScript
readonly MAX_VERTEX_TEXTURE_IMAGE_UNITS: GLenum
```

Max Vertex Texture Image Units

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_VERTEX_UNIFORM_VECTORS

```TypeScript
readonly MAX_VERTEX_UNIFORM_VECTORS: GLenum
```

Max vertex uniform vectors

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MAX_VIEWPORT_DIMS

```TypeScript
readonly MAX_VIEWPORT_DIMS: GLenum
```

Max viewport dims

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MEDIUM_FLOAT

```TypeScript
readonly MEDIUM_FLOAT: GLenum
```

Precision: medium float

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MEDIUM_INT

```TypeScript
readonly MEDIUM_INT: GLenum
```

Precision: medium int

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## MIRRORED_REPEAT

```TypeScript
readonly MIRRORED_REPEAT: GLenum
```

Texture wrap: mirrored repeat

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NEAREST

```TypeScript
readonly NEAREST: GLenum
```

Filter: nearest

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NEAREST_MIPMAP_LINEAR

```TypeScript
readonly NEAREST_MIPMAP_LINEAR: GLenum
```

Mipmap filter: nearest mipmap linear

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NEAREST_MIPMAP_NEAREST

```TypeScript
readonly NEAREST_MIPMAP_NEAREST: GLenum
```

Mipmap filter: nearest mipmap nearest

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NEVER

```TypeScript
readonly NEVER: GLenum
```

Never

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NICEST

```TypeScript
readonly NICEST: GLenum
```

Hint: nicest

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NO_ERROR

```TypeScript
readonly NO_ERROR: GLenum
```

Error code: no error

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NONE

```TypeScript
readonly NONE: GLenum
```

None

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## NOTEQUAL

```TypeScript
readonly NOTEQUAL: GLenum
```

Comparison function: not equal

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE

```TypeScript
readonly ONE: GLenum
```

One value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE_MINUS_CONSTANT_ALPHA

```TypeScript
readonly ONE_MINUS_CONSTANT_ALPHA: GLenum
```

One minus constant alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE_MINUS_CONSTANT_COLOR

```TypeScript
readonly ONE_MINUS_CONSTANT_COLOR: GLenum
```

One minus constant color blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE_MINUS_DST_ALPHA

```TypeScript
readonly ONE_MINUS_DST_ALPHA: GLenum
```

One minus destination alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE_MINUS_DST_COLOR

```TypeScript
readonly ONE_MINUS_DST_COLOR: GLenum
```

One minus destination color blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE_MINUS_SRC_ALPHA

```TypeScript
readonly ONE_MINUS_SRC_ALPHA: GLenum
```

One minus source alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ONE_MINUS_SRC_COLOR

```TypeScript
readonly ONE_MINUS_SRC_COLOR: GLenum
```

One minus source color blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## OUT_OF_MEMORY

```TypeScript
readonly OUT_OF_MEMORY: GLenum
```

Error code: out of memory

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## PACK_ALIGNMENT

```TypeScript
readonly PACK_ALIGNMENT: GLenum
```

Pack alignment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## POINTS

```TypeScript
readonly POINTS: GLenum
```

Primitive type: points

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## POLYGON_OFFSET_FACTOR

```TypeScript
readonly POLYGON_OFFSET_FACTOR: GLenum
```

Polygon offset factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## POLYGON_OFFSET_FILL

```TypeScript
readonly POLYGON_OFFSET_FILL: GLenum
```

Enable cap: polygon offset fill

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## POLYGON_OFFSET_UNITS

```TypeScript
readonly POLYGON_OFFSET_UNITS: GLenum
```

Polygon offset units

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RED_BITS

```TypeScript
readonly RED_BITS: GLenum
```

Red bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER

```TypeScript
readonly RENDERBUFFER: GLenum
```

Renderbuffer target

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_ALPHA_SIZE

```TypeScript
readonly RENDERBUFFER_ALPHA_SIZE: GLenum
```

Renderbuffer parameter: alpha size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_BINDING

```TypeScript
readonly RENDERBUFFER_BINDING: GLenum
```

Renderbuffer binding

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_BLUE_SIZE

```TypeScript
readonly RENDERBUFFER_BLUE_SIZE: GLenum
```

Renderbuffer parameter: blue size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_DEPTH_SIZE

```TypeScript
readonly RENDERBUFFER_DEPTH_SIZE: GLenum
```

Renderbuffer parameter: depth size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_GREEN_SIZE

```TypeScript
readonly RENDERBUFFER_GREEN_SIZE: GLenum
```

Renderbuffer parameter: green size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_HEIGHT

```TypeScript
readonly RENDERBUFFER_HEIGHT: GLenum
```

Renderbuffer parameter: height

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_INTERNAL_FORMAT

```TypeScript
readonly RENDERBUFFER_INTERNAL_FORMAT: GLenum
```

Renderbuffer parameter: internal format

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_RED_SIZE

```TypeScript
readonly RENDERBUFFER_RED_SIZE: GLenum
```

Renderbuffer parameter: red size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_STENCIL_SIZE

```TypeScript
readonly RENDERBUFFER_STENCIL_SIZE: GLenum
```

Renderbuffer parameter: stencil size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERBUFFER_WIDTH

```TypeScript
readonly RENDERBUFFER_WIDTH: GLenum
```

Renderbuffer parameter: width

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RENDERER

```TypeScript
readonly RENDERER: GLenum
```

Renderer name

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## REPEAT

```TypeScript
readonly REPEAT: GLenum
```

Texture wrap: repeat

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## REPLACE

```TypeScript
readonly REPLACE: GLenum
```

Stencil operation: replace

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RGB

```TypeScript
readonly RGB: GLenum
```

Pixel format: RGB

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RGB565

```TypeScript
readonly RGB565: GLenum
```

Renderbuffer internal format: RGB565

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RGB5_A1

```TypeScript
readonly RGB5_A1: GLenum
```

Renderbuffer internal format: RGB5_A1

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RGBA

```TypeScript
readonly RGBA: GLenum
```

Pixel format: RGBA

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## RGBA4

```TypeScript
readonly RGBA4: GLenum
```

Renderbuffer internal format: RGBA4

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLE_ALPHA_TO_COVERAGE

```TypeScript
readonly SAMPLE_ALPHA_TO_COVERAGE: GLenum
```

Enable cap: sample alpha to coverage

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLE_BUFFERS

```TypeScript
readonly SAMPLE_BUFFERS: GLenum
```

Sample buffers

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLE_COVERAGE

```TypeScript
readonly SAMPLE_COVERAGE: GLenum
```

Enable cap: sample coverage

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLE_COVERAGE_INVERT

```TypeScript
readonly SAMPLE_COVERAGE_INVERT: GLenum
```

Sample coverage invert

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLE_COVERAGE_VALUE

```TypeScript
readonly SAMPLE_COVERAGE_VALUE: GLenum
```

Sample coverage value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLER_2D

```TypeScript
readonly SAMPLER_2D: GLenum
```

Sampler type: 2D

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLER_CUBE

```TypeScript
readonly SAMPLER_CUBE: GLenum
```

Sampler type: cube

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SAMPLES

```TypeScript
readonly SAMPLES: GLenum
```

Samples

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SCISSOR_BOX

```TypeScript
readonly SCISSOR_BOX: GLenum
```

Scissor box

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SCISSOR_TEST

```TypeScript
readonly SCISSOR_TEST: GLenum
```

Enable cap: scissor test

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Test API:** This API is used only in automated test scripts.

## SHADER_TYPE

```TypeScript
readonly SHADER_TYPE: GLenum
```

Shader Type

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SHADING_LANGUAGE_VERSION

```TypeScript
readonly SHADING_LANGUAGE_VERSION: GLenum
```

Shading Language Version

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SHORT

```TypeScript
readonly SHORT: GLenum
```

Data type: short

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SRC_ALPHA

```TypeScript
readonly SRC_ALPHA: GLenum
```

Source alpha blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SRC_ALPHA_SATURATE

```TypeScript
readonly SRC_ALPHA_SATURATE: GLenum
```

Source alpha saturate blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SRC_COLOR

```TypeScript
readonly SRC_COLOR: GLenum
```

Source color blend factor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STATIC_DRAW

```TypeScript
readonly STATIC_DRAW: GLenum
```

Buffer usage: static draw

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_ATTACHMENT

```TypeScript
readonly STENCIL_ATTACHMENT: GLenum
```

Stencil Attachment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_FAIL

```TypeScript
readonly STENCIL_BACK_FAIL: GLenum
```

Stencil back fail operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_FUNC

```TypeScript
readonly STENCIL_BACK_FUNC: GLenum
```

Stencil back function

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_PASS_DEPTH_FAIL

```TypeScript
readonly STENCIL_BACK_PASS_DEPTH_FAIL: GLenum
```

Stencil back pass depth fail operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_PASS_DEPTH_PASS

```TypeScript
readonly STENCIL_BACK_PASS_DEPTH_PASS: GLenum
```

Stencil back pass depth pass operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_REF

```TypeScript
readonly STENCIL_BACK_REF: GLenum
```

Stencil back reference value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_VALUE_MASK

```TypeScript
readonly STENCIL_BACK_VALUE_MASK: GLenum
```

Stencil back value mask

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BACK_WRITEMASK

```TypeScript
readonly STENCIL_BACK_WRITEMASK: GLenum
```

Stencil back write mask

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BITS

```TypeScript
readonly STENCIL_BITS: GLenum
```

Stencil bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_BUFFER_BIT

```TypeScript
readonly STENCIL_BUFFER_BIT: GLenum
```

Stencil buffer clear value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_CLEAR_VALUE

```TypeScript
readonly STENCIL_CLEAR_VALUE: GLenum
```

Stencil clear value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_FAIL

```TypeScript
readonly STENCIL_FAIL: GLenum
```

Stencil fail operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_FUNC

```TypeScript
readonly STENCIL_FUNC: GLenum
```

Stencil function

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_INDEX8

```TypeScript
readonly STENCIL_INDEX8: GLenum
```

Renderbuffer internal format: stencil index8

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_PASS_DEPTH_FAIL

```TypeScript
readonly STENCIL_PASS_DEPTH_FAIL: GLenum
```

Stencil pass depth fail operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_PASS_DEPTH_PASS

```TypeScript
readonly STENCIL_PASS_DEPTH_PASS: GLenum
```

Stencil pass depth pass operation

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_REF

```TypeScript
readonly STENCIL_REF: GLenum
```

Stencil reference value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_TEST

```TypeScript
readonly STENCIL_TEST: GLenum
```

Enable cap: stencil test

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

**Test API:** This API is used only in automated test scripts.

## STENCIL_VALUE_MASK

```TypeScript
readonly STENCIL_VALUE_MASK: GLenum
```

Stencil value mask

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STENCIL_WRITEMASK

```TypeScript
readonly STENCIL_WRITEMASK: GLenum
```

Stencil write mask

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## STREAM_DRAW

```TypeScript
readonly STREAM_DRAW: GLenum
```

Buffer usage: stream draw

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## SUBPIXEL_BITS

```TypeScript
readonly SUBPIXEL_BITS: GLenum
```

Subpixel bits

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE

```TypeScript
readonly TEXTURE: GLenum
```

Texture target: texture

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE0

```TypeScript
readonly TEXTURE0: GLenum
```

Texture unit 0

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE1

```TypeScript
readonly TEXTURE1: GLenum
```

Texture unit 1

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE10

```TypeScript
readonly TEXTURE10: GLenum
```

Texture unit 10

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE11

```TypeScript
readonly TEXTURE11: GLenum
```

Texture unit 11

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE12

```TypeScript
readonly TEXTURE12: GLenum
```

Texture unit 12

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE13

```TypeScript
readonly TEXTURE13: GLenum
```

Texture unit 13

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE14

```TypeScript
readonly TEXTURE14: GLenum
```

Texture unit 14

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE15

```TypeScript
readonly TEXTURE15: GLenum
```

Texture unit 15

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE16

```TypeScript
readonly TEXTURE16: GLenum
```

Texture unit 16

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE17

```TypeScript
readonly TEXTURE17: GLenum
```

Texture unit 17

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE18

```TypeScript
readonly TEXTURE18: GLenum
```

Texture unit 18

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE19

```TypeScript
readonly TEXTURE19: GLenum
```

Texture unit 19

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE2

```TypeScript
readonly TEXTURE2: GLenum
```

Texture unit 2

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE20

```TypeScript
readonly TEXTURE20: GLenum
```

Texture unit 20

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE21

```TypeScript
readonly TEXTURE21: GLenum
```

Texture unit 21

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE22

```TypeScript
readonly TEXTURE22: GLenum
```

Texture unit 22

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE23

```TypeScript
readonly TEXTURE23: GLenum
```

Texture unit 23

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE24

```TypeScript
readonly TEXTURE24: GLenum
```

Texture unit 24

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE25

```TypeScript
readonly TEXTURE25: GLenum
```

Texture unit 25

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE26

```TypeScript
readonly TEXTURE26: GLenum
```

Texture unit 26

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE27

```TypeScript
readonly TEXTURE27: GLenum
```

Texture unit 27

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE28

```TypeScript
readonly TEXTURE28: GLenum
```

Texture unit 28

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE29

```TypeScript
readonly TEXTURE29: GLenum
```

Texture unit 29

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE3

```TypeScript
readonly TEXTURE3: GLenum
```

Texture unit 3

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE30

```TypeScript
readonly TEXTURE30: GLenum
```

Texture unit 30

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE31

```TypeScript
readonly TEXTURE31: GLenum
```

Texture unit 31

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE4

```TypeScript
readonly TEXTURE4: GLenum
```

Texture unit 4

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE5

```TypeScript
readonly TEXTURE5: GLenum
```

Texture unit 5

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE6

```TypeScript
readonly TEXTURE6: GLenum
```

Texture unit 6

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE7

```TypeScript
readonly TEXTURE7: GLenum
```

Texture unit 7

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE8

```TypeScript
readonly TEXTURE8: GLenum
```

Texture unit 8

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE9

```TypeScript
readonly TEXTURE9: GLenum
```

Texture unit 9

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_2D

```TypeScript
readonly TEXTURE_2D: GLenum
```

Texture target: 2D

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_BINDING_2D

```TypeScript
readonly TEXTURE_BINDING_2D: GLenum
```

Texture binding 2D

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_BINDING_CUBE_MAP

```TypeScript
readonly TEXTURE_BINDING_CUBE_MAP: GLenum
```

Texture binding cube map

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP

```TypeScript
readonly TEXTURE_CUBE_MAP: GLenum
```

Texture target: cube map

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP_NEGATIVE_X

```TypeScript
readonly TEXTURE_CUBE_MAP_NEGATIVE_X: GLenum
```

Texture cube map negative X

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP_NEGATIVE_Y

```TypeScript
readonly TEXTURE_CUBE_MAP_NEGATIVE_Y: GLenum
```

Texture cube map negative Y

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP_NEGATIVE_Z

```TypeScript
readonly TEXTURE_CUBE_MAP_NEGATIVE_Z: GLenum
```

Texture cube map negative Z

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP_POSITIVE_X

```TypeScript
readonly TEXTURE_CUBE_MAP_POSITIVE_X: GLenum
```

Texture cube map positive X

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP_POSITIVE_Y

```TypeScript
readonly TEXTURE_CUBE_MAP_POSITIVE_Y: GLenum
```

Texture cube map positive Y

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_CUBE_MAP_POSITIVE_Z

```TypeScript
readonly TEXTURE_CUBE_MAP_POSITIVE_Z: GLenum
```

Texture cube map positive Z

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_MAG_FILTER

```TypeScript
readonly TEXTURE_MAG_FILTER: GLenum
```

Texture parameter: mag filter

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_MIN_FILTER

```TypeScript
readonly TEXTURE_MIN_FILTER: GLenum
```

Texture parameter: min filter

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_WRAP_S

```TypeScript
readonly TEXTURE_WRAP_S: GLenum
```

Texture parameter: wrap s

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TEXTURE_WRAP_T

```TypeScript
readonly TEXTURE_WRAP_T: GLenum
```

Texture parameter: wrap t

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TRIANGLE_FAN

```TypeScript
readonly TRIANGLE_FAN: GLenum
```

Primitive type: triangle fan

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TRIANGLE_STRIP

```TypeScript
readonly TRIANGLE_STRIP: GLenum
```

Primitive type: triangle strip

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## TRIANGLES

```TypeScript
readonly TRIANGLES: GLenum
```

Primitive type: triangles

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNPACK_ALIGNMENT

```TypeScript
readonly UNPACK_ALIGNMENT: GLenum
```

Unpack alignment

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNPACK_COLORSPACE_CONVERSION_WEBGL

```TypeScript
readonly UNPACK_COLORSPACE_CONVERSION_WEBGL: GLenum
```

Unpack option: colorspace conversion WebGL

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNPACK_FLIP_Y_WEBGL

```TypeScript
readonly UNPACK_FLIP_Y_WEBGL: GLenum
```

Unpack option: flip Y WebGL

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNPACK_PREMULTIPLY_ALPHA_WEBGL

```TypeScript
readonly UNPACK_PREMULTIPLY_ALPHA_WEBGL: GLenum
```

Unpack option: premultiply alpha WebGL

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNSIGNED_BYTE

```TypeScript
readonly UNSIGNED_BYTE: GLenum
```

Data type: unsigned byte

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNSIGNED_INT

```TypeScript
readonly UNSIGNED_INT: GLenum
```

Data type: unsigned int

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNSIGNED_SHORT

```TypeScript
readonly UNSIGNED_SHORT: GLenum
```

Data type: unsigned short

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNSIGNED_SHORT_4_4_4_4

```TypeScript
readonly UNSIGNED_SHORT_4_4_4_4: GLenum
```

Unsigned short 5_5_5_1

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNSIGNED_SHORT_5_5_5_1

```TypeScript
readonly UNSIGNED_SHORT_5_5_5_1: GLenum
```

Unsigned short 5_5_5_1

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## UNSIGNED_SHORT_5_6_5

```TypeScript
readonly UNSIGNED_SHORT_5_6_5: GLenum
```

Unsigned short 5_6_5

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VALIDATE_STATUS

```TypeScript
readonly VALIDATE_STATUS: GLenum
```

Validate Status

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VENDOR

```TypeScript
readonly VENDOR: GLenum
```

Renderer vendor

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERSION

```TypeScript
readonly VERSION: GLenum
```

WebGL version

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_BUFFER_BINDING

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_BUFFER_BINDING: GLenum
```

Vertex attrib array: buffer binding

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_ENABLED

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_ENABLED: GLenum
```

Vertex attrib array: enabled

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_NORMALIZED

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_NORMALIZED: GLenum
```

Vertex attrib array: normalized

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_POINTER

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_POINTER: GLenum
```

Vertex attrib array: pointer

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_SIZE

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_SIZE: GLenum
```

Vertex attrib array: size

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_STRIDE

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_STRIDE: GLenum
```

Vertex attrib array: stride

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_ATTRIB_ARRAY_TYPE

```TypeScript
readonly VERTEX_ATTRIB_ARRAY_TYPE: GLenum
```

Vertex attrib array: type

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VERTEX_SHADER

```TypeScript
readonly VERTEX_SHADER: GLenum
```

Shader type: vertex shader

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## VIEWPORT

```TypeScript
readonly VIEWPORT: GLenum
```

Viewport

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL

## ZERO

```TypeScript
readonly ZERO: GLenum
```

Zero value

**Type:** [GLenum](arkts-arkgraphics2d-glenum-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Graphic.Graphic2D.WebGL
