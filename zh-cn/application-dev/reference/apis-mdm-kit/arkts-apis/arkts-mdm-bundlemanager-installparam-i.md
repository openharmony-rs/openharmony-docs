# InstallParam

应用包安装需指定的参数信息。

**起始版本：** 12

<!--Device-bundleManager-interface InstallParam--><!--Device-bundleManager-interface InstallParam-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## installFlag

```TypeScript
installFlag?: number
```

安装标志。枚举值：0：应用初次安装，1：应用覆盖安装，2：应用免安装，默认值为应用初次安装。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallParam-installFlag?: number--><!--Device-InstallParam-installFlag?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## parameters

```TypeScript
parameters?: Record<string, string>
```

扩展参数，默认值为空。key取值支持"ohos.bms.param.enterpriseForAllUser"，若对应的value值为"true"，表示为所有用户安装应用。

**类型：** Record<string, string>

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallParam-parameters?: Record<string, string>--><!--Device-InstallParam-parameters?: Record<string, string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## userId

```TypeScript
userId?: number
```

指示用户ID，默认值：调用方所在用户，取值范围：大于等于0。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallParam-userId?: number--><!--Device-InstallParam-userId?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

