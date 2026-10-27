# EnableOptions（系统接口）

```TypeScript
interface EnableOptions
```

打开星闪时使用的选项。

**起始版本：** 26.1.0

<!--Device-manager-interface EnableOptions--><!--Device-manager-interface EnableOptions-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## autoConnPolicy

```TypeScript
autoConnPolicy?: AutoConnectPolicy
```

打开星闪时使用的自动连接策略。默认值为**AUTO_CONN_GENERAL**。

**类型：** [AutoConnectPolicy](arkts-connectivity-manager-autoconnectpolicy-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-EnableOptions-autoConnPolicy?: AutoConnectPolicy--><!--Device-EnableOptions-autoConnPolicy?: AutoConnectPolicy-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。
