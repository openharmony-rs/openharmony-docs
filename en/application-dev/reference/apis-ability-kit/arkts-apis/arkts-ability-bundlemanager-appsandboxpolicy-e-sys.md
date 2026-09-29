# AppSandboxPolicy (System API)

```TypeScript
export enum AppSandboxPolicy
```

App sandbox policy for dual-mode (2in1/tablet) scenarios.

**Since:** 26.0.1

<!--Device-bundleManager-export enum AppSandboxPolicy--><!--Device-bundleManager-export enum AppSandboxPolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## SHARED_SANDBOX

```TypeScript
SHARED_SANDBOX = 0
```

Application sharing sandbox in the two modes.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppSandboxPolicy-SHARED_SANDBOX = 0--><!--Device-AppSandboxPolicy-SHARED_SANDBOX = 0-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ISOLATED_SANDBOX

```TypeScript
ISOLATED_SANDBOX = 1
```

The application isolation sandbox for the two modes, with each application having its own independent sandbox.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AppSandboxPolicy-ISOLATED_SANDBOX = 1--><!--Device-AppSandboxPolicy-ISOLATED_SANDBOX = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
