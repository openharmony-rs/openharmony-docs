# GeneralName

表示X.509 GeneralName，定义在RFC 5280中，可出现在Subject Alternative Name等扩展中。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-cert-interface GeneralName--><!--Device-cert-interface GeneralName-End-->

**系统能力：** SystemCapability.Security.Cert

## name

```TypeScript
name?: Uint8Array
```

指定GeneralName的DER编码值。

**类型：** Uint8Array

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GeneralName-name?: Uint8Array--><!--Device-GeneralName-name?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## type

```TypeScript
type: GeneralNameType
```

GeneralName类型。

**类型：** GeneralNameType

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GeneralName-type: GeneralNameType--><!--Device-GeneralName-type: GeneralNameType-End-->

**系统能力：** SystemCapability.Security.Cert

