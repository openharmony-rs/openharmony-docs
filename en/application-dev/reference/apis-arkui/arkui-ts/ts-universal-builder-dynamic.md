# @Builder Decorator: Custom Builder Function

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-10-30T09:02:04.889Z pushedAt=2026-10-30T09:32:33.720Z nl=1 -->

Functions decorated with **\@Builder** are also known as custom builder functions. They are used to encapsulate reusable UI building logic and can be called multiple times within a custom component, thereby reducing code duplication and improving the maintainability of UI building. It is suitable for scenarios where the same UI structure needs to be reused.

For details about the development guide, see [@Builder Decorator: Custom Builder Function](../../../ui/state-management/arkts-builder.md).

> **NOTE**
>
> - This decorator is supported since API version 7. For newly added APIs in later versions, the since version of each API is marked separately with a superscript.
>
> - Since API version 26.1.0, the [BuilderDecoratorConfig](#builderdecoratorconfig) configuration item can be passed in to declare a placeholder builder function.

## @Builder

const Builder: MethodDecorator & BuilderMethodDecorator

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Example**

```ts
@Entry
@Component
struct BuilderDemo {
  // Decorate this function with @Builder to make it a custom builder function for configuring and building the Text component.
  @Builder
  showTextBuilder() {
    Text('Hello World')
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  @Builder
  showTextValueBuilder(param: string) {
    Text(param)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  build() {
    Column() {
      // No parameter.
      this.showTextBuilder()
      // With parameter.
      this.showTextValueBuilder('Hello @Builder')
    }
  }
}
```

## BuilderMethodDecorator

type BuilderMethodDecorator = (value: BuilderDecoratorConfig) => MethodDecorator

Actual type when configuration options are passed to the **\@Builder** decorator.

**Since:** 26.1.0

**Widget capability:** This API can be used in ArkTS widgets since API version 26.1.0.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type     | Mandatory | Description                                                         |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| value  | [BuilderDecoratorConfig](#builderdecoratorconfig) | Yes   | \@Builder Configuration options of the decorator.                                     |

**Return value**

| Type            | Description                                 |
| --------------- | ------------------------------------ |
| MethodDecorator | Method decorator. You do not need to pay attention to this return value. |

## BuilderDecoratorConfig

Configuration options of the **\@Builder** decorator.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.1.0.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type    | Read-Only | Optional | Description                                                         |
| ------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| isPlaceholder | boolean | No   | No   | Whether to declare the \@Builder function as a placeholder builder function. true: enables the placeholder capability. In this case, the function must be a global function with no parameters. It can only perform static rendering that does not depend on state variables, but cannot register gestures or business callbacks. After being registered through the register method of [placeholderRegister](../../../ui/state-management/arkts-builder.md#placeholder-builder-function), it is used by the [scrollPlaceholder](../../../ui/state-management/arkts-builder.md#placeholder-builder-function) attribute of scrollable components. false: does not enable the placeholder capability, which is equivalent to \@Builder without the configuration option. The default value is false. |

**Example**

The following example declares a placeholder builder function, which is registered through placeholderRegister and then used by the scrollPlaceholder attribute of List.

```ts
import { PlaceholderOptions } from '@kit.ArkUI';

// The placeholder builder function must be global and parameterless, and only performs static rendering that does not depend on state variables.
@Builder({ isPlaceholder: true })
function ItemPlaceholder() {
  Column() {
    Text('Loading...')
      .fontSize(16)
      .fontColor(0x999999)
  }
  .width('100%')
  .height(100)
  .justifyContent(FlexAlign.Center)
}

@Entry
@ComponentV2
struct BuilderPlaceholderList {
  @Local data: number[] = [];

  aboutToAppear(): void {
    // Obtain the placeholder registry through UIContext. The placeholder builder function is wrapped by wrapBuilder and then registered for scrollPlaceholder to reference by id.
    this.getUIContext().getPlaceholderRegister()
      .register('itemPlaceholder', wrapBuilder(ItemPlaceholder));
    const list: number[] = [];
    for (let i = 0; i < 10000; i++) {
      list.push(i);
    }
    this.data = list;
  }

  build() {
    Column({ space: 5 }) {
      List({ space: 10 }) {
        Repeat<number>(this.data)
          .each((repeatItem: RepeatItem<number>) => {
            ListItem() {
              Text(repeatItem.item.toString())
                .fontSize(16)
                .width('100%')
                .height(100)
                .textAlign(TextAlign.Center)
            }
          })
      }
      .width('90%')
      .height(300)
      // The id corresponds to the registered placeholder builder function, and size is the suggested size of the placeholder, which is consistent with the height of the real list item to reduce visual jumps during replacement.
      .scrollPlaceholder((index: number): PlaceholderOptions | undefined => {
        return { id: 'itemPlaceholder', size: { height: 100 } };
      })
    }
    .width('100%')
    .padding({ top: 10 })
    .backgroundColor('#FFDCDCDC')
  }
}
```
