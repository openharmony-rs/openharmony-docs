# 信息展示

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_LOADING_PROGRESS_COLOR

```c
NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS
```

**描述：**

加载进度条前景色属性，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].u32：前景颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。默认值：跟随主题。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].u32：前景颜色数值，0xargb格式。</li> </ul>

**起始版本：** 12

### NODE_LOADING_PROGRESS_ENABLE_LOADING

```c
NODE_LOADING_PROGRESS_ENABLE_LOADING
```

**描述：**

LoadingProgress动画显示属性，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：1时不显示动画，1时显示动画。默认值为1。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：1时不显示动画，1时显示动画。</li> </ul>

**起始版本：** 12

### NODE_PROGRESS_VALUE

```c
NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS
```

**描述：**

进度条的当前进度值属性，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].f32：进度条当前值，取值范围为[0, total]，默认值为0。超出范围时自动修正至有效范围边界值。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].f32：进度条当前值，取值范围为[0, total]，默认值为0。</li> </ul>

**起始版本：** 12

### NODE_PROGRESS_TOTAL

```c
NODE_PROGRESS_TOTAL
```

**描述：**

进度条的总长属性，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].f32：进度条总长，取值范围为(0, +∞)，默认值为100，需大于0。传入小于等于0的值时不生效。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].f32：进度条总长，取值范围为(0, +∞)，默认值为100。</li> </ul>

**起始版本：** 12

### NODE_PROGRESS_COLOR

```c
NODE_PROGRESS_COLOR
```

**描述：**

进度条显示进度值的颜色属性，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].u32：颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。默认值：跟随主题。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].u32：颜色数值，0xargb格式。</li> </ul>

**起始版本：** 12

### NODE_PROGRESS_TYPE

```c
NODE_PROGRESS_TYPE
```

**描述：**

进度条的类型属性，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：进度条类型，具体枚举值及含义参见{@link ArkUI_ProgressType}。默认值为ARKUI_PROGRESS_TYPE_LINEAR。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：进度条类型。</li> </ul>

**起始版本：** 12

### NODE_PROGRESS_LINEAR_STYLE

```c
NODE_PROGRESS_LINEAR_STYLE
```

**描述：**

线性进度条样式设置，支持属性设置、属性重置和属性获取接口，如果进度条类型不是线性样式则不生效，需先通过NODE_PROGRESS_TYPE将进度条类型设置为ARKUI_PROGRESS_TYPE_LINEAR。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.object：使用{@link ArkUI_ProgressLinearStyleOption}对象设置组件样式。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.object：返回{@link ArkUI_ProgressLinearStyleOption}对象，包含线性进度条的样式信息。</li> </ul>

**起始版本：** 15


