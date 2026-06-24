# Context

Context是Stage模型的上下文基类，主要用于访问特定应用程序的资源，以及执行应用级操作的回调。

**继承/实现关系：** Context extends [BaseContext](arkts-ability-basecontext-c.md#BaseContext)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## createBundleContext

```TypeScript
createBundleContext(bundleName: string): Context
```

根据Bundle名称创建安装包的上下文。

> **说明：**
>
> - stage模型多module的情况下可能发生资源id冲突的情况，建议使用
> [application.createModuleContext](arkts-ability-application-createmodulecontext-f.md#createModuleContext-1)替代。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [createBundleContext](arkts-ability-application-createbundlecontext-f-sys.md#createBundleContext-1)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Context | 安装包的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

## createModuleContext

```TypeScript
createModuleContext(bundleName: string, moduleName: string): Context
```

根据Bundle名称和模块名称创建上下文。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [createModuleContext](arkts-ability-application-createmodulecontext-f.md#createModuleContext-1)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |
| moduleName | string | 是 | 模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Context | 模块的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

## createModuleResourceManager

```TypeScript
createModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager
```

为指定Module创建资源管理对象。

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |
| moduleName | string | 是 | 模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| resmgr.ResourceManager | Object for resource management. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |

## createSystemHspModuleResourceManager

```TypeScript
createSystemHspModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager
```

该接口用于OEM厂商预置的[系统级HSP](../../../../quick-start/application-package-glossary.md#系统级hsp)创建自己的
[ResourceManager](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |
| moduleName | string | 是 | 模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| resmgr.ResourceManager | Returns the system HSP module resource manager. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16400001](../../errorcode-universal.md#16400001-The) | The input bundleName is not a system HSP. |

