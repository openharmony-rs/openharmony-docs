# EditorAttribute

编辑框属性值。

**起始版本：** 8

<!--Device-inputMethodEngine-interface EditorAttribute--><!--Device-inputMethodEngine-interface EditorAttribute-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## abilityName

```TypeScript
readonly abilityName?: string
```

编辑框设置的ability名称。

**类型：** string

**起始版本：** 20

<!--Device-EditorAttribute-readonly abilityName?: string--><!--Device-EditorAttribute-readonly abilityName?: string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## bundleName

```TypeScript
readonly bundleName?: string
```

编辑框所属应用包名；该值可能为""，使用该属性时需要考虑为""的场景。

**类型：** string

**起始版本：** 14

<!--Device-EditorAttribute-readonly bundleName?: string--><!--Device-EditorAttribute-readonly bundleName?: string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## capitalizeMode

```TypeScript
readonly capitalizeMode?: CapitalizeMode
```

编辑框设置大小写模式。如果没有设置或设置非法值，默认不进行任何首字母大写处理。

**类型：** CapitalizeMode

**起始版本：** 20

<!--Device-EditorAttribute-readonly capitalizeMode?: CapitalizeMode--><!--Device-EditorAttribute-readonly capitalizeMode?: CapitalizeMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## consumeKeyEvents

```TypeScript
readonly consumeKeyEvents?: boolean
```

编辑框是否具有完整处理字母、字符、功能等按键的能力。

- 值为true，表示具备此能力。  
- 值为false，表示不具备此能力。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditorAttribute-readonly consumeKeyEvents?: boolean--><!--Device-EditorAttribute-readonly consumeKeyEvents?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## displayId

```TypeScript
readonly displayId?: number
```

编辑框设置窗口对应的屏幕ID。如果没有设置windowId，取当前焦点窗口屏幕ID。

**类型：** number

**起始版本：** 18

<!--Device-EditorAttribute-readonly displayId?: long--><!--Device-EditorAttribute-readonly displayId?: long-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## enterKeyType

```TypeScript
readonly enterKeyType: number
```

编辑框的功能属性

**类型：** number

**起始版本：** 8

<!--Device-EditorAttribute-readonly enterKeyType: int--><!--Device-EditorAttribute-readonly enterKeyType: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## extraConfig

```TypeScript
readonly extraConfig?: InputMethodExtraConfig
```

输入法扩展信息。

**类型：** InputMethodExtraConfig

**起始版本：** 22

<!--Device-EditorAttribute-readonly extraConfig?: InputMethodExtraConfig--><!--Device-EditorAttribute-readonly extraConfig?: InputMethodExtraConfig-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## gradientMode

```TypeScript
readonly gradientMode?: GradientMode
```

渐变模式。如果没有设置或设置非法值，默认不使用渐变模式。

**类型：** GradientMode

**起始版本：** 20

<!--Device-EditorAttribute-readonly gradientMode?: GradientMode--><!--Device-EditorAttribute-readonly gradientMode?: GradientMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## immersiveMode

```TypeScript
readonly immersiveMode?: ImmersiveMode
```

输入法沉浸模式。

**类型：** ImmersiveMode

**起始版本：** 15

<!--Device-EditorAttribute-readonly immersiveMode?: ImmersiveMode--><!--Device-EditorAttribute-readonly immersiveMode?: ImmersiveMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## inputPattern

```TypeScript
readonly inputPattern: number
```

编辑框的文本属性

**类型：** number

**起始版本：** 8

<!--Device-EditorAttribute-readonly inputPattern: int--><!--Device-EditorAttribute-readonly inputPattern: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## isTextPreviewSupported

```TypeScript
isTextPreviewSupported: boolean
```

编辑框是否支持预上屏。

- 值为true，表示支持。  
- 值为false，表示不支持。

**类型：** boolean

**起始版本：** 12

<!--Device-EditorAttribute-isTextPreviewSupported: boolean--><!--Device-EditorAttribute-isTextPreviewSupported: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## placeholder

```TypeScript
readonly placeholder?: string
```

编辑框设置的占位符信息。

**类型：** string

**起始版本：** 20

<!--Device-EditorAttribute-readonly placeholder?: string--><!--Device-EditorAttribute-readonly placeholder?: string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## windowId

```TypeScript
readonly windowId?: number
```

编辑框设置所属窗口ID。

**类型：** number

**起始版本：** 18

<!--Device-EditorAttribute-readonly windowId?: int--><!--Device-EditorAttribute-readonly windowId?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

