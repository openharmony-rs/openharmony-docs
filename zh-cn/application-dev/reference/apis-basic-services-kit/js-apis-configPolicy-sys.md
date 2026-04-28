# @ohos.configPolicy (配置策略)(系统接口)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Customization-->
<!--Owner: @liule_123-->
<!--Designer: @sunshine_liu-->
<!--Tester: @lpw_work-->
<!--Adviser: @fang-jinxu-->

配置策略提供按系统预定义的定制配置层级获取对应目录和文件路径的能力。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口均为系统接口。

## 导入模块

```ts
import { configPolicy } from '@kit.BasicServicesKit';
```

## getOneCfgFile

getOneCfgFile(relPath: string, callback: AsyncCallback&lt;string&gt;): void

获取指定文件名优先级最高的配置文件路径。使用callback异步回调。

例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml，最终返回优先级最高的是：/sys_pod/etc/config.xml。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                         | 必填 | 说明                                  |
| -------- | --------------------------- | ---- | ------------------------------------ |
| relPath  | string                      | 是   | 配置文件名。                           |
| callback | AsyncCallback&lt;string&gt; | 是   | 回调函数。当获取配置文件路径成功，error为undefined，value为获取到的优先级最高的配置文件路径；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getOneCfgFile(relpath, (error: BusinessError, value: string) => {
        if (error == null) {
          console.info('value is ' + value);
        } else {
          console.error('error: ' + error.code + ', ' + error.message);
        }
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getOneCfgFile(relpath, (error: BusinessError | null, value: string | undefined) => {
        if (error == null) {
          console.info('value is ' + value);
        } else {
          console.error('error: ' + error.code + ', ' + error.message);
        }
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getOneCfgFile

getOneCfgFile(relPath: string): Promise&lt;string&gt;

获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明       |
| ------- | ------ | ---- | ---------- |
| relPath | string | 是   | 配置文件名。 |

**返回值：**

| 类型                   | 说明                     |
| ---------------------- | ------------------------ |
| Promise&lt;string&gt;  | Promise对象，返回优先级最高的配置文件路径。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getOneCfgFile(relpath).then((value: string) => {
        console.info('value is ' + value);
      }).catch((error: BusinessError) => {
        console.error('getOneCfgFile promise error: ' + error.code + ', ' + error.message);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getOneCfgFile(relpath).then((value: string) => {
        console.info('value is ' + value);
      }).catch((error: Error) => {
        console.error('getOneCfgFile promise error: ' + error);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgFiles

getCfgFiles(relPath: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

获取指定文件名的所有文件列表，按优先级从低到高。使用callback异步回调。
例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                     | 必填 | 说明                       |
| -------- | ---------------------------------------- | ---- | -------------------------- |
| relPath  | string                                   | 是   | 配置文件名。                 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是   | 回调函数。当获取文件列表成功，error为undefined，value为获取到的文件列表；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      configPolicy.getCfgFiles('etc/config.xml', (error: BusinessError, value: Array<string>) => {
        if (error == null) {
          console.info('value is ' + value);
        } else {
          console.error('error: ' + error.code + ', ' + error.message);
        }
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      configPolicy.getCfgFiles('etc/config.xml', (error: BusinessError | null, value: Array<string> | undefined) => {
        if (error == null) {
          console.info('value is ' + value);
        } else {
          console.error('error: ' + error.code + ', ' + error.message);
        }
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgFiles

getCfgFiles(relPath: string): Promise&lt;Array&lt;string&gt;&gt;

获取指定文件名的所有文件列表，按优先级从低到高。使用Promise异步回调。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明       |
| ------- | ------ | ---- | ---------- |
| relPath | string | 是   | 配置文件名。 |

**返回值：**

| 类型                               | 说明     |
| ---------------------------------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回文件列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getCfgFiles(relpath).then((value: Array<string>) => {
        console.info('value is ' + value);
      }).catch((error: BusinessError) => {
        console.error('getCfgFiles promise error: ' + error.code + ', ' + error.message);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getCfgFiles(relpath).then((value: Array<string>) => {
        console.info('value is ' + value);
      }).catch((error: Error) => {
        console.error('getCfgFiles promise error: ' + error);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgDirList

getCfgDirList(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

获取配置层级目录列表，按优先级从低到高。使用callback异步回调。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                     | 必填 | 说明                               |
| -------- | ---------------------------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是   | 回调函数。当获取配置层级目录列表成功，error为undefined，value为获取到的配置层级目录列表；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      configPolicy.getCfgDirList((error: BusinessError, value: Array<string>) => {
        if (error == null) {
          console.info('value is ' + value);
        } else {
          console.error('error: ' + error.code + ', ' + error.message);
        }
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      configPolicy.getCfgDirList((error: BusinessError | null, value: Array<string> | undefined) => {
        if (error == null) {
          console.info('value is ' + value);
        } else {
          console.error('error: ' + error.code + ', ' + error.message);
        }
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgDirList

getCfgDirList(): Promise&lt;Array&lt;string&gt;&gt;

获取配置层级目录列表，按优先级从低到高。使用Promise异步回调。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                               | 说明             |
| ---------------------------------- | ---------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回配置层级目录列表。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      configPolicy.getCfgDirList().then((value: Array<string>) => {
        console.info('value is ' + value);
      }).catch((error: BusinessError) => {
        console.error('getCfgDirList promise error: ' + error.code + ', ' + error.message);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      configPolicy.getCfgDirList().then((value: Array<string>) => {
        console.info('value is ' + value);
      }).catch((error: Error) => {
        console.error('getCfgDirList promise error: ' + error);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getOneCfgFile<sup>11+</sup>

getOneCfgFile(relPath: string, followMode: FollowXMode, callback: AsyncCallback&lt;string&gt;): void

根据提供的跟随模式获取指定文件名优先级最高的配置文件路径。使用callback异步回调。

例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                          | 必填 | 说明                                       |
| ---------- | ----------------------------- | ---- | ------------------------------------------ |
| relPath    | string                        | 是   | 配置文件名。                                 |
| followMode | [FollowXMode](#followxmode11) | 是   | 跟随模式。                                   |
| callback   | AsyncCallback&lt;string&gt;   | 是   | 回调函数。当获取配置文件路径成功，error为undefined，value为获取到的优先级最高的配置文件路径；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.SIM_DEFAULT,
        (error: BusinessError, value: string) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.SIM_DEFAULT,
        (error: BusinessError | null, value: string | undefined) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getOneCfgFile<sup>11+</sup>

getOneCfgFile(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback&lt;string&gt;): void

根据跟随模式获取指定文件优先级最高的配置文件路径。使用callback异步回调。
例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                          | 必填 | 说明                                                   |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | 是   | 配置文件名。                                             |
| followMode | [FollowXMode](#followxmode11) | 是   | 跟随模式。                                               |
| extra      | string                        | 是   | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](#followxmode11)时有效。 |
| callback   | AsyncCallback&lt;string&gt;   | 是   | 回调函数。当获取配置文件路径成功，error为undefined，value为获取到的优先级最高的配置文件路径；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.USER_DEFINED, extra,
        (error: BusinessError, value: string) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.USER_DEFINED, extra,
        (error: BusinessError | null, value: string | undefined) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getOneCfgFile<sup>11+</sup>

getOneCfgFile(relPath: string, followMode: FollowXMode, extra?: string): Promise&lt;string&gt;

根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                          | 必填 | 说明                                                   |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | 是   | 配置文件名。                                             |
| followMode | [FollowXMode](#followxmode11) | 是   | 跟随模式。                                               |
| extra      | string                        | 否   | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](#followxmode11)时有效。 |

**返回值：**

| 类型                   | 说明                     |
| ---------------------- | ------------------------ |
| Promise&lt;string&gt;  | Promise对象，返回优先级最高的配置文件路径。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra).then((value: string) => {
        console.info('value is ' + value);
      }).catch((error: BusinessError) => {
        console.error('getOneCfgFile promise error: ' + error.code + ', ' + error.message);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra).then((value: string) => {
        console.info('value is ' + value);
      }).catch((error: Error) => {
        console.error('getOneCfgFile promise error: ' + error);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getOneCfgFileSync<sup>11+</sup>

getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string

根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                          | 必填 | 说明                                                 |
| ---------- | ----------------------------- | ---- | ----------------------------------------------------|
| relPath    | string                        | 是   | 配置文件名。                                           |
| followMode | [FollowXMode](#followxmode11) | 否   | 跟随模式，不设置时，默认使用[DEFAULT](#followxmode11)。                    |
| extra      | string                        | 否   | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](#followxmode11)时有效。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| string | 返回优先级最高的配置文件路径。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      let result: string = configPolicy.getOneCfgFileSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
      console.info('result is ' + result);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      let result: string = configPolicy.getOneCfgFileSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
      console.info('result is ' + result);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgFiles<sup>11+</sup>

getCfgFiles(relPath: string, followMode: FollowXMode, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。

例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                     | 必填 | 说明                       |
| ---------- | ---------------------------------------- | ---- | -------------------------- |
| relPath    | string                                   | 是   | 配置文件名。                 |
| followMode | [FollowXMode](#followxmode11)            | 是   | 跟随模式。                   |
| callback   | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是   | 回调函数。当获取文件列表成功，error为undefined，value为获取到的文件列表；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT,
        (error: BusinessError, value: Array<string>) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT,
        (error: BusinessError | null, value: Array<string> | undefined) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgFiles<sup>11+</sup>

getCfgFiles(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。

例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                     | 必填 | 说明                                                   |
| ---------- | ---------------------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                                   | 是   | 配置文件名。                                             |
| followMode | [FollowXMode](#followxmode11)            | 是   | 跟随模式。                                               |
| extra      | string                                   | 是   | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](#followxmode11)时有效。 |
| callback   | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是   | 回调函数。当获取文件列表成功，error为undefined，value为获取到的文件列表；否则error为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.USER_DEFINED, extra,
        (error: BusinessError, value: Array<string>) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.USER_DEFINED, extra,
        (error: BusinessError | null, value: Array<string> | undefined) => {
          if (error == null) {
            console.info('value is ' + value);
          } else {
            console.error('error: ' + error.code + ', ' + error.message);
          }
        });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgFiles<sup>11+</sup>

getCfgFiles(relPath: string, followMode: FollowXMode, extra?: string): Promise&lt;Array&lt;string&gt;&gt;

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用Promise异步回调。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                          | 必填 | 说明                                                   |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | 是   | 配置文件名。                                             |
| followMode | [FollowXMode](#followxmode11) | 是   | 跟随模式。                                               |
| extra      | string                        | 否   | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](#followxmode11)时有效。 |

**返回值：**

| 类型                               | 说明     |
| ---------------------------------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回文件列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra).then((value: Array<string>) => {
        console.info('value is ' + value);
      }).catch((error: BusinessError) => {
        console.error('getCfgFiles promise error: ' + error.code + ', ' + error.message);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra).then((value: Array<string>) => {
        console.info('value is ' + value);
      }).catch((error: Error) => {
        console.error('getCfgFiles promise error: ' + error);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgFilesSync<sup>11+</sup>

getCfgFilesSync(relPath: string, followMode?: FollowXMode, extra?: string): Array&lt;string&gt;

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                          | 必填 | 说明                                                   |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | 是   | 配置文件名。                                             |
| followMode | [FollowXMode](#followxmode11) | 否   | 跟随模式，不设置时，默认使用[DEFAULT](#followxmode11)。                    |
| extra      | string                        | 否   | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](#followxmode11)时有效。 |

**返回值：**

| 类型                | 说明     |
| ------------------- | -------- |
| Array&lt;string&gt; | 返回文件列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      let result: Array<string> = configPolicy.getCfgFilesSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
      console.info('result is ' + result);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      let result: Array<string> = configPolicy.getCfgFilesSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
      console.info('result is ' + result);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## getCfgDirListSync<sup>11+</sup>

getCfgDirListSync(): Array&lt;string&gt;

获取配置层级目录列表，按优先级从低到高。

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                | 说明             |
| ------------------- | ---------------- |
| Array&lt;string&gt; | 返回配置层级目录列表。 |


**示例：**

ArkTS-Dyn示例：
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let result: Array<string> = configPolicy.getCfgDirListSync();
      console.info('result is ' + result);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

ArkTS-Sta示例：
```ts
'use static'

import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      let result: Array<string> = configPolicy.getCfgDirListSync();
      console.info('result is ' + result);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error: ' + code + ', ' + message);
    }
  }
}
```

## FollowXMode<sup>11+</sup>

**系统能力：** SystemCapability.Customization.ConfigPolicy

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称                          | 值  | 说明                                                                                            |
| ----------------------------- | --- | ----------------------------------------------------------------------------------------------- |
| DEFAULT                       | 0   | 默认模式，会根据各配置层级下的followx_file_list.cfg文件配置的跟随规则进行文件查找。                   |
| NO_RULE_FOLLOWED              | 1   | 不跟随模式，不会使用任何跟随规则，即使存在followx_file_list.cfg文件。                                |
| SIM_DEFAULT                   | 10  | 跟随默认卡模式，会根据默认卡的opkey在各配置层级下的etc/carrier/${opkey}下查找文件。                   |
| SIM_1                         | 11  | 跟随卡1模式，会根据卡1的opkey在各配置层级下的etc/carrier/${opkey}下查找文件。                        |
| SIM_2                         | 12  | 跟随卡2模式，会根据卡2的opkey在各配置层级下的etc/carrier/${opkey}下查找文件。                        |
| USER_DEFINED                  | 100 | 用户自定义模式，会根据入参extra提供的跟随规则进行配置文件获取，忽略各配置层级下的followx_file_list.cfg文件。 | 
