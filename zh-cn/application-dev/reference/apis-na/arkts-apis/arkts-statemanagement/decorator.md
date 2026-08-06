# stateManagement/decorator

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CustomEnvKey](decorator-customenvkey-c.md) | 自定义环境变量的Key的类型。 |
| [ReadonlyEnvKey](decorator-readonlyenvkey-c.md) | 只读系统环境变量Key类，用于@Env装饰器的字符串参数格式\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的key声明。 |
| [ReadonlySystemEnvKey](decorator-readonlysystemenvkey-c.md) | 只读系统环境变量Key，继承自[SystemEnvKey]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [SystemEnvKey](decorator-systemenvkey-c.md) | 系统环境变量Key的基类。 |
| [WritableEnvKey](decorator-writableenvkey-c.md) | 可写系统环境变量Key类，用于@Env装饰器的字符串参数格式\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的key声明。 |
| [WritableSystemEnvKey](decorator-writablesystemenvkey-c.md) | 可写系统环境变量Key，继承自[SystemEnvKey]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConsumeOptions](decorator-consumeoptions-i.md) | ConsumeOptions类 |
| [EnvOptions](decorator-envoptions-i.md) | Env创建可选参数 |
| [IComputedDecoratedVariable](decorator-icomputeddecoratedvariable-i.md) | 定义@Computed状态变量的接口 |
| [IConsumeDecoratedVariable](decorator-iconsumedecoratedvariable-i.md) | Define Consume decoration variable interface. |
| [IConsumerDecoratedVariable](decorator-iconsumerdecoratedvariable-i.md) | Consumer装饰的变量。 |
| [ICustomEnvDecoratedVariable](decorator-icustomenvdecoratedvariable-i.md) | 定义CustomEnv装饰变量接口。 |
| [IDecoratedImmutableVariable](decorator-idecoratedimmutablevariable-i.md) | 定义只读状态变量接口 |
| [IDecoratedMutableVariable](decorator-idecoratedmutablevariable-i.md) | 定义可读写状态变量接口 |
| [IDecoratedReadableVariable](decorator-idecoratedreadablevariable-i.md) | 定义状态变量接口 |
| [IDecoratedUpdatableVariable](decorator-idecoratedupdatablevariable-i.md) | Define decorated updatable variable interface. |
| [IDecoratedV1Variable](decorator-idecoratedv1variable-i.md) | Define V1 decorated variable interface. |
| [IDecoratedV2Variable](decorator-idecoratedv2variable-i.md) | V2装饰的变量。 |
| [IDecoratedVariable](decorator-idecoratedvariable-i.md) | 定义状态变量接口 |
| [IEnvDecoratedVariable](decorator-ienvdecoratedvariable-i.md) | Define Env decoration variable interface. |
| [IGlobalReusePoolVariable](decorator-iglobalreusepoolvariable-i.md) | 全局复用池句柄。 |
| [ILinkDecoratedVariable](decorator-ilinkdecoratedvariable-i.md) | Define Link decoration variable interface. |
| [ILocalDecoratedVariable](decorator-ilocaldecoratedvariable-i.md) | Local装饰的变量。 |
| [ILocalStorageLinkDecoratedVariable](decorator-ilocalstoragelinkdecoratedvariable-i.md) | Define LocalStorageLink decoration variable interface. |
| [ILocalStoragePropRefDecoratedVariable](decorator-ilocalstorageproprefdecoratedvariable-i.md) | Define LocalStoragePropRef decoration variable interface. |
| [IMonitor](decorator-imonitor-i.md) | 当监听的变量变化时，状态管理框架侧将回调开发者注册的函数，并传入变化信息。变化信息的类型即为IMonitor类型。 |
| [IMonitorDecoratedVariable](decorator-imonitordecoratedvariable-i.md) | Defines @Monitor decorated variable interface. |
| [IMonitorPathInfo](decorator-imonitorpathinfo-i.md) | Defines Monitor path with its accessor interface. |
| [IMonitorValue](decorator-imonitorvalue-i.md) |  |
| [IMutableKeyedStateMeta](decorator-imutablekeyedstatemeta-i.md) | Define mutable state meta interface with key. |
| [IMutableStateMeta](decorator-imutablestatemeta-i.md) | Define mutable state meta interface. |
| [IObjectLinkDecoratedVariable](decorator-iobjectlinkdecoratedvariable-i.md) | Define ObjectLink decoration variable interface. |
| [IObserve](decorator-iobserve-i.md) | Define IObserve interface. |
| [IObservedAnyProp](decorator-iobservedanyprop-i.md) | 定义IObservableAnyProp类型。 |
| [IObservedObject](decorator-iobservedobject-i.md) | Define IObservedObject interface. |
| [IParamDecoratedVariable](decorator-iparamdecoratedvariable-i.md) | Param装饰的变量。 |
| [IParamOnceDecoratedVariable](decorator-iparamoncedecoratedvariable-i.md) | Param和Once装饰的变量。 |
| [IPropRefDecoratedVariable](decorator-iproprefdecoratedvariable-i.md) | Define PropRef decoration variable interface. |
| [IProvideDecoratedVariable](decorator-iprovidedecoratedvariable-i.md) | Define Provide decoration variable interface. |
| [IProviderDecoratedVariable](decorator-iproviderdecoratedvariable-i.md) | Provider装饰的变量。 |
| [IStateDecoratedVariable](decorator-istatedecoratedvariable-i.md) | Define state decoration variable interface. |
| [IStateMgmtFactory](decorator-istatemgmtfactory-i.md) | Define IStateMgmtFactory interface. |
| [IStorageLinkDecoratedVariable](decorator-istoragelinkdecoratedvariable-i.md) | Define StorageLink decoration variable interface. |
| [IStoragePropRefDecoratedVariable](decorator-istorageproprefdecoratedvariable-i.md) | Define StoragePropRef decoration variable interface. |
| [ISubscribedWatches](decorator-isubscribedwatches-i.md) | Define ISubscribedWatches interface. |
| [IVariableOwner](decorator-ivariableowner-i.md) | 定义一个提供变量相关功能的自定义组件API。 |
| [IWatchSubscriberRegister](decorator-iwatchsubscriberregister-i.md) | Define IWatchSubscriberRegister interface. |
| [MakeMonitorOptions](decorator-makemonitoroptions-i.md) | 定义makeMonitor可选配置 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ComputedCallback](arkts-na-computedcallback-t.md) | Defines computed callback funciton |
| [LinkSourceType](arkts-na-linksourcetype-t.md) | Define Link source type. |
| [MonitorCallback](arkts-na-monitorcallback-t.md) | 触发监听时被调用的回调函数。 |
| [MonitorValueCallback](arkts-na-monitorvaluecallback-t.md) | 监听状态变量的回调类型。 |
| [RenderIdType](arkts-na-renderidtype-t.md) | Define int alias. |
| [WatchFuncType](arkts-na-watchfunctype-t.md) | Defines the callback that is called when state variable is change |
| [WatchIdType](arkts-na-watchidtype-t.md) | Define int alias. |

