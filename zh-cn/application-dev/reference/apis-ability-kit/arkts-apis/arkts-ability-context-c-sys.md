# Context

Context是Stage模型的上下文基类，主要用于访问特定应用程序的资源，以及执行应用级操作的回调。

**继承/实现关系：** Context extends [BaseContext](arkts-ability-basecontext-c.md)

**起始版本：** 9

<!--Device-unnamed-declare class Context extends BaseContext--><!--Device-unnamed-declare class Context extends BaseContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## createBundleContext

```TypeScript
createBundleContext(bundleName: string): Context
```

根据Bundle名称创建安装包的上下文。

> **说明：**  
>  
> - stage模型多module的情况下可能发生资源id冲突的情况，建议使用  
> [application.createModuleContext](arkts-ability-application-createmodulecontext-f.md#createmodulecontext-1)替代。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [createBundleContext](arkts-ability-application-createbundlecontext-f-sys.md#createbundlecontext-1)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Context-createBundleContext(bundleName: string): Context--><!--Device-Context-createBundleContext(bundleName: string): Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 安装包的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

## createModuleContext

```TypeScript
createModuleContext(bundleName: string, moduleName: string): Context
```

根据Bundle名称和模块名称创建上下文。

**起始版本：** 9

**废弃版本：** 12

**替代接口：** [createModuleContext](arkts-ability-application-createmodulecontext-f.md#createmodulecontext-1)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Context-createModuleContext(bundleName: string, moduleName: string): Context--><!--Device-Context-createModuleContext(bundleName: string, moduleName: string): Context-End-->

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
| [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 模块的上下文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

## createModuleResourceManager

```TypeScript
createModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager
```

为指定Module创建资源管理对象。

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Context-createModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager--><!--Device-Context-createModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager-End-->

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
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |

## createSystemHspModuleResourceManager

```TypeScript
createSystemHspModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager
```

该接口用于OEM厂商预置的[系统级HSP](../../../../quick-start/application-package-glossary.md#系统级hsp)创建自己的[ResourceManager](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Context-createSystemHspModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager--><!--Device-Context-createSystemHspModuleResourceManager(bundleName: string, moduleName: string): resmgr.ResourceManager-End-->

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
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [16400001](../errorcode-ability.md#16400001-目标应用类型不是系统级hsp) | The input bundleName is not a system HSP. |

