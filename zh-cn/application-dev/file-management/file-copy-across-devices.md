# 跨设备文件拷贝
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wang_zhangjun; @gzhuangzhuang-->
<!--Designer: @wang_zhangjun; @gzhuangzhuang; @renguang1116-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

分布式文件系统为应用提供了跨设备文件拷贝的能力，开发者可以通过[基础文件接口](../reference/apis-core-file-kit/js-apis-file-fs.md)进行跨设备拷贝文件。例如：多设备数据流转的场景，设备组网互联之后，设备A上的应用可将沙箱文件拷贝到设备A的分布式目录下。设备B在粘贴时，从B设备的分布式目录下将文件拷贝到对应的沙箱文件中。

## 开发步骤

1. 完成分布式组网。
   将需要跨设备访问的两个设备登录同一账号，保证设备蓝牙和Wi-Fi功能开启，蓝牙无需互连，Wi-Fi无需接入同一个局域网。

2. 授权分布式数据同步权限。
   分布式数据同步权限的授权方式为user_grant，因此需要调用requestPermissionsFromUser接口，以动态弹窗的方式向用户申请授权。示例中的context的获取方式请参见[获取UIAbility的上下文信息](../application-models/uiability-usage.md#获取uiability的上下文信息)。

   ```ts
   import { common, abilityAccessCtrl } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```
   <!--@[distributed_Data_Permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/DistributedFileSample/entry/src/main/ets/pages/Index.ets)-->

3. 执行跨设备文件拷贝操作。
   同一应用在不同设备之间实现跨设备文件拷贝，只需要将对应的文件放在应用沙箱的分布式目录即可。

   将A设备的待拷贝沙箱文件拷贝到A设备的分布式目录下。

   ```ts
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { common } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { fileUri } from '@kit.CoreFileKit';
   ```
   <!--@[copy_sand_to_distributed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/DistributedFileSample/entry/src/main/ets/pages/Index.ets)-->

   B设备在获取A设备沙箱文件时，从B设备的分布式目录下将对应的文件拷贝走，以此完成跨设备拷贝。

   ```ts
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { common } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { fileUri } from '@kit.CoreFileKit';
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   ```
   <!--@[copy_distributed_to_sand](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/DistributedFileSample/entry/src/main/ets/pages/Index.ets)-->

4. 跨设备文件拷贝完成，断开链路。

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { distributedDeviceManager } from '@kit.DistributedServiceKit'
   import { fileIo as fs } from '@kit.CoreFileKit';
   ```
   <!--@[access_DisConnectDfs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/DistributedFileSample/entry/src/main/ets/pages/Index.ets)-->
