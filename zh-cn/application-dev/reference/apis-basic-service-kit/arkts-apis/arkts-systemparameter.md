# @ohos.systemparameter

系统参数（SystemParameter）是为各系统服务提供的简单易用的键值对访问接口，各个系统服务可以定义系统参数来描述该服务的状态信息，或者通过系统参数来改变系统服务的行为。其基本操作原语为get和set，通过get可以查询系统参数的值，通过set可以修改系统参数的值。

详细的系统参数设计原理及定义可参考[系统参数](../../../../device-dev/subsystems/subsys-boot-init-sysparam.md)。
> **说明：**  
>  
> - 本模块接口从API version 9开始不再维护，建议使用新接口  
> [@ohos.systemParameterEnhance](arkts-systemparameterenhance.md)替代。  
>  
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
>  
> - 本模块接口为系统接口。  
>  
> - 由于系统参数都是各个系统服务的内部信息和控制参数，每个系统参数都有各自不同的DAC（Discretionary Access Control，自主访问控制）和MAC（Mandatory Access Control，强制访问控制）访问控制权限，三方应用不能使用此类接口。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [systemParameterEnhance:systemParameterEnhance](arkts-systemparameterenhance.md)

<!--Device-unnamed-declare namespace systemParameter--><!--Device-unnamed-declare namespace systemParameter-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [get](arkts-basicservices-systemparameter-get-f-sys.md#get) | 获取系统参数key对应的值，使用callback异步回调。 |
| [get](arkts-basicservices-systemparameter-get-f-sys.md#get-1) | 获取系统参数key对应的值，使用callback异步回调。 |
| [get](arkts-basicservices-systemparameter-get-f-sys.md#get-2) | 获取系统参数key对应的值，使用Promise异步回调。 |
| [getSync](arkts-basicservices-systemparameter-getsync-f-sys.md#getsync) | 获取系统参数key对应的值。 |
| [set](arkts-basicservices-systemparameter-set-f-sys.md#set) | 设置系统参数key对应的值，使用callback异步回调。 |
| [set](arkts-basicservices-systemparameter-set-f-sys.md#set-1) | 设置系统参数key对应的值，使用Promise异步回调。 |
| [setSync](arkts-basicservices-systemparameter-setsync-f-sys.md#setsync) | 设置系统参数key对应的值。 |
<!--DelEnd-->

