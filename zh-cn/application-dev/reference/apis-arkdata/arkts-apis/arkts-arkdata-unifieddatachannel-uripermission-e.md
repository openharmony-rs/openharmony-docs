# UriPermission

拖拽场景下的URI授权策略。
> **说明：**  
>  
> 此授权策略仅在拖拽场景下生效，其他场景不生效。  
> **实现机制：** 系统在拖拽数据传输时，根据UriPermission配置对目标URI进行临时授权。授权生命周期与拖拽会话绑定，拖拽完成后自动清理临时授权。接收方应用访问URI时，系统验证权限配置决定是否允许访问。  
> PERSIST权限会将临时授权转换为持久化授权。

支持不授权、读、写、持久化四种权限策略，可组合使用，仅以下组合生效：

- 仅使用NONE：不做任何文件授权。  
- 仅使用READ：仅做单次只读授权。  
- 仅使用WRITE：做单次读、写授权（写授权包含读授权）。  
- READ+WRITE：做单次读、写授权，与仅使用WRITE的授权效果相同。  
- READ+PERSIST：做持久化读授权。  
- WRITE+PERSIST：做持久化读写授权。  
- READ+WRITE+PERSIST：做持久化读写授权。

拖拽授权策略应用规则（按优先级从高到低）：

- 单个数据级别：FileUri、HTML两个统一数据结构（UDS）以及File、Image、Video、Audio、Folder、HTML六个统一数据内容（UDC）数据结构支持配置授权策略参数，仅对单个record单次生效，优先级最高。  
- UnifiedData级别：UnifiedDataProperties中提供的授权参数对单次拖拽有效。若某个数据中配置了授权策略，则优先按照该数据的配置进行，优先级次之。  
- 默认级别：若单个数据和UnifiedDataProperties均未配置授权策略，则按照拖拽默认逻辑进行代理授权。默认逻辑如下：

- FileUri类型数据（FileUri UDS或File、Image、Video、Audio、Folder五个UDC类型）：拖拽场景下默认授权为READ+WRITE+PERSIST（读+写+持久化授权）。  
- HTML类型数据，仅针对HTML文本中img标签下的uri做读授权。

**起始版本：** 26.0.0

<!--Device-unifiedDataChannel-export const enum UriPermission--><!--Device-unifiedDataChannel-export const enum UriPermission-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## NONE

```TypeScript
NONE = 0
```

表示未授予任何权限。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-UriPermission-NONE = 0--><!--Device-UriPermission-NONE = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## READ

```TypeScript
READ = 1
```

表示读取或查看数据的权限。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-UriPermission-READ = 1--><!--Device-UriPermission-READ = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WRITE

```TypeScript
WRITE = 2
```

表示修改数据的权限（包含READ）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-UriPermission-WRITE = 2--><!--Device-UriPermission-WRITE = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PERSIST

```TypeScript
PERSIST = 3
```

表示持久化文件的权限。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-UriPermission-PERSIST = 3--><!--Device-UriPermission-PERSIST = 3-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

