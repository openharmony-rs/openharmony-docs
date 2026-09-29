# GattPermissions

```TypeScript
interface GattPermissions
```

Describes the permission of a att attribute item.

**Since:** 20

<!--Device-ble-interface GattPermissions--><!--Device-ble-interface GattPermissions-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## read

```TypeScript
read?: boolean
```

The attribute field has the read permission.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-read?: boolean--><!--Device-GattPermissions-read?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## readEncrypted

```TypeScript
readEncrypted?: boolean
```

The attribute field has the encrypted read permission.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-readEncrypted?: boolean--><!--Device-GattPermissions-readEncrypted?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## readEncryptedMitm

```TypeScript
readEncryptedMitm?: boolean
```

The attribute field has the read permission for encryption authentication.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-readEncryptedMitm?: boolean--><!--Device-GattPermissions-readEncryptedMitm?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## write

```TypeScript
write?: boolean
```

The attribute field has the write permission.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-write?: boolean--><!--Device-GattPermissions-write?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## writeEncrypted

```TypeScript
writeEncrypted?: boolean
```

The attribute field has the encrypted write permission.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-writeEncrypted?: boolean--><!--Device-GattPermissions-writeEncrypted?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## writeEncryptedMitm

```TypeScript
writeEncryptedMitm?: boolean
```

The attribute field has the write permission for encryption authentication.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-writeEncryptedMitm?: boolean--><!--Device-GattPermissions-writeEncryptedMitm?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## writeSigned

```TypeScript
writeSigned?: boolean
```

The attribute field has the signed write permission.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-writeSigned?: boolean--><!--Device-GattPermissions-writeSigned?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## writeSignedMitm

```TypeScript
writeSignedMitm?: boolean
```

The attribute field has the write permission for signature authentication.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattPermissions-writeSignedMitm?: boolean--><!--Device-GattPermissions-writeSignedMitm?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
