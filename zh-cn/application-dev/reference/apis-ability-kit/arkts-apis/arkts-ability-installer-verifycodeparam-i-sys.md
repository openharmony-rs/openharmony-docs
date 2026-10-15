# VerifyCodeParam（系统接口）

```TypeScript
export interface VerifyCodeParam
```


> 从API version 11开始不再维护，应用的代码签名文件将集成到安装包中，不再需要该接口来指定安装包的代码签名文件。
> 应用程序代码签名文件信息。

**起始版本：** 10

**废弃版本：** 11

<!--Device-installer-export interface VerifyCodeParam--><!--Device-installer-export interface VerifyCodeParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## moduleName

```TypeScript
moduleName: string
```

应用程序模块名称。

**类型：** string

**起始版本：** 10

**废弃版本：** 11

<!--Device-VerifyCodeParam-moduleName: string--><!--Device-VerifyCodeParam-moduleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## signatureFilePath

```TypeScript
signatureFilePath: string
```

代码签名文件路径。

**类型：** string

**起始版本：** 10

**废弃版本：** 11

<!--Device-VerifyCodeParam-signatureFilePath: string--><!--Device-VerifyCodeParam-signatureFilePath: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
