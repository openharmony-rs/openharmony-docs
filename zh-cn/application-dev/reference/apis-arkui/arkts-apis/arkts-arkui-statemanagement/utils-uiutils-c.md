# UIUtils

UIUtils是状态管理提供的工具，用于处理可观察数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class UIUtils--><!--Device-unnamed-export declare class UIUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addMonitor

```TypeScript
static addMonitor(valueCallback: MonitorValueCallback | MonitorValueCallback[], 
    monitorCallback: MonitorCallback, options?: MonitorOptions): IMonitorDecoratedVariable
```

动态地为状态变量注册监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static addMonitor(valueCallback: MonitorValueCallback | MonitorValueCallback[],     monitorCallback: MonitorCallback, options?: MonitorOptions): IMonitorDecoratedVariable--><!--Device-UIUtils-static addMonitor(valueCallback: MonitorValueCallback | MonitorValueCallback[],     monitorCallback: MonitorCallback, options?: MonitorOptions): IMonitorDecoratedVariable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| valueCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| MonitorValueCallback[] | 是 | 返回被监听状态变量的箭头函数或箭头函数数组。 |
| monitorCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 触发监听时调用的回调函数。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置函数的行为，默认行行为详见[MonitorOptions]{ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 指代监听关系的句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [130000](../../errorcode-stateManagement.md#130000-addmonitorclearmonitor非法目标对象) | options.owner is not ComponentV2 struct. |

## addMonitor

```TypeScript
static addMonitor(valueInfo: MonitorValueInfo | MonitorValueInfo[], 
    monitorCallback: MonitorCallback, options?: MonitorBaseOptions): IMonitorDecoratedVariable
```

动态地为状态变量注册监听。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static addMonitor(valueInfo: MonitorValueInfo | MonitorValueInfo[],     monitorCallback: MonitorCallback, options?: MonitorBaseOptions): IMonitorDecoratedVariable--><!--Device-UIUtils-static addMonitor(valueInfo: MonitorValueInfo | MonitorValueInfo[],     monitorCallback: MonitorCallback, options?: MonitorBaseOptions): IMonitorDecoratedVariable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| valueInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| MonitorValueInfo[] | 是 | 监听变量的信息或其数组。 |
| monitorCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 触发监听时调用的回调函数。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置函数的行为，默认行为详见[MonitorBaseOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 指代监听关系的句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [130000](../../errorcode-stateManagement.md#130000-addmonitorclearmonitor非法目标对象) | options.owner is not ComponentV2 struct. |

## canBeObserved

```TypeScript
static canBeObserved<T extends object>(source: T): ObservedResult
```

判断数据对象是否为可观察对象，并返回观察结果。详见 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static canBeObserved<T extends object>(source: T): ObservedResult--><!--Device-UIUtils-static canBeObserved<T extends object>(source: T): ObservedResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 输入一个数据对象，判断其是否可被观察。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_具体使用规则，详见\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回对象是否可被观察的结果。 |

## clearMonitor

```TypeScript
static clearMonitor(monitor: IMonitorDecoratedVariable): void
```

动态地为状态变量解绑监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static clearMonitor(monitor: IMonitorDecoratedVariable): void--><!--Device-UIUtils-static clearMonitor(monitor: IMonitorDecoratedVariable): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitor | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指代监听关系的句柄。 |

## getCustomComponentContext

```TypeScript
static getCustomComponentContext<T extends IVariableOwner>(customComponent: T): CustomComponentContext
```

获取自定义组件的上下文信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static getCustomComponentContext<T extends IVariableOwner>(customComponent: T): CustomComponentContext--><!--Device-UIUtils-static getCustomComponentContext<T extends IVariableOwner>(customComponent: T): CustomComponentContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customComponent | T | 是 | 自定义组件对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 传入自定义组件的上下文信息。 |

## getLifecycle

```TypeScript
static getLifecycle<T extends IVariableOwner>(customComponent: T): CustomComponentLifecycle
```

getLifecycle用于获取[自定义组件的生命周期]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_实例。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static getLifecycle<T extends IVariableOwner>(customComponent: T): CustomComponentLifecycle--><!--Device-UIUtils-static getLifecycle<T extends IVariableOwner>(customComponent: T): CustomComponentLifecycle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customComponent | T | 是 | 自定义组件实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 自定义组件的生命周期实例。 |

## getTarget

```TypeScript
static getTarget<T extends object>(source: T): T
```

获取状态管理框架包装前的原始对象。支持built-in类型（Array、Map、Set、Date）以及interface字面量。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static getTarget<T extends object>(source: T): T--><!--Device-UIUtils-static getTarget<T extends object>(source: T): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 状态管理框架包装的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 状态管理框架包装前的原始对象。 |

## makeBinding

```TypeScript
static makeBinding<T>(getter: GetterCallback<T>): Binding<T>
```

创建只读的单向数据绑定实例，用于在@Builder函数中为参数类型为Binding的参数提供实参。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static makeBinding<T>(getter: GetterCallback<T>): Binding<T>--><!--Device-UIUtils-static makeBinding<T>(getter: GetterCallback<T>): Binding<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| getter | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 获取值的回调函数，每次访问值时重新执行以获取最新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 包含一个value属性，用于获取当前绑定的值，且只能读取，不能修改。 |

## makeBinding

```TypeScript
static makeBinding<T>(getter: GetterCallback<T>, setter: SetterCallback<T>): MutableBinding<T>
```

创建双向数据绑定实例，用于构建@Builder函数中类型为MutableBinding的参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static makeBinding<T>(getter: GetterCallback<T>, setter: SetterCallback<T>): MutableBinding<T>--><!--Device-UIUtils-static makeBinding<T>(getter: GetterCallback<T>, setter: SetterCallback<T>): MutableBinding<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| getter | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 获取值的回调函数，每次访问值时重新执行。 |
| setter | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 定义如何更新值，当.value被修改时调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 包含一个value属性，支持读取和修改数据，设置值时检查类型是否匹配泛型\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

## makeObserved

```TypeScript
static makeObserved<T extends object | null | undefined>(source: T): T
```

将不可观察数据转化为可观察数据。支持built-in类型（Array、Map、Set、Date）以及interface字面量。 > **说明：** > 默认情况下，返回对象支持深度观察，可观察嵌套属性变化。 > 如果传入了undefined或null，则直接返回传入值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static makeObserved<T extends object | null | undefined>(source: T): T--><!--Device-UIUtils-static makeObserved<T extends object | null | undefined>(source: T): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 数据源对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 可观察的数据对象。 |

## makeObserved

```TypeScript
static makeObserved<T extends object | null | undefined>(source: T, allowDeep: boolean): T
```

将不可观察数据转化为可观察数据，并通过\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_控制观察深度。支持built-in类型（Array、Map、Set、Date）以及interface字面量。 > **说明：** > 如果传入了undefined或null，则直接返回传入值。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIUtils-static makeObserved<T extends object | null | undefined>(source: T, allowDeep: boolean): T--><!--Device-UIUtils-static makeObserved<T extends object | null | undefined>(source: T, allowDeep: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | T | 是 | 数据源对象。 |
| allowDeep | boolean | 是 | 是否深度观察。传入\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时为深度观察；传入\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时仅观察第一层属性变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 可观察的数据对象。 |

