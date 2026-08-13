# IInputer（系统接口）

凭据输入器回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-osAccount-interface IInputer--><!--Device-osAccount-interface IInputer-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## onGetData

```TypeScript
onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void
```

通知调用者获取数据的回调函数。

**类型：** (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-IInputer-onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void--><!--Device-IInputer-onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

