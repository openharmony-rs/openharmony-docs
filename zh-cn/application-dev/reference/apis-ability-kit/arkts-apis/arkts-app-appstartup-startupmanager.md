# @ohos.app.appstartup.startupManager

本模块提供[应用启动框架](docroot://application-models/app-startup.md)管理启动任务的能力，只能在主线程调用。

> **说明：**  
>  
> 本模块从API version 18开始支持so预加载。

**起始版本：** 12

<!--Device-unnamed-declare namespace startupManager--><!--Device-unnamed-declare namespace startupManager-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## 导入模块

```TypeScript
import { startupManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getStartupTaskResult](arkts-ability-startupmanager-getstartuptaskresult-f.md#getstartuptaskresult) | 获取指定启动任务或so预加载任务的执行结果。 |
| [isStartupTaskInitialized](arkts-ability-startupmanager-isstartuptaskinitialized-f.md#isstartuptaskinitialized) | 获取指定启动任务或so预加载任务是否已初始化。 |
| [removeAllStartupTaskResults](arkts-ability-startupmanager-removeallstartuptaskresults-f.md#removeallstartuptaskresults) | 删除所有启动任务结果。如果存在so预加载任务，则将对应so文件置为未加载状态。对于缓存中已加载的so文件，不会被移除。 |
| [removeStartupTaskResult](arkts-ability-startupmanager-removestartuptaskresult-f.md#removestartuptaskresult) | 删除指定启动任务或so预加载任务的初始化结果。  - 输入为启动任务名时，删除指定启动任务的初始化结果。  - 输入为so文件时，将该so文件置为未加载，缓存中已加载的so文件不会被移除。 |
| [run](arkts-ability-startupmanager-run-f.md#run) | 执行启动框架启动任务或加载so文件。 |
| [run](arkts-ability-startupmanager-run-f.md#run-1) | 执行启动框架启动任务或加载so文件。支持指定[AbilityStageContext](arkts-ability-abilitystagecontext-c.md)用于启动任务的加载。使用Promise异步回调。 |

