# PathSharedData

```TypeScript
interface PathSharedData
```

共享路径数据。

**起始版本：** 26.1.0

<!--Device-networkManager-interface PathSharedData--><!--Device-networkManager-interface PathSharedData-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## shareLimit

```TypeScript
shareLimit: number
```

允许访问该共享资源的最大用户数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathSharedData-shareLimit: number--><!--Device-PathSharedData-shareLimit: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## shareName

```TypeScript
shareName: string
```

共享路径名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathSharedData-shareName: string--><!--Device-PathSharedData-shareName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## shareUri

```TypeScript
shareUri: string
```

共享路径的URI。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathSharedData-shareUri: string--><!--Device-PathSharedData-shareUri: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## userPathInfoList

```TypeScript
userPathInfoList: Array<UserPathInfo>
```

用户路径信息列表，用于权限管理。

**类型：** Array&lt;[UserPathInfo](arkts-mdm-networkmanager-userpathinfo-i.md)&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathSharedData-userPathInfoList: Array<UserPathInfo>--><!--Device-PathSharedData-userPathInfoList: Array<UserPathInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
