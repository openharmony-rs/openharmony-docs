# @ohos.arkui.advanced.SegmentButton

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [SegmentButtonItemOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptions-c.md) | Button options in a segment button. |
| [SegmentButtonItemOptionsArray](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsarray-c.md) | Represents an array for storing button information. |
| [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) |  |

### Structs

| Name | Description |
| --- | --- |
| [SegmentButton](arkts-arkui-arkui-advanced-segmentbutton-segmentbutton-s.md) | The segment button component includes tab-style segment buttons and capsule-style segment buttons. Tab-style segment buttons are suitable for switching between pages or content areas. Capsule-style segment buttons are suitable for single-select or multi-select scenarios, including capsule-style single-select segment buttons and capsule-style multi-select segment buttons. This component supports custom appearance attributes such as text color, font size, font weight, background color, image size, padding, and background blur material. It supports three button styles: text-only, icon-only, and icon + text. It also provides capabilities such as accessibility reading, layout direction mirroring, custom rounded corners, and property animation, making it suitable for scenarios where you need to quickly build a segmented selection interface that complies with design specifications. |

### Interfaces

| Name | Description |
| --- | --- |
| [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md) | Represents configuration options for creating a **SegmentButton** component consisting of capsule-style segment buttons. |
| [CapsuleSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonoptions-i.md) | Provides configuration options for capsule-style segment buttons. Inherits from [CapsuleSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-capsulesegmentbuttonconstructionoptions-i.md). |
| [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md) | Defines the customizable attributes of a segment button component. |
| [SegmentButtonIconItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttoniconitem-i.md) | Icon button information. |
| [SegmentButtonIconTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonicontextitem-i.md) | Icon and text button information. |
| [SegmentButtonItemOptionsConstructorOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonitemoptionsconstructoroptions-i.md) | Construct parameters for SegmentButtonItemOptions. |
| [SegmentButtonTextItem](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttontextitem-i.md) | Text button information. |
| [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md) | Creates a SegmentButtonOptions object of the tab type. |
| [TabSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonoptions-i.md) | Provides configuration options for tab-style segment buttons. Inherits from [TabSegmentButtonConstructionOptions](arkts-arkui-arkui-advanced-segmentbutton-tabsegmentbuttonconstructionoptions-i.md). |

### Enums

| Name | Description |
| --- | --- |
| [BorderRadiusMode](arkts-arkui-arkui-advanced-segmentbutton-borderradiusmode-e.md) | Enumerates the border radius modes for the **SegmentButton** component, which are used to control the border radius calculation method. |

### Types

| Name | Description |
| --- | --- |
| [DimensionNoPercentage](arkts-arkui-dimensionnopercentage-t.md) | The percentage length union type is not supported. |
| [ItemRestriction](arkts-arkui-itemrestriction-t.md) | Tuple type that stores button information. |
| [SegmentButtonItemArray](arkts-arkui-segmentbuttonitemarray-t.md) | Represents the array union type used to store button information. |
| [SegmentButtonItemTuple](arkts-arkui-segmentbuttonitemtuple-t.md) | Represents the tuple union type used to store button information. |

## Examples

### Example 1: Setting the Type of the SegmentButton component

