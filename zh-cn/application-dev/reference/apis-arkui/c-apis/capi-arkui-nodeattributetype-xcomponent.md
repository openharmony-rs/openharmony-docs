# 自定义渲染组件

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_XCOMPONENT_ID

```c
NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT
```

**描述：**

XComponent组件的ID，支持属性设置和属性获取接口。 作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string: XComponent组件的ID内容，用于唯一标识该组件。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string: XComponent组件的ID内容，用于唯一标识该组件。</li> </ul>

**起始版本：** 12

### NODE_XCOMPONENT_TYPE

```c
NODE_XCOMPONENT_TYPE
```

**描述：**

XComponent组件的类型，仅支持属性获取接口。 XComponent组件的类型需要在组件创建时通过ArkUI_NodeType中的ARKUI_NODE_XCOMPONENT或者ARKUI_NODE_XCOMPONENT_TEXTURE明确，不允许后续修改。 使用setAttribute接口尝试修改XComponent组件的类型时会发生绘制内容异常。 作为属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32: XComponent组件的类型，取值类型为ArkUI_XComponentType，具体枚举值及其与数字的对应关系请参见该枚举定义。</li> </ul>

**起始版本：** 12

### NODE_XCOMPONENT_SURFACE_SIZE

```c
NODE_XCOMPONENT_SURFACE_SIZE
```

**描述：**

XComponent组件所持有的Surface的宽高，仅支持属性获取接口。 使用setAttribute接口尝试修改Surface的宽高时，该设置不会生效。 作为属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].u32: 宽度数值，单位为px。</li><br><li>.value[1].u32: 高度数值，单位为px。</li> </ul>

**起始版本：** 12

### NODE_XCOMPONENT_SURFACE_RECT

```c
NODE_XCOMPONENT_SURFACE_RECT
```

**描述：**

XComponent组件所持有的Surface显示区域，支持属性设置和属性获取接口。 适用于需要在XComponent组件内指定局部区域进行渲染的场景，例如视频画面裁剪显示、画中画局部渲染等。 作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32: Surface显示区域相对于XComponent组件左上角的x轴坐标，单位为px。</li><br><li>.value[1].i32: Surface显示区域相对于XComponent组件左上角的y轴坐标，单位为px。</li><br><li>.value[2].i32: Surface显示区域的宽度，单位为px，取值必须为正整数。传入0或负数时设置不生效。</li><br><li>.value[3].i32: Surface显示区域的高度，单位为px，取值必须为正整数。传入0或负数时设置不生效。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32: Surface显示区域相对于XComponent组件左上角的x轴坐标，单位为px。</li><br><li>.value[1].i32: Surface显示区域相对于XComponent组件左上角的y轴坐标，单位为px。</li><br><li>.value[2].i32: Surface显示区域的宽度，单位为px，取值应为正整数。</li><br><li>.value[3].i32: Surface显示区域的高度，单位为px，取值应为正整数。</li> </ul>

**起始版本：** 18

### NODE_XCOMPONENT_ENABLE_ANALYZER

```c
NODE_XCOMPONENT_ENABLE_ANALYZER
```

**描述：**

XComponent组件是否支持图像分析的属性，支持属性设置和属性获取接口。 开启后可对组件中显示的图像进行内容识别分析，适用于相机预览实时识别、图像内容理解等场景。 作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32: 是否支持图像分析，1表示支持图像分析，0表示不支持图像分析，默认值：0。传入非0和非1的值时按0处理。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32: 是否支持图像分析，1表示支持图像分析，0表示不支持图像分析。</li> </ul>

**起始版本：** 18


