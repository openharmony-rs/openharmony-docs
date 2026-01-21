# SaveButton

<!--Kit: ArkUI-->
<!--Subsystem: Security-->
<!--Owner: @harylee-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

**SaveButton** is a security component that provides a save button. After it is integrated into your application and is used for the first time, a dialog box is displayed to ask for user authorization. If the user taps **Allow**, the application automatically obtains the permission to access the media library within a short period of time. No more dialog box is displayed for authorization. For API version 19 and earlier, the authorization duration is 10 seconds. For API version 20 and later, the authorization duration is 1 minute.

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
> - If neither **icon** nor **text** is provided, the **options** parameter in **SaveButton** will not take effect, and the created **SaveButton** component will use the default style:
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

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| SUCCESS | 0 | Authorization is successful.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| TEMPORARY_AUTHORIZATION_FAILED | 1 | Authorization fails.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| CANCELED_BY_USER<sup>21+</sup>  | 2 | Authorization is canceled by the user through a dialog box after the **SaveButton** component is tapped.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|

## SaveButtonCallback<sup>18+</sup>

type SaveButtonCallback = (event: ClickEvent, result: SaveButtonOnClickResult, error?: BusinessError&lt;void&gt;) =&gt; void

Triggered when the **SaveButton** component is clicked.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| event | [ClickEvent](ts-universal-events-click.md#clickevent) |Yes|See **ClickEvent**.|
| result | [SaveButtonOnClickResult](#savebuttononclickresult)| Yes| Authorization result.|
| error | [BusinessError&lt;void&gt;](../../apis-basic-services-kit/js-apis-base.md#businesserror) | No| Error code and message when the component is clicked.<br>Error code 0 indicates that the authorization is successful or the user cancels the authorization.<br>Error code 1 indicates an internal system error, including but not limited to:<br>1. IPC failed.<br>2. Failed to display the security component dialog box.<br>Error code 2 indicates attribute setting errors, including but not limited to:<br>1. The font or icon size is too small.<br>2. The font or icon color is too similar to the background color.<br>3. The font or icon color is too transparent.<br>4. The padding is negative.<br>5. The component is obscured by other components or windows.<br>6. The text exceeds the background range.<br>7. The component exceeds the window or screen bounds.<br>8. The component size is too large.<br>9. The component text is truncated and not fully displayed.<br>10. Related attribute settings affect the display of security components.|

## SaveButtonAttribute
SaveButtonAttribute provides methods for setting attributes such as custom icon (setIcon), custom text (setText), icon size (iconSize), icon corner radius (iconBorderRadius), and pressed state effect (stateEffect).

**Atomic service API**: This API can be used in atomic services since API version 11.

### setIcon<sup>20+</sup>

setIcon(icon: Resource)

Sets the icon of the **SaveButton** component.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| icon | [Resource](ts-types.md#resource) |Yes|Custom icon resource information. Only data sources of the Resource type are supported.<br>Images in the following formats are supported: PNG, JPG, JPEG, BMP, SVG, WebP, GIF, and HEIF. For details about the supported image formats, see [Image](ts-basic-components-image.md). If the resource is not an image resource or the format is not supported, the icon is displayed as blank.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the custom icon setting does not take effect, and the **SaveButton** component retains the default style. For details, see [SaveButtonOptions](#savebuttonoptions).|

### setText<sup>20+</sup>

setText(text: string | Resource)

Sets the text of the **SaveButton** component.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| text | string \| [Resource](ts-types.md#resource) |Yes|Custom text.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the custom text setting does not take effect, and the **SaveButton** component retains the default style. For details, see [SaveButtonOptions](#savebuttonoptions).|

### iconSize<sup>20+</sup>

iconSize(size: Dimension | SizeOptions)

Sets the icon size of the **SaveButton** component.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| size | [Dimension](ts-types.md#dimension10) \| [SizeOptions](ts-types.md#sizeoptions) |Yes|Icon size. The default width and height are both 16 vp.<br>Percentage strings are not supported. If a percentage string is specified for a Dimension type parameter, the icon will be displayed with the default size. If either the **width** or **height** property of a SizeOptions type parameter is set to a percentage string, the icon will be displayed with a size of 0.<br>For the system icons provided by the **SaveButton** component:<br>- Dimension type: Width and height are both set to the specified value.<br>- SizeOptions type: If width and height are different, the smaller value is used for both. If only one value is specified, it applies to both dimensions.<br>For custom icons:<br>- Dimension type: Width and height are both set to the specified value.<br>- SizeOptions type: It is recommended that you set both width and height explicitly; if only one value is set, it applies to both dimensions.<br>- If the specified size's aspect ratio does not match the custom icon's original ratio, the icon displays in [ImageFit.Cover](ts-appendix-enums.md#imagefit) mode.|

### iconBorderRadius<sup>20+</sup>

iconBorderRadius(radius: Dimension | BorderRadiuses)

Sets the corner radius of the **SaveButton** component.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| radius | [Dimension](ts-types.md#dimension10) \| [BorderRadiuses](ts-types.md#borderradiuses9) |Yes|Corner radius of the **SaveButton** component. You can set the radius for each of the four corners individually.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the corner radius setting does not take effect.|

### stateEffect<sup>20+</sup>

stateEffect(enabled: boolean)

Sets the press effect of the **SaveButton** component.

**Required permissions**: ohos.permission.CUSTOMIZE_SAVE_BUTTON

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| enabled | boolean |Yes| Whether to enable the press effect. **true** to enable, **false** otherwise.<br>Default value: **true**.<br>If the application does not have the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission, the setting does not take effect.|

### userCancelEvent<sup>21+</sup>

userCancelEvent(enabled: boolean)

Sets the user authorization cancellation event for the **SaveButton** component.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                  | Mandatory| Description                  |
|------------|------|-------|---------|
| enabled | boolean | Yes| Whether to receive the user authorization cancellation event for the save button. The options are true (yes) and false (no).<br>Default value: **false**.<br>|

## Attributes

This component can only inherit the [universal attributes of security components](ts-securitycomponent-attributes.md).

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
        // Create a button with only an icon and background. If the alpha value of the most significant eight bits of the background color is less than 0x1a, the system forcibly adjusts the alpha value to 0xff.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, buttonType: ButtonType.Capsule })
          .backgroundColor(0x10007dff)
        // Create a button with an icon, text, and background. If the alpha value of the most significant eight bits of the background color is less than 0x1a, the system forcibly adjusts the alpha value to 0xff.
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
        // Configure the SaveButton component to receive the user authorization cancellation event.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .onClick((this.handleSaveButtonClick))
          .userCancelEvent(true)
      }.width('100%')
    }.height('100%')
  }
}
```



## Example 2

The application requires the ohos.permission.CUSTOMIZE_SAVE_BUTTON permission.

```ts
// xxx.ets
@Entry
@Component
struct SetIcon {
  build() {
    Row() {
      Column({ space: 10 }) {
        // Set icon to the resource type. The icon is displayed when permission is granted.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setIcon($r('app.media.startIcon'))
        // Set text to the string type. The text is displayed when permission is granted.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setText("SaveButton Set Text")
        // Set text to the resource type. The resource text is displayed when permission is granted.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setText($r('app.string.app_name'))
        // Set the icon size for the SaveButton component. The input parameter is of the Dimension type.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .iconSize(28)
        // Set the default icon size for the SaveButton component. The input parameter is of the SizeOptions type. It uses smaller value between width and height as the default icon size.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .iconSize({ width: 20, height: 40 })
        // Set the custom icon size for the SaveButton component. The input parameter is SizeOptions type. The image is displayed based on the configured width and height.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setIcon($r('app.media.startIcon'))
          .iconSize({ width: 30, height: 40 })
        // Set the custom icon size for the SaveButton component. The input parameter is of the SizeOptions type with a single value. The image is displayed based on the configured width and height.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .setIcon($r('app.media.startIcon'))
          .iconSize({ width: 40 })
        // Set the corner radius of the SaveButton component icon. The input parameter is of the Dimension type. All four corners use the input parameter value.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .backgroundColor(Color.Orange)
          .setIcon($r('app.media.background'))
          .iconSize(30)
          .iconBorderRadius(6)
        // Set the square icon corner radius greater than half side length to display as circle.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, buttonType: ButtonType.Circle })
          .backgroundColor(Color.Orange)
          .setIcon($r('app.media.foreground'))
          .iconSize(30)
          .iconBorderRadius(30)
          .padding(0)
        // Set iconBorderRadius to circle, background color to transparent, and add border.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, buttonType:ButtonType.Circle })
          .setIcon($r('app.media.background'))
          .backgroundColor(Color.Transparent)
          .iconSize(40)
          .iconBorderRadius(30)
          .borderWidth(1)
          .borderColor(Color.Black)
          .borderStyle(BorderStyle.Solid)
          .padding(10)
        // Set the border radius for the SaveButton component corners. The input parameter is of the BorderRadiuses type. Each corner uses the corresponding input parameter value. Unset corners remain square.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .backgroundColor(Color.Orange)
          .setIcon($r('app.media.background'))
          .iconSize(30)
          .iconBorderRadius({ topLeft: 10, topRight: 16, bottomRight: 20 })
        // Disable the pressed state effect for the SaveButton component.
        SaveButton({ icon: SaveIconStyle.FULL_FILLED, text: SaveDescription.DOWNLOAD })
          .stateEffect(false)
      }.width('100%')
    }.height('100%')
  }
}
```

