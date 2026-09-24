# AppSandboxPolicy（系统接口）

```TypeScript
export enum AppSandboxPolicy
```

双模式（2in1/平板）场景下的应用沙箱策略。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## SHARED_SANDBOX

```TypeScript
SHARED_SANDBOX = 0
```

共享沙箱（默认）

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## ISOLATED_SANDBOX

```TypeScript
ISOLATED_SANDBOX = 1
```

隔离沙箱

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
