# @ohos.inputMethodList(Input Method List)

The **inputMethodList** module is oriented to system applications and input method applications.
 It provides APIs for implementing an input method list. This list displays the default input method subtypes and
 third-party input methods. Users can use this list to switch from the default input method to another input method.
 <br>
 <br> > **NOTE**
 <br> >
 <br> > This component is supported since API version 11.
 Updates will be marked with a superscript to indicate their earliest API version.
 <br>
 <br>

## Child Components

<br><br>Not supported<br><br>

## Attributes

<br><br>The [universal attributes](../../apis-arkui/arkts-components/arkts-arkui-common-comp.md#common) are not supported.<br><br>

## Events

<br><br>The [universal events](../../apis-arkui/arkts-components/arkts-arkui-common-comp.md#common) are not supported.<br><br>## Example<br><br>```ts
 <br>import { Pattern, PatternOptions } from '@kit.IMEKit';
 <br>
 <br>@Entry
 <br>// Configure the component.
 <br>@Component
 <br>struct SettingsItem {
 <br>  @State defaultPattern: number = 1;
 <br>  private oneHandAction: PatternOptions = {
 <br>    defaultSelected: this.defaultPattern,
 <br>    patterns: [ // Icons in patterns can be used only after the corresponding icon resources have been added to
 the resource directory of the project.
 <br>      {
 <br>        icon: $r('app.media.hand_icon'), // Icon resource for the input method mode option, for example,
 the icon for the one-handed mode.
 <br>        selectedIcon: $r('app.media.hand_icon_selected') // Icon resource for the input method mode option in
 the selected state, for example, the icon for the one-handed mode in the selected state.
 <br>      },
 <br>      {
 <br>        icon: $r('app.media.hand_icon1'),
 <br>        selectedIcon: $r('app.media.hand_icon_selected1')
 <br>      },
 <br>      {
 <br>        icon: $r('app.media.hand_icon2'),
 <br>        selectedIcon: $r('app.media.hand_icon_selected2'),
 <br>      }],
 <br>    action:(index: number)=&gt;{
 <br>      console.info(`pattern is changed, current is ${index}`);
 <br>      this.defaultPattern = index;
 <br>    }
 <br>  };
 <br>  private listController: CustomDialogController = new CustomDialogController({
 <br>    builder: InputMethodListDialog({ patternOptions: this.oneHandAction }),
 <br>    customStyle: true,
 <br>    maskColor: '#00000000'
 <br>  });
 <br>
 <br>  build() {
 <br>    Column() {
 <br>      Flex({ direction: FlexDirection.Column,
 <br>        alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
 <br>        Text("Input Method List").fontSize(20)
 <br>      }
 <br>    }
 <br>    .width("13%")
 <br>    .id('bindInputMethod')
 <br>    .onClick((event?: ClickEvent) =&gt; {
 <br>      this.listController.open();
 <br>    })
 <br>  }
 <br>}
 <br>```

## Modules to Import

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md) | InputMethodListDialog({controller: CustomDialogController, patternOptions?: PatternOptions})<br> <br>Implements a dialog box showing the input method list. |

### Interfaces

| Name | Description |
| --- | --- |
| [Pattern](arkts-ime-inputmethodlist-pattern-i.md) |  |
| [PatternOptions](arkts-ime-inputmethodlist-patternoptions-i.md) |  |

## Examples

```TypeScript
import { PatternOptions, InputMethodListDialog } from '@kit.IMEKit';

@Entry
// Set the component.
@Component
struct SettingsItem {
  @State defaultPattern: number = 1;
  private oneHandAction: PatternOptions = {
    defaultSelected: this.defaultPattern,
    patterns: [ // The icons in patterns can be used only after the corresponding icon resources are added to the resource directory of the project.
      {
        icon: $r('app.media.hand_icon'), // This is the icon resource of the input method mode option, for example, the one-handed mode icon.
        selectedIcon: $r('app.media.hand_icon_selected') // This is the selected state of the icon resource of the input method mode option, for example, the selected state icon of the one-handed mode.
      },
      {
        icon: $r('app.media.hand_icon1'),
        selectedIcon: $r('app.media.hand_icon_selected1')
      },
      {
        icon: $r('app.media.hand_icon2'),
        selectedIcon: $r('app.media.hand_icon_selected2')
      }],
    // Callback function invoked when the mode option changes.
    action: (index: number) => {
      console.info(`pattern is changed, current is ${index}`);
      this.defaultPattern = index; // Update the default selected mode.
    }
  };
  // Create a custom dialog controller.
  private listController: CustomDialogController = new CustomDialogController({
    builder: InputMethodListDialog({ patternOptions: this.oneHandAction }), // Build the input method list dialog.
    customStyle: true,
    maskColor: '#00000000'
  });

  build() {
    Column() {
      Flex({
        direction: FlexDirection.Column,
        alignItems: ItemAlign.Center, 
        justifyContent: FlexAlign.Center 
      }) {
        Text('Input method switching list').fontSize(20)
      }
    }
    .width('13%')
    .id('bindInputMethod')
    .onClick((event?: ClickEvent) => {
      this.listController.open();
    })
  }
}
```
