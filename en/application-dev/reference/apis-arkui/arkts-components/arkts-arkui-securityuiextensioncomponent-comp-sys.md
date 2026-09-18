# SecurityUIExtensionComponent(System API) (System API)

**SecurityUIExtensionComponent** is used to embed the UI provided by another application on the current page. The displayed content runs in another process, and the current application does not participate in its layout and rendering.

It is typically used in modular development scenarios that require process isolation. Currently, **SecurityUIExtensionComponent** can only start **UIExtensionAbility** of the [PhotoPicker](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photopickercomponent-photopickercomponent-s.md) type.

## Child Components

None

## SecurityUIExtensionComponent

```TypeScript
SecurityUIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: SecurityUIExtensionOptions
  )
```

Creates a **SecurityUIExtensionComponent** component to embed and display the UI provided by a remote [UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | import('../api/@ohos.app.ability.Want').default | Yes | Ability information to load. The **UIExtensionAbilit**y to be started is determined by both **bundleName** and **abilityName**. In addition, the **ability.want.params.uiExtensionType** field must be specified in **parameters** to indicate the type of the **UIExtensionAbility**. Currently, only **sysPicker/photoPicker** is supported. |
| options | [SecurityUIExtensionOptions](arkts-arkui-securityuiextensionoptions-i-sys.md) | No | Options used to construct **SecurityUIExtensionComponent**. If this parameter is left empty, the default value is used for each field. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [SecurityUIExtensionOptions](arkts-arkui-securityuiextensionoptions-i-sys.md) | Defines the options to be passed when constructing **SecurityUIExtensionComponent**. |
| [SecurityUIExtensionProxy](arkts-arkui-securityuiextensionproxy-i-sys.md) | Implements a **SecurityUIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started ability through the connection established between the two parties. |
| [TerminationInfo](arkts-arkui-terminationinfo-i-sys.md) | Defines the result returned when the started **UIExtensionAbility** exits normally. |

### Enums

| Name | Description |
| --- | --- |
| [SecurityDpiFollowStrategy](arkts-arkui-securitydpifollowstrategy-e-sys.md) | Defines the enum of the resolution following strategy for **SecurityUIExtensionComponent**. |