This example demonstrates how to create two different types of SegmentButton components by configuring SegmentButtonOptions with tab and capsule types.



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonItemTuple,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Tab type segment button array.
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab 1' }, { text: 'Tab 2' }, {
      text: 'Tab 3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    // Configure CommonSegmentButtonOptions to implement the background blur style.
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  // Capsule type segment button array.
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: 'Single-selection 1' }, { text: 'Single-selection 2' }, { text: 'Single-selection 3' }] as SegmentButtonItemTuple,
    multiply: false,
    // Configure CommonSegmentButtonOptions to implement the background blur style.
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  // Multi-select capsule type segment button array.
  @State multiplySelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: 'Multi-selection 1' }, { text: 'Multi-selection 2' }, { text: 'Multi-selection 3' }] as SegmentButtonItemTuple,
    multiply: true
  });
  // Capsule type segment button array with selected and unselected icons.
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: false,
    // Configure CommonSegmentButtonOptions to implement the background blur style.
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  // Multi-select capsule type segment button array with selected and unselected icons.
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: 'Icon 1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: true
  });
  @State tabSelectedIndexes: number[] = [1];
  @State singleSelectCapsuleSelectedIndexes: number[] = [0];
  @State multiplySelectCapsuleSelectedIndexes: number[] = [0, 1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          SegmentButton({
            options: this.tabOptions,
            selectedIndexes: $tabSelectedIndexes
          })
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $singleSelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.multiplySelectCapsuleOptions,
            selectedIndexes: $multiplySelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 2: Setting the Style of the SegmentButton component

Customize the text and background style of the segment button by configuring CommonSegmentButtonOptions.



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonItemTuple,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab 1' }, { text: 'Tab 2' }, {
      text: 'Tab 3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundColor: 'rgb(213,213,213)',
    selectedBackgroundColor: 'rgb(112,112,112)', // Configure CommonSegmentButtonOptions to implement the selected background color.
    textPadding: {
      top: 10,
      right: 10,
      bottom: 10,
      left: 10
    }, // Configure CommonSegmentButtonOptions to implement the text padding.
  });
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: 'Single-selection 1' }, { text: 'Single-selection 2' }, { text: 'Single-selection 3' }] as SegmentButtonItemTuple,
    multiply: false,
    fontColor: 'rgb(0,74,175)', // Configure CommonSegmentButtonOptions to implement the text color.
    selectedFontColor: 'rgb(247,247,247)', // Configure CommonSegmentButtonOptions to implement the selected text color.
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK // Configure CommonSegmentButtonOptions to implement the background blur style.
  });
  @State multiplySelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: 'Multi-selection 1' }, { text: 'Multi-selection 2' }, { text: 'Multi-selection 3' }] as SegmentButtonItemTuple,
    multiply: true,
    fontSize: 18,
    selectedFontSize: 18,
    fontWeight: FontWeight.Bolder, // Configure CommonSegmentButtonOptions to implement the text weight.
    selectedFontWeight: FontWeight.Lighter, // Configure CommonSegmentButtonOptions to implement the weight of the selected text.
  });
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: false,
    imageSize: { width: 40, height: 40 },
    buttonPadding: {
      top: 6,
      right: 10,
      bottom: 6,
      left: 10
    },
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: 'Icon 1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: true,
    imageSize: { width: 10, height: 10 },
  });
  @State tabSelectedIndexes: number[] = [0];
  @State singleSelectCapsuleSelectedIndexes: number[] = [0];
  @State multiplySelectCapsuleSelectedIndexes: number[] = [0, 1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 20 }) {
          SegmentButton({ options: this.tabOptions, selectedIndexes: $tabSelectedIndexes })
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $singleSelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.multiplySelectCapsuleOptions,
            selectedIndexes: $multiplySelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 3: Performing Array Operations on the SegmentButton Component

This example shows how to perform operations such as adding and removing segment buttons using array functions like pop, shift, and unshift.



```TypeScript
import {
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonItemOptionsArray,
  SegmentButtonItemTuple,
  SegmentButtonItemOptions
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Array of capsule-type segment buttons.
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: '1' }, { text: '2' }, { text: '3' },
      { text: '4' }, { text: '5' }] as SegmentButtonItemTuple,
    multiply: false,
    // Configure CommonSegmentButtonOptions to implement the background blur style.
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State capsuleSelectedIndexes: number[] = [0];

  build() {
    Row() {
      Column() {
        Column({ space: 10 }) {
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $capsuleSelectedIndexes
          })
          // Tap "Delete First Item" to delete the first button.
          Button('Delete First Item')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.shift()
            })
          // Tap "Delete Last Item" to delete the last button.
          Button('Delete Last Item')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.pop()
            })
          // Tap "Add to End" to add a button at the end.
          Button('Add to End')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.push({ text: 'push' })
            })
          // Tap "Add to Beginning" to add a button at the beginning.
          Button('Add to Beginning')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.unshift(({ text: 'unshift' }))
            })
          // Tap "Replace Items 2 and 3 with splice1 and splice2" to replace buttons 2 and 3 with splice1 and splice2.
          Button('Replace Items 2 and 3 with splice1 and splice2')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons.splice(1, 2, new SegmentButtonItemOptions({
                text: 'splice1'
              }), new SegmentButtonItemOptions({ text: 'splice2' }))
            })
          // Tap "Change All Button Text" to replace the button texts 1, 2, 3, 4, and 5 with a, b, c, d, and e.
          Button('Change All Button Text')
            .onClick(() => {
              this.singleSelectCapsuleOptions.buttons =
                SegmentButtonItemOptionsArray.create([{ text: 'a' }, { text: 'b' },
                  { text: 'c' }, { text: 'd' }, { text: 'e' }])
            })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 4: Implementing a Mirrored Layout

This example shows how to implement a mirrored layout for a SegmentButton component by configuring direction.



```TypeScript
import { LengthMetrics, SegmentButton, SegmentButtonOptions } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  // Tab-type segment button array.
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab 1' }, { text: 'Tab 2' }, {
      text: 'Tab 3'
    }],
    direction: Direction.Rtl, // Set the layout direction of the segment button.
    backgroundColor: Color.Green, // Set the background color of the segment button.
    selectedBackgroundColor: Color.Orange, // Set the background color of the segment button component in selected state.
    // Set the text padding.
    localizedTextPadding: {
      end: LengthMetrics.vp(10),
      start: LengthMetrics.vp(10)
    },
  });
  // Capsule-type segment button array.
  @State singleSelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: 'Single-selection 1' }, { text: 'Single-selection 2' }, { text: 'Single-selection 3' }],
    multiply: false, // Set whether the segment button component supports multiple selection.
    direction: Direction.Rtl, // Set the layout direction of the segment button.
    fontColor: Color.Black, // Set the text color of the segment button component in unselected state.
    selectedFontColor: Color.Yellow, // Set the text color of the segment button component in selected state.
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK // Set the background blur material of the segment button component.
  });
  // Capsule-type segment button array.
  @State multiplySelectCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [{ text: 'Multi-selection 1' }, { text: 'Multi-selection 2' }, { text: 'Multi-selection 3' }],
    multiply: true, // Set whether the segment button component supports multiple selection.
    direction: Direction.Rtl, // Set the layout direction of the segment button.
    fontSize: 18, // Set the font size of the segment button component in unselected state.
    selectedFontSize: 18, // Set the font size of the segment button component in selected state.
    fontWeight: FontWeight.Bolder, // Set the font weight of the segment button component in unselected state.
    selectedFontWeight: FontWeight.Lighter, // Set the font weight of the segment button component in selected state.
  });
  // Capsule-type segment button array.
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ],
    multiply: false, // Set whether the segment button component supports multiple selection.
    direction: Direction.Rtl, // Set the layout direction of the segment button.
    imageSize: { width: 40, height: 40 }, // Set the image size of the segment button component.
    // Set the button padding of the segment button component, which adapts to the layout direction (LTR/RTL).
    localizedButtonPadding: {
      end: LengthMetrics.vp(10),
      start: LengthMetrics.vp(10)
    },
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK // Set the background blur material of the segment button component.
  });
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: 'Icon 1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ],
    multiply: true, // Set whether the segment button component supports multiple selection.
    direction: Direction.Rtl, // Set the layout direction of the segment button.
    imageSize: { width: 10, height: 10 }, // Set the image size of the segment button component.
  });
  @State tabSelectedIndexes: number[] = [0];
  @State singleSelectCapsuleSelectedIndexes: number[] = [0];
  @State multiplySelectCapsuleSelectedIndexes: number[] = [0, 1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 20 }) {
          SegmentButton({ options: this.tabOptions, selectedIndexes: $tabSelectedIndexes })
          SegmentButton({
            options: this.singleSelectCapsuleOptions,
            selectedIndexes: $singleSelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.multiplySelectCapsuleOptions,
            selectedIndexes: $multiplySelectCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 5: Setting Accessibility

This example showcases how to implement accessibility features for the SegmentButton component by configuring attributes such as accessibilityLevel and selectedIconAccessibilityText.

```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonItemTuple,
  SegmentButtonOptions,
  SegmentButtonTextItem,
  SegmentButtonItemOptions
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab 1', accessibilityLevel: 'yes', accessibilityDescription: 'Tab 1 usage hints' },
      { text: 'Tab 2', accessibilityLevel: 'yes', accessibilityDescription: 'Tab 2 usage hints' },
      {
        text: 'Tab 3 ', accessibilityLevel: 'yes', accessibilityDescription: 'Tab 3 usage hints'
      }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State iconCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconItem newbie reminder' // Accessibility description.
      },
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconItem newbie reminder' // Accessibility description.
      },
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconItem newbie reminder' // Accessibility description.
      },
      {
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility importance. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconItem newbie reminder' // Accessibility description.
      }
    ] as SegmentButtonItemTuple,
    multiply: false,
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK
  });
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      {
        text: 'Icon 1',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconTextItem newbie reminder' // Accessibility description.
      },
      {
        text: 'Icon 2',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconTextItem newbie reminder' // Accessibility description.
      },
      {
        text: 'Icon 3',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconTextItem newbie reminder' // Accessibility description.
      },
      {
        text: 'Icon 4',
        icon: $r('sys.media.ohos_ic_public_email'),
        iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
        selectedIcon: $r('sys.media.ohos_ic_public_clock'),
        selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
        accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
        accessibilityDescription: 'SegmentButtonIconTextItem newbie reminder' // Accessibility description.
      }
    ] as SegmentButtonItemTuple,
    multiply: true
  });
  @State tabSelectedIndexes: number[] = [1];
  @State singleSelectIconCapsuleSelectedIndexes: number[] = [3];
  @State multiplySelectIconTextCapsuleSelectedIndexes: number[] = [1, 2];

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          SegmentButton({
            options: this.tabOptions,
            selectedIndexes: $tabSelectedIndexes
          })
          SegmentButton({
            options: this.iconCapsuleOptions,
            selectedIndexes: $singleSelectIconCapsuleSelectedIndexes
          })
          SegmentButton({
            options: this.iconTextCapsuleOptions,
            selectedIndexes: $multiplySelectIconTextCapsuleSelectedIndexes
          })
          Button('Replace Items 2 and 3 with splice1 and splice2')
            .onClick(() => {
              this.iconTextCapsuleOptions.buttons.splice(1, 2, new SegmentButtonItemOptions({
                text: 'splice1', accessibilityLevel: 'yes', accessibilityDescription: 'SegmentButtonItemOptions usage hints'
              }), new SegmentButtonItemOptions({
                text: 'splice2',
                icon: $r('sys.media.ohos_ic_public_email'),
                iconAccessibilityText: 'Accessibility text for unselected icon', // Accessibility text for the icon of the unselected button.
                selectedIcon: $r('sys.media.ohos_ic_public_clock'),
                selectedIconAccessibilityText: 'Accessibility text for selected icon', // Accessibility text for the icon of the selected button.
                accessibilityLevel: 'yes', // Accessibility level. Controls whether the current component can be recognized by accessibility services.
                accessibilityDescription: 'SegmentButtonIconTextItem newbie reminder' // Accessibility description.
              }))
            })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 6: Setting Custom Border Radius

This example demonstrates how to set a custom border radius for the SegmentButton component.



```TypeScript
import {
  BorderRadiusMode,
  ItemRestriction,
  LengthMetrics,
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonTextItem
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab 1' }, { text: 'Tab 2' }, {
      text: 'Tab 3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundBlurStyle: BlurStyle.BACKGROUND_THICK,
    borderRadiusMode: BorderRadiusMode.CUSTOM, // Customize the corner radius of the border.
    backgroundBorderRadius: LengthMetrics.vp(8),
    itemBorderRadius: LengthMetrics.vp(6)
  });
  @State tabSelectedIndexes: number[] = [1];

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          SegmentButton({
            options: this.tabOptions,
            selectedIndexes: $tabSelectedIndexes,
          })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 7: Enabling Property Animation for SegmentButton

This example demonstrates how to enable property animation for SegmentButton. That is, after enableStateAnimation is set to true, modifying the selectedIndexes value triggers a button switching animation. In addition, two SegmentButton components with the same selectedIndexes value present different switching animations depending on whether property animation is enabled.

Since API version 24, [SegmentButton](#segmentbutton-1) has added the enableStateAnimation attribute.



```TypeScript
import { SegmentButton, SegmentButtonItemTuple, SegmentButtonOptions } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State singleSelectTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: 'Single-select 1' }, { text: 'Single-select 2' }, { text: 'Single-select 3' }
    ] as SegmentButtonItemTuple,
    multiply: false
  });

  @State textCapsuleSingleSelected: number[] = [0]; // Index of the selected single-select. The first button is selected by default.

  enableStateAnimation: boolean[] = [false, true];
  @State enableStateAnimationIndex: number = 0;
  @State currentSelectedIndex: number = 0; // Index counter for switching the selected item.

  build() {
    Row() {
      Column() {
        Column({ space: 25 }) {
          // The animation takes effect only when the selected item is switched by manual tap. Switching the selected item through non-tap operations does not trigger the animation.
          SegmentButton({
            options: this.singleSelectTextCapsuleOptions,
            selectedIndexes: this.textCapsuleSingleSelected // Property animation is not enabled.
          })

          Text('enableStateAnimation: ' + this.enableStateAnimation[this.enableStateAnimationIndex])
            .fontSize(18)
            .fontWeight(FontWeight.Bold)

          Row({ space: 10 }) {
            Button('false')
              .onClick(() => {
                this.enableStateAnimationIndex = 0;
              })

            Button('true')
              .onClick(() => {
                this.enableStateAnimationIndex = 1;
              })
          }
          .width('100%')
          .justifyContent(FlexAlign.Center)
          .margin({ bottom: 10 })

          // When enableStateAnimation is true, switching the selected item triggers the button switching animation. When enableStateAnimation is false, the animation takes effect only when the selected item is switched by manual tap. Switching the selected item through non-tap operations does not trigger the animation.
          SegmentButton({
            options: this.singleSelectTextCapsuleOptions,
            selectedIndexes: this.textCapsuleSingleSelected,
            enableStateAnimation: this.enableStateAnimation[this.enableStateAnimationIndex] // Property animation is enabled.
          })

          Button('change selectedIndexes')
            .onClick(() => {
              // Increment the index of the selected item. If the index exceeds the maximum, reset it to 0.
              this.currentSelectedIndex = this.currentSelectedIndex < 2 ? this.currentSelectedIndex + 1 : 0;
              this.textCapsuleSingleSelected = [this.currentSelectedIndex];
            })
        }.width('90%')
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 8: Setting the Background Material

The following example uses the backgroundSystemMaterial attribute to set a transparent background material for the segment button, enable automatic color inversion and interactive deformation effects, and customize the color of the feedback light effect.

Starting from API version 26.0.0, the backgroundSystemMaterial attribute has been added to [SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) and [CommonSegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-commonsegmentbuttonoptions-i.md).



```TypeScript
import {
  ItemRestriction,
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonTextItem,
  uiMaterial
} from '@kit.ArkUI';


@Entry
@Component
struct Index {
  @State tabOptions: SegmentButtonOptions = SegmentButtonOptions.tab({
    buttons: [{ text: 'Tab button 1' }, { text: 'Tab button 2' }, {
      text: 'Tab button 3'
    }] as ItemRestriction<SegmentButtonTextItem>,
    backgroundColor: Color.Transparent,
    // Set fontColor to a special system resource value to enable automatic color inversion.
    fontColor: $r('sys.color.font_primary'),
    // Set the system material style to ULTRA_THIN, and enable automatic color inversion, interactive deformation effect, and custom feedback light color.
    backgroundSystemMaterial: new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.ULTRA_THIN,
      colorInvert: true,
      interactive: true,
      lightEffect: { color: undefined }
    })
  });
  @State tabSelectedIndexes: number[] = [0];

  build() {
    Column({ space: 20 }) {
      SegmentButton({
        options: this.tabOptions,
        selectedIndexes: $tabSelectedIndexes
      })
    }
    .width('100%')
    .height('20%')
    .padding(20)
    .linearGradient({
      angle: 90, // Gradient angle. 90 degrees means from left to right.
      colors: [
        ['#FF9A9E', 0.0], // Start color and position (0.0 indicates the start point).
        ['#FECFEF', 0.1], // Intermediate color and position.
        ['#3B324C', 1.0] // End color and position (1.0 indicates the end point).
      ]
    })
  }
}
```

### Example 9: Listening for Changes to Properties in SegmentButtonOptions

[SegmentButtonOptions](arkts-arkui-arkui-advanced-segmentbutton-segmentbuttonoptions-c.md) uses the @Observed decorator, and the SegmentButton component receives this object through @ObjectLink. For first-level basic type properties of SegmentButtonOptions (such as fontColor and backgroundColor), the linkage mechanism of @Observed and @ObjectLink can already observe property changes and trigger UI refresh without additional processing. However, for internal properties of object-type properties in SegmentButtonOptions (such as width and height of imageSize, or properties of buttonPadding), which are deeper nested properties, @State can only observe first-level assignment changes and cannot detect modifications to such deep properties. As a result, the UI does not automatically refresh when internal properties of object-type properties are modified. Using the [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved) API to wrap object-type properties (such as imageSize) can add deep observation capability to the internal properties of the object, so that when internal properties (such as width and height) are modified, the framework can detect the changes and trigger UI refresh. For details about the makeObserved API, see [makeObserved API: Changing Unobservable Data to Observable Data](../../../ui/state-management/arkts-new-makeObserved.md).

The following example compares two scenarios: tapping the "Change fontColor" button changes the fontColor property of iconTextCapsuleOptions (a first-level basic type property, already supported for observation through @Observed and @ObjectLink), and the UI automatically refreshes. Tapping the "Change icon size" button changes the width and height properties of iconTextCapsuleOptions.imageSize (internal properties of the imageSize object, which require UIUtils.makeObserved to wrap imageSize for observation), and the UI also automatically refreshes.

```TypeScript
import {
  SegmentButton,
  SegmentButtonOptions,
  SegmentButtonItemTuple,
  UIUtils
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State iconTextCapsuleOptions: SegmentButtonOptions = SegmentButtonOptions.capsule({
    buttons: [
      { text: 'Icon 1', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 2', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 3', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 4', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') },
      { text: 'Icon 5', icon: $r('sys.media.ohos_ic_public_email'), selectedIcon: $r('sys.media.ohos_ic_public_clock') }
    ] as SegmentButtonItemTuple,
    multiply: false,
    // Wrap imageSize with UIUtils.makeObserved so that its internal properties width and height can be observed.
    imageSize: UIUtils.makeObserved({ width: 30, height: 30 })
  });
  @State selectedIndexes: number[] = [0];
  @State currentFontColor: ResourceColor = Color.Blue;

  build() {
    Column({ space: 20 }) {
      SegmentButton({
        options: this.iconTextCapsuleOptions,
        selectedIndexes: $selectedIndexes
      })
      // The first-level primitive property, this.iconTextCapsuleOptions.fontColor, is already observable through @Observed and @ObjectLink, so the UI refreshes automatically.
      Button('Change fontColor')
        .onClick(() => {
          if (this.currentFontColor === Color.Blue) {
            this.currentFontColor = Color.Red;
          } else {
            this.currentFontColor = Color.Blue;
          }
          this.iconTextCapsuleOptions.fontColor = this.currentFontColor;
        })
      // Change the internal properties of imageSize. The UI refreshes automatically because of the makeObserved wrapper.
      Button('Change icon size')
        .onClick(() => {
          this.iconTextCapsuleOptions.imageSize.width = 10;
          this.iconTextCapsuleOptions.imageSize.height = 10;
        })
    }
    .width('100%')
    .height('50%')
    .padding({ top: 20 })
  }
}
```
