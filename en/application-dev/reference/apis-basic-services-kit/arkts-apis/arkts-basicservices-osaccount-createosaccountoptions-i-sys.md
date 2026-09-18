# CreateOsAccountOptions (System API)

Represents the optional parameter used to create an OS account.

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## allowedPreinstalledBundles

```TypeScript
allowedPreinstalledBundles?: Array<string>
```

Trustlist of the preinstalled applications, which can be installed on the device. The default value is **std::nullopt**.

**Type:** Array&lt;string&gt;

**Since:** 19

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## disallowedPreinstalledBundles

```TypeScript
disallowedPreinstalledBundles?: Array<string>
```

Forbidden list of the preinstalled applications, which cannot be installed on the device. The value is left empty by default.

**Type:** Array&lt;string&gt;

**Since:** 19

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## shortName

```TypeScript
shortName: string
```

Short name of the account (used as the name of the personal folder).

**The short name cannot**:

1. Contain any of the following characters: &lt; &gt;| : " * ? / \
2. Contain any of the following: . or ..
3. Exceed 255 characters.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## token

```TypeScript
token?: Uint8Array
```

Token obtained from the authentication management API. The value is left empty by default.

**Type:** Uint8Array

**Since:** 24

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
