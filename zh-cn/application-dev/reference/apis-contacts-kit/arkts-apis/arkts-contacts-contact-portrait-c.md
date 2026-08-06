# Portrait

联系人的头像类。 > **说明：** > > 从API version 22开始，支持通过uri和[PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_格式设置联系人头像资源(暂不支持通过 > [addContactViaUI]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 > [saveToExistingContactViaUI]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口设置)。 > > uri为可访问的联系人头像文件地址，[PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_为通过联系人头像资源生成的 > [PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_对象。 > > 从API version 22开始，支持通过uri格式读取联系人头像资源，该格式仅支持以 > [fs.open]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_方式打开，无法直接在Image组件内显示，需读取后转换为 > [PixelMap]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_格式显示。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-contact-class Portrait--><!--Device-contact-class Portrait-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## photo

```TypeScript
photo?: image.PixelMap
```

PixelMap格式的联系人头像。

**类型：** image.PixelMap

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Portrait-photo?: image.PixelMap--><!--Device-Portrait-photo?: image.PixelMap-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## uri

```TypeScript
uri: string
```

uri格式联系人头像。

**类型：** string

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Portrait-uri: string--><!--Device-Portrait-uri: string-End-->

**系统能力：** SystemCapability.Applications.ContactsData

