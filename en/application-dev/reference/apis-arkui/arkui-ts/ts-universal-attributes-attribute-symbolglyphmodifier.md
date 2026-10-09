# Symbol Glyph Modifier

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=92567145241181b97abe57e944e177355e50f4eb translatedAt=2026-09-01T12:06:57.873Z -->

SymbolGlyphModifier is used to dynamically set the attributes and styles of the SymbolGlyph component. It supports using if/else statements to dynamically adjust the component style based on conditions, and is suitable for scenarios where the icon appearance needs to change dynamically according to the application state or user interaction. [SymbolGlyph](./ts-basic-components-symbolGlyph.md) is a component used to display icon symbols.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## SymbolGlyphModifier

Defines the **SymbolGlyphModifier**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(src?: Resource)

A constructor used to create a **SymbolGlyphModifier** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                             | Mandatory| Description  |
| ------- | --------------------------------- | ---- | --------------------------------- |
| src | [Resource](./ts-types.md#resource) | No  | Sets the symbol icon resource to be displayed by the SymbolGlyph component. If not passed, no resource is loaded. |

### applyNormalAttribute

applyNormalAttribute?(instance: SymbolGlyphAttribute): void

Sets the style of the component in the normal state (that is, the default interaction state in which the component is not pressed, does not have focus, and so on). This method is a callback method that is automatically invoked by the framework when the component is in the normal state. Developers can dynamically set the style of the SymbolGlyph component by modifying the properties of the instance object in the method body.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                             | Mandatory| Description  |
| ------- | --------------------------------- | ---- | --------------------------------- |
| instance | [SymbolGlyphAttribute](./ts-basic-components-symbolGlyph.md) | Yes | Instance of SymbolGlyphAttribute, used to dynamically set the properties and styles of the SymbolGlyph component. |

## Example

This example demonstrates the effect of customizing the style of the clear button with a symbol type on the right through [SymbolGlyphModifier](#symbolglyphmodifier) and the [cancelButton](./ts-basic-components-textinput.md#cancelbutton18) attribute of the TextInput component.

```ts
import { SymbolGlyphModifier } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  @State text: string = '';
  symbolGlyphModifier: SymbolGlyphModifier =
    new SymbolGlyphModifier($r('sys.symbol.trash')).fontColor([Color.Red]).fontSize(16).fontWeight(FontWeight.Regular);

  build() {
    Column() {
      TextInput({ text: this.text, placeholder: 'input your word...' })
        .height(50)
        .cancelButton({
          style: CancelButtonStyle.CONSTANT,
          icon: this.symbolGlyphModifier // SymbolGlyph type is supported since API version 18.
        })
    }.margin(10)
  }
}
```

![SymbolGlyphModifier](figures/symbolGlyphModifier.PNG)