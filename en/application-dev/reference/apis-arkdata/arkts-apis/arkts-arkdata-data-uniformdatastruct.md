# @ohos.data.uniformDataStruct(Uniform Data Structs)

As a part of the Unified Data Management Framework (UDMF), the **uniformDataStruct** module provides data structs corresponding to certain [UniformDataTypes](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md) for service scenarios of many-to-many data sharing across applications. It helps simplify data interaction and reduce the data type adaptation workload.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace uniformDataStruct--><!--Device-unnamed-declare namespace uniformDataStruct-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ContentForm](arkts-arkdata-uniformdatastruct-contentform-i.md) | Defines the content card typed data, which is used to share content card information across applications. Typical usage scenarios include sharing article cards in news applications, sharing product cards in e-commerce applications, and sharing content previews in social applications. |
| [FileUri](arkts-arkdata-uniformdatastruct-fileuri-i.md) | Defines the file URI typed data, which is used to describe the URI address information of a file. After a FileUri object is created, it can be used in scenarios such as file drag-and-drop and file sharing, support controlling file access permissions through uriAuthorizationPolicies, and implement cross-application file data transfer and permission management. |
| [Form](arkts-arkdata-uniformdatastruct-form-i.md) | Represents the system-defined card typed data, which is used to share card information across applications. Typical usage scenarios include card drag-and-drop sharing, cross-application transfer of card content, and data sharing of home screen widgets. |
| [HTML](arkts-arkdata-uniformdatastruct-html-i.md) | Defines the HTML typed data, which is used to describe HyperText Markup Language data. After an HTML object is created, it can be used to transfer rich text content in scenarios such as drag-and-drop and copy-paste, support cross-application HTML format data interaction, and control the URI authorization policy through **uriAuthorizationPolicies**. |
| [Hyperlink](arkts-arkdata-uniformdatastruct-hyperlink-i.md) | Defines the hyperlink typed data, which is used to describe and manage hyperlink information. After a Hyperlink object is created, it can be used in scenarios such as drag-and-drop and sharing to implement cross-application hyperlink data transfer and redirection. |
| [OpenHarmonyAppItem](arkts-arkdata-uniformdatastruct-openharmonyappitem-i.md) | Represents the system-defined desktop icon typed data, which is used to share desktop icon information across applications. Typical usage scenarios include dragging icons on the home screen launcher, sharing application icons in the app store, or creating shortcuts. |
| [PixelMap](arkts-arkdata-uniformdatastruct-pixelmap-i.md) | Represents the system-defined pixel map typed data, used to describe image pixel data. After a PixelMap object is created, it can be used in scenarios such as image drag-and-drop and image sharing to implement cross-application image data transfer. |
| [PlainText](arkts-arkdata-uniformdatastruct-plaintext-i.md) | Represents data of the plain text type. |
