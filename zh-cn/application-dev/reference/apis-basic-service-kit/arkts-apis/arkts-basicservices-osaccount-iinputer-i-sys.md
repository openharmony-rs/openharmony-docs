# IInputer（系统接口）

凭据输入器回调。

**起始版本：** 8

<!--Device-osAccount-interface IInputer--><!--Device-osAccount-interface IInputer-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## onGetData

```TypeScript
onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void
```

通知调用者获取数据的回调函数。

**类型：** (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) =&gt; void

**起始版本：** 8

<!--Device-IInputer-onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void--><!--Device-IInputer-onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

