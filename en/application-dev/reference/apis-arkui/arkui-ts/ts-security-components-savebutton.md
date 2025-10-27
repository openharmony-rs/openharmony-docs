# SaveButton

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

**SaveButton** is a security component that provides a save button. After it is integrated into your application and is used for the first time, a dialog box is displayed to ask for user authorization. If the user taps **Allow**, the application automatically obtains the permission to access the media library within one minute. No more dialog box is displayed for authorization.

> **NOTE**
>
> This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

## Child Components

Not supported

## APIs

### SaveButton

SaveButton()

Creates a **SaveButton** component with an icon, text, and background.

You may want to learn the [restrictions on security component styles](../../../security/AccessToken/security-component-overview.md#constraints) to avoid authorization failures caused by incompliant styles.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### SaveButton

SaveButton(options: SaveButtonOptions)

Creates a **SaveButton** component that contains the specified elements.

You may want to learn the [restrictions on security component styles](../../../security/AccessToken/security-component-overview.md#constraints) to avoid authorization failures caused by incompliant styles.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [SaveButtonOptions](#savebuttonoptions) | Yes| Options for creating the **SaveButton** component.|

## SaveButtonOptions

Describes the icon, text, and other specific elements for the **SaveButton** component.

> **NOTE**
>
> - At least one of **icon** or **text** must be provided.<br>
> - If neither **icon** nor **text** is provided, the **options** parameter in [SaveButton](#savebutton-1) will not take effect, and the created **SaveButton** component will use the default style:
>
>   The default value of **SaveIconStyle** is **FULL_FILLED**.
>
>   The default style of **SaveDescription** is **DOWNLOAD**.
>
>   The default value of **ButtonType** is **Capsule**.
> - The **icon**, **text**, and **buttonType** parameters do not support dynamic modification.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| icon | [SaveIconStyle](#saveiconstyle) | No| Yes| Icon style of the **SaveButton** component.<br>If this parameter is not specified, there is no icon.|
| text | [SaveDescription](#savedescription) | No| Yes| Text on the **SaveButton** component.<br>If this parameter is not specified, there is no text description.|
| buttonType | [ButtonType](ts-securitycomponent-attributes.md#buttontype) | No| Yes| Background type of the **SaveButton** component.<br>If this parameter is not specified, the system uses a capsule-type button as the **SaveButton** component.|

## SaveIconStyle

Enumerates icon styles of the **SaveButton** component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| FULL_FILLED | 0 | Filled style icon.|
| LINES | 1 | Line style icon.|

## SaveDescription

Enumerates text descriptions of the **SaveButton** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| DOWNLOAD | 0 | The text on the **SaveButton** component is **Download**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| DOWNLOAD_FILE | 1 | The text on the **SaveButton** component is **Download file**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SAVE | 2 | The text on the **SaveButton** component is **Save**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SAVE_IMAGE | 3 | The text on the **SaveButton** component is **Save image**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SAVE_FILE | 4 | The text on the **SaveButton** component is **Save file**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| DOWNLOAD_AND_SHARE | 5 | The text on the **SaveButton** component is **Download & share**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| RECEIVE | 6 | The text on the **SaveButton** component is **Receive**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| CONTINUE_TO_RECEIVE | 7 | The text on the **SaveButton** component is **Continue**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SAVE_TO_GALLERY<sup>12+</sup> | 8 | The text on the **SaveButton** component is **Save to Gallery**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| EXPORT_TO_GALLERY<sup>12+</sup> | 9 | The text on the **SaveButton** component is **Export**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| QUICK_SAVE_TO_GALLERY<sup>12+</sup> | 10 | The text on the **SaveButton** component is **Save to Gallery**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| RESAVE_TO_GALLERY<sup>12+</sup> | 11 | The text on the **SaveButton** component is **Resave**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| SAVE_ALL<sup>18+</sup> | 12 | The text on the **SaveButton** component is **Save all**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## SaveButtonOnClickResult

Enumerates the authorization results after the **SaveButton** component is tapped.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| SUCCESS | 0 | Authorization is successful.|
| TEMPORARY_AUTHORIZATION_FAILED | 1 | Authorization fails.|
| CANCELED_BY_USER<sup>21+</sup>  | 2 | Authorization is canceled by the user through a dialog box after the **SaveButton** component is tapped.|

## SaveButtonCallback<sup>18+</sup>

type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError&lt;void&gt;) =&gt; void

Triggered when the **SaveButton** component is clicked.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| event | [ClickEvent](ts-universal-events-click.md#clickevent) |Yes|See **ClickEvent**.|
| result | [SaveButtonOnClickResult](#savebuttononclickresult)| Yes| Authorization result of the storage permission. The authorization duration is one minute. That is, after the click event is triggered, the specific media library API can be called unlimited times within one minute. If the call is made beyond one minute, the authentication will fail.|
| error | [BusinessError&lt;void&gt;](../../apis-basic-services-kit/js-apis-base.md#businesserror) | No| Error code and message when the component is clicked.<br>Error code 0 indicates that the authorization is successful or the user cancels the authorization.<br>Error code 1 indicates an internal system error, including but not limited to:<br>1. IPC communication failure.<br>2. Failed to display the security control dialog box.<br>Error code 2 indicates attribute setting errors, including but not limited to:<br>1. The font or icon size is too small.<br>2. The font or icon color is too similar to the background color.<br>3. The font or icon color is too transparent.<br>4. The padding is negative.<br>5. The component is obscured by other components or windows.<br>6. The text exceeds the background range.<br>7. The component exceeds the window or screen bounds.<br>8. The component size is too large.<br>9. The component text is truncated and not fully displayed.<br>10. Related attribute settings affect the display of security components.|

## SaveButtonAttribute
SaveButtonAttribute provides methods for setting attributes such as custom icon (setIcon), custom text (setText), icon size (iconSize), icon corner radius (iconBorderRadius), and pressed state effect (stateEffect).

**Atomic service API**: This API can be used in atomic services since API version 11.

### setIcon<sup>20+</sup>

setIcon(icon: Resource)

Sets the icon of the save control.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| icon | [Resource](ts-types.md#resource) |Yes|Custom icon resource information. Only data sources of the Resource type are supported.<br>Images in the following formats are supported: PNG, JPG, JPEG, BMP, SVG, WebP, GIF, and HEIF. For details about the supported image formats, see [Image](ts-basic-components-image.md). If the resource is not an image resource or the format is not supported, the icon is displayed as blank.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the custom icon setting does not take effect, and the Save control retains the default style. For details, see [SaveButtonOptions](#savebuttonoptions).|

### setText<sup>20+</sup>

setText(text: string | Resource)

Sets the text of the Save control.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| text | string \| [Resource](ts-types.md#resource) |Yes|Custom text.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the custom text setting does not take effect, and the Save control retains the default style. For details, see [SaveButtonOptions](#savebuttonoptions).|

### iconSize<sup>20+</sup>

iconSize(size: Dimension | SizeOptions)

Sets the icon size of the Save control.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| size | [Dimension](ts-types.md#dimension10) \| [SizeOptions](ts-types.md#sizeoptions) |Yes|Icon size. Percentage strings are not supported. The default width and height are both 16 vp.<br>For the system icons provided by the Save control:<br>- When the Dimension type is used as the input parameter, the width and height are the same and are the specified values.<br>- When the SizeOptions type is used as the input parameter, if the specified width and height are different, the smaller value is used. If only one value is specified, the value is used as the width and height.<br>For custom icons:<br>- If the input parameter is of the Dimension type, the width and height are equal and are set to the specified value.<br>- If the input parameter is of the SizeOptions type, you are advised to set both the width and height. In this case, the specified width and height take effect. If only one of the values is set, the width and height are displayed as the specified value.<br>- If the ratio of the specified width and height is different from that of the custom icon, the image is displayed in the [ImageFit.Cover](ts-appendix-enums.md#imagefit) mode.|

### iconBorderRadius<sup>20+</sup>

iconBorderRadius(radius: Dimension | BorderRadiuses)

Sets the radius of the rounded corners of the border of the save control icon.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| radius | [Dimension](ts-types.md#dimension10) \| [BorderRadiuses](ts-types.md#borderradiuses9) |Yes|Rounded corner radius of the border of the save control icon. You can set four rounded corners.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the rounded corner radius setting does not take effect.|

### stateEffect<sup>20+</sup>

stateEffect(enabled: boolean)

Sets the press effect of the save control.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| enabled | boolean |Yes| Whether to enable the press effect. true: The press effect is displayed when the save control is pressed. false: The press effect is not displayed when the save control is pressed.<br>Default value: **true**.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the setting does not take effect.|

### userCancelEvent<sup>21+</sup>

userCancelEvent(enabled: boolean)

Sets the user authorization cancellation event for the save control.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| enabled | boolean | Yes| Whether to receive the user authorization cancellation event for the save control. The options are true (yes) and false (no).<br>Default value: **false**.<br>|

## Attributes

This component does not support common attributes and inherits only the common attributes of security components (ts-securitycomponent-attributes.md).

## Events

Only the following events are supported.

### onClick

onClick(event: SaveButtonCallback)

Called when a click event occurs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| event | [SaveButtonCallback](#savebuttoncallback18) |Yes|See **SaveButtonCallback**.<br>In API versions 10 to 17, the parameter type is (event: [ClickEvent](ts-universal-events-click.md#clickevent), result: [SaveButtonOnClickResult](#savebuttononclickresult)) => void.<br>Since API version 18, the parameter type changes into SaveButtonCallback.|

## Example 1

```ts
// xxx.ets
import { photoAccessHelper } from '@kit.MediaLibraryKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  handleSaveButtonClick: SaveButtonCallback =
    async (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError) => {
      if (result === SaveButtonOnClickResult.SUCCESS) {
        try {
          const context = this.getUIContext().getHostContext();
          let helper = photoAccessHelper.getPhotoAccessHelper(context);
          // Call createAsset() within 1 minute after onClick is triggered to create an image file. After 1 minute have elapsed, the permission for calling createAsset is revoked.
          let uri = await helper.createAsset(photoAccessHelper.PhotoType.IMAGE, 'png');
          // Open the file based on its URI. The write process is not time bound.
          let file = await fileIo.open(uri, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
          // Write to the file.
          await fileIo.write(file.fd, "context");
          // Close the file.
          await fileIo.close(file.fd);
        } catch (error) {
          console.error(`errCode: ${error.code}, errMessage: ${error.message}`);
        }
      } else if (result === SaveButtonOnClickResult.CANCELED_BY_USER) {
        console.info("errCode: " + error?.code);
        console.info("errMessage: " + error?.message);
      } else {
        console.error("errCode: " + error?.code);
        console.error("errMessage: " + error?.message);
      }
    };

  build() {
    Row() {
      Column({ space: 10 }) {
        // Create a default button with an icon, text, and background.
        SaveButton().onClick((this.handleSaveButtonClick))
        // Whether the button has an icon, text, and background depends on whether the corresponding parameter is passed in. If buttonType is not passed in, the button uses the ButtonType.Capsule settings.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED })
        //If only the icon and background are displayed, the alpha value of the high eight bits of the background color is forcibly adjusted to 0xff by the system if it is less than 0x1a.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, buttonType: ButtonType.Capsule })
          .backgroundColor(0x10007dff)
        //If the icon, text, and background exist, the alpha value of the high eight bits of the background color is forcibly adjusted to 0xff by the system if it is less than 0x1a.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Capsule })
        // Create a button with an icon, text, and background. If the set width is less than the minimum allowed, the button's text will wrap to guarantee full text display.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Capsule })
          .fontSize(16)
          .width(30)
        // Create a button with an icon, text, and background. If the set width is less than the minimum allowed, the button's text will wrap to guarantee full text display.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Capsule })
          .fontSize(16)
          .size({ width: 30, height: 30 })
        // Create a button with an icon, text, and background. If the set width is less than the minimum allowed, the button's text will wrap to guarantee full text display.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD, buttonType: ButtonType.Capsule })
          .fontSize(16)
          .constraintSize({
            minWidth: 0,
            maxWidth: 30,
            minHeight: 0,
            maxHeight: 30
          })
        //Set the event for the secure control to receive the user's authorization cancellation.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .onClick((this.handleSaveButtonClick))
          .userCancelEvent(true)
      }.width('100%')
    }.height('100%')
  }
}
```



## Example 2

The application needs to apply for the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission.

```ts
// xxx.ets
@Entry
@Component
struct SetIcon {
  build() {
    Row() {
      Column({ space: 10 }) {
        // Set the icon to the resource type. The icon is displayed when the permission is granted.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setIcon($r('app.media.startIcon'))
        // Set the text to the string type. The text is displayed when the permission is granted.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setText("Save control settings text")
        // Set the text type to resource. The resource text is displayed if the user has the permission.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setText($r('app.string.app_name'))
        // Set the size of the save control icon. The input parameter is of the Dimension type.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .iconSize(28)
        // Set the default size of the save control icon. The input parameter is of the SizeOptions type. The smaller value between the width and height is used as the default icon size.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .iconSize({ width: 20, height: 40 })
        // Set the size of the custom save control icon. The input parameter is of the SizeOptions type. The image is displayed based on the configured width and height.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setIcon($r('app.media.startIcon'))
          .iconSize({ width: 30, height: 40 })
        // Set the size of the custom save control icon. The input parameter is of the SizeOptions type and only one value is set. The width and height of the image are both the configured value.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setIcon($r('app.media.startIcon'))
          .iconSize({ width: 40 })
        // Set the rounded corner of the save control icon. The input parameter is of the Dimension type. The radius of the four rounded corners of the image is the input parameter value.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .backgroundColor(Color.Orange)
          .setIcon($r('app.media.background'))
          .iconSize(30)
          .iconBorderRadius(6)
        // Set the rounded corner of a square icon to be greater than half of the side length so that the icon is displayed as a circle.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, buttonType: ButtonType.Circle })
          .backgroundColor(Color.Orange)
          .setIcon($r('app.media.foreground'))
          .iconSize(30)
          .iconBorderRadius(30)
          .padding(0)
        // Set the iconBorderRadius attribute to a circle, set the background color to transparent, and set the border.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, buttonType:ButtonType.Circle })
          .setIcon($r('app.media.background'))
          .backgroundColor(Color.Transparent)
          .iconSize(40)
          .iconBorderRadius(30)
          .borderWidth(1)
          .borderColor(Color.Black)
          .borderStyle(BorderStyle.Solid)
          .padding(10)
        // Set the rounded corner of the icon of the save control. The input parameter is of the BorderRadiuses type. The radius of the four rounded corners of the image is the size of the corresponding input parameter. If no rounded corner is set, no rounded corner is displayed.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .backgroundColor(Color.Orange)
          .setIcon($r('app.media.background'))
          .iconSize(30)
          .iconBorderRadius({ topLeft: 10, topRight: 16, bottomRight: 20 })
        //Disable the press effect of the save control.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .stateEffect(false)
      }.width('100%')
    }.height('100%')
  }
}
```

