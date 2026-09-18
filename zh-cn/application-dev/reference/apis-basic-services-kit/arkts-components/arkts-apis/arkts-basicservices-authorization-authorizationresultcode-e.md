# AuthorizationResultCode

枚举授权结果码。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Account.OsAccount

## AUTHORIZATION_GRANTED

```TypeScript
AUTHORIZATION_GRANTED = 0
```

授权成功。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

## AUTHORIZATION_CANCELED

```TypeScript
AUTHORIZATION_CANCELED = 12300301
```

该授权已被用户或用户代理取消。

可能原因：用户明确关闭（取消）了授权弹窗（例如：点击“取消”按钮，或点击窗口关闭操作）。

> **说明：** 
> 建议的解决方案：
> 1. 将此行为视为符合预期的用户级流程中止，而非系统故障。
> 2. 实现非侵入式的用户体验（UX）通知或状态回退策略（例如：平滑地回滚 UI 界面，并将状态标签更新为“授权已取消”或“操作已关闭”）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

## AUTHORIZATION_DENIED

```TypeScript
AUTHORIZATION_DENIED = 12300303
```

授权被系统策略拒绝。

未满足该特权所对应的授权策略。例如：该特权要求调用方必须持有指定的应用权限，且必须在管理员操作系统账户会话下运行。

> **说明：** 
> 建议的解决方案：
> 1. 检查目标特权的授权策略配置。
> 2. 采取适当的降级处理或平滑降级策略（例如：引导用户切换到管理员环境，或提示该功能暂时不可用）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

## AUTHORIZATION_NOT_SUPPORTED

```TypeScript
AUTHORIZATION_NOT_SUPPORTED = 12300305
```

不支持该授权请求。这表明所请求的目标特权在当前系统版本中完全未注册或缺失，其关联功能通常亦不受支持。

可能原因：包含前沿系统特性的新版应用，正运行在未升级的旧版宿主操作系统上，而该旧版系统完全没有这个新引入特权的任何定义。

> **说明：** 
> 建议的解决方案：应当采取降级处理（例如：提示该功能不可用，或直接跳过此操作）。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount
