# SignatureInfo

```TypeScript
export interface SignatureInfo
```

Describes the signature information of the app package, which can identify the app source, ensure app integrity, and be used for app security verification and identification.

**Since:** 9

<!--Device-unnamed-export interface SignatureInfo--><!--Device-unnamed-export interface SignatureInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## validity

```TypeScript
readonly validity?: Validity
```

Validity period in the signing certificate file.

**Type:** [Validity](arkts-ability-appprovisioninfo-validity-i-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SignatureInfo-readonly validity?: Validity--><!--Device-SignatureInfo-readonly validity?: Validity-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
