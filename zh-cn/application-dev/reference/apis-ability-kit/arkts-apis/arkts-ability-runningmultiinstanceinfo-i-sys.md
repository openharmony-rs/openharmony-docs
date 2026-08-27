# RunningMultiInstanceInfo（系统接口）

定义多实例应用在运行态的结构信息，通过appManager的 [getRunningMultiAppInfo](arkts-ability-appmanager-getrunningmultiappinfo-f-sys.md)来获取。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## instanceKey

```TypeScript
instanceKey: string
```

多实例应用的唯一实例标识。

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pids

```TypeScript
pids: Array<number>
```

应用的进程ID集合。

**类型：** Array&lt;number&gt;

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

表示应用程序的UID。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
      console.info(`getRunningMultiAppInfo success`);
    }).catch((err: BusinessError) => {
      console.error(`getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
    });
} catch (err: BusinessError) {
  console.error(`getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
}
```
