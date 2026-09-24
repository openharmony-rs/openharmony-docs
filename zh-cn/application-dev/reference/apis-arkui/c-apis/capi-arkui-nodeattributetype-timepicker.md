# 时间选择器

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### 

```c

```

**描述：**

设置时间选择器组件的选中项时间，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：时间。默认值：当前系统时间。设置格式：时:分或时-分（例：23:59或23-59）。返回格式：时,分,秒（例：23,59,0）。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：选中的时间。格式：时,分,秒，使用`,`分隔（例：23,59,0）。</li> </ul>

**起始版本：** 12

### NODE_TIME_PICKER_USE_MILITARY_TIME

```c
NODE_TIME_PICKER_USE_MILITARY_TIME
```

**描述：**

设置时间选择组件展示时间是否为24小时制，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否为24小时制，默认值：0。0表示展示时间为12小时制，1表示展示时间为24小时制。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否为24小时制。返回0表示展示时间为12小时制（对应false），返回1表示展示时间为24小时制（对应true）。</li> </ul>

**起始版本：** 12

### NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TIME_PICKER_DISAPPEAR_TEXT_STYLE
```

**描述：**

设置边缘项（以选中项为基准向上或向下的第二项）的文本样式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1： 文本颜色，#argb类型。 参数2： 文本大小，数字类型，单位fp。 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4： 文本字体列表，使用 ',' 进行分割。 参数5： 文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。 </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul>

**起始版本：** 12

### NODE_TIME_PICKER_TEXT_STYLE

```c
NODE_TIME_PICKER_TEXT_STYLE
```

**描述：**

设置时间选择组件所有选项中除了边缘项及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1： 文本颜色，#argb类型。 参数2： 文本大小，数字类型，单位fp。 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4： 文本字体列表，使用 ',' 进行分割。 参数5： 文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。 </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul>

**起始版本：** 12

### NODE_TIME_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TIME_PICKER_SELECTED_TEXT_STYLE
```

**描述：**

设置时间选择组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1： 文本颜色，#argb类型。 参数2： 文本大小，数字类型，单位fp。 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4： 文本字体列表，使用 ',' 进行分割。 参数5： 文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。 </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul>

**起始版本：** 12

### NODE_TIME_PICKER_START

```c
NODE_TIME_PICKER_START = 14005
```

**描述：**

设置时间选择器组件的起始时间，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：时间。默认值："0:0"。设置时仅支持时:分，使用`:`或`-`分隔（例：12:59或12-59）。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：设置的起始时间。格式：时:分:秒（例：0:0:0）。</li> </ul>

**起始版本：** 18

### NODE_TIME_PICKER_END

```c
NODE_TIME_PICKER_END = 14006
```

**描述：**

设置时间选择器组件的结束时间，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：时间。默认值："23:59"。设置时仅支持时:分，使用`:`或`-`分隔（例：23:59或23-59）。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：设置的结束时间。格式：时:分:秒（例：23:59:0）。</li> </ul>

**起始版本：** 18

### NODE_TIME_PICKER_ENABLE_CASCADE

```c
NODE_TIME_PICKER_ENABLE_CASCADE = 14007
```

**描述：**

在设置12小时制时，上午和下午的标识会根据小时数自动切换，支持属性设置、重置和获取；在24小时制时，该参数不生效。 使用场景：适用于需要提供友好的12小时制选择体验的场景，例如用户滚动选择小时时，上午/下午标识自动跟随变化，无需用户手动切换。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：在12小时制时，设置上午和下午的标识是否会根据小时数自动切换，默认值：0。0表示不自动切换，1表示自动切换。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：在12小时制时，上午和下午的标识是否会根据小时数自动切换。返回0表示不自动切换（对应false），返回1表示自动切换（对应true）。</li> </ul>

**起始版本：** 18


