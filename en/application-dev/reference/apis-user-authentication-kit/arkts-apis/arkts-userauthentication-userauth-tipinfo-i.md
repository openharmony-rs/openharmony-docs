# TipInfo

```TypeScript
interface TipInfo
```

Represents the tip information displayed during the authentication, which is used to provide feedback during the authentication process.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [AuthTipInfo](arkts-userauthentication-userauth-authtipinfo-i.md)

<!--Device-userAuth-interface TipInfo--><!--Device-userAuth-interface TipInfo-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## module

```TypeScript
module: number
```

ID of the module that sends the tip information.

**Type:** number

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [tipType](arkts-userauthentication-userauth-authtipinfo-i.md#tiptype)

<!--Device-TipInfo-module: number--><!--Device-TipInfo-module: number-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## tip

```TypeScript
tip: number
```

Tip to be given during the authentication process.

**Type:** number

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [tipCode](arkts-userauthentication-userauth-authtipinfo-i.md#tipcode)

<!--Device-TipInfo-tip: number--><!--Device-TipInfo-tip: number-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
