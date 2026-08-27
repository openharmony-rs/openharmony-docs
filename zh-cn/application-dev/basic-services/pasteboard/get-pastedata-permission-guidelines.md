# 申请访问剪贴板权限
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @zhusiyuan2-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## 概述

API version 12及之后，系统为提升用户隐私安全保护能力，剪贴板读取接口增加权限管控。

涉及接口如下：

| 名称 | 说明                                                                                                                                        |
| -------- |----------------------------------------------------------------------------------------------------------------------------------------|
| getData(callback: AsyncCallback&lt;PasteData&gt;): void | 读取系统剪贴板内容，使用callback异步回调。 |
| getData(): Promise&lt;PasteData&gt; | 读取系统剪贴板内容，使用Promise异步回调。 |
| getDataSync(): PasteData | 读取系统剪贴板内容, 此接口为同步接口。 |
| getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData\> | 从系统剪贴板中读取统一数据对象的数据。 |
| getUnifiedDataSync(): unifiedDataChannel.UnifiedData | 从系统剪贴板中读取统一数据对象的数据，此接口为同步接口。 |
| OH_UdmfData* OH_Pasteboard_GetData (OH_Pasteboard *pasteboard, int *status) | 获取剪贴板中的数据。 |
| getDataWithProgress(params: GetDataParams): Promise\<PasteData\> | 获取剪贴板的内容和进度，使用Promise异步回调，不支持对文件夹的拷贝。 |
| OH_UdmfData* OH_Pasteboard_GetDataWithProgress(OH_Pasteboard* pasteboard, Pasteboard_GetDataParams* params, int* status) | 获取剪贴板的数据以及粘贴进度，不支持对文件夹的拷贝。 |

> **说明：**
>
> 申请访问剪贴板权限前，需提前判断剪贴板上的内容是否包含应用所需数据，包括但不限于hasData检查是否有数据、hasDataType/getMimeTypes检查是否有应用所需类型、getChangeCount检查数据是否改变，详见剪贴板弹窗适配优化。

## 访问剪贴板内容

剪贴板为应用提供如下两种访问内容的方式。

- 使用安全控件

    使用粘贴控件访问剪贴板内容的应用，可以无需申请权限。

    已经使用了安全控件的应用无需做任何适配就可以访问剪贴板内容。

- 申请ohos.permission.READ_PASTEBOARD权限

    ohos.permission.READ_PASTEBOARD是受限的user_grant（用户授权）权限，使用自定义控件的应用申请此权限后，在用户授权场景下可访问剪贴板内容。

    权限申请步骤：
    <!--RP1-->
    1.通过ACL方式，申请高级别权限。
    
    2.在module.json5配置文件中声明权限。
    
    3.通过弹窗向用户申请授权。
    <!--RP1End-->

## 剪贴板弹窗适配优化

应用申请剪贴板权限需要提前判断剪贴板上的内容是否包含所需数据，避免出现无效弹框。

- 使用hasData判断剪贴板是否有数据，无数据则不访问剪贴板。

- 使用hasDataType/getMimeTypes判断是否包含应用当前场景支持处理的数据类型，如果没有对应的数据类型，则不访问剪贴板。

- 使用getChangeCount获取剪贴板的内容变化次数，与上次读取剪贴板时查询的变化次数比较是否一致，一致则剪贴板内容无变化，不访问剪贴板。

- 使用detectPatterns判断是否包含应用自身口令的格式，如果格式不匹配，则不访问剪贴板。应用读取口令后如果确认是自身的口令，建议使用clearData清除剪贴板口令内容。

## 示例代码

<!-- @[pasteboard_permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/pasteboard/pasteboard_arkts_sample/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { BusinessError, pasteboard } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, common, Permissions } from '@kit.AbilityKit';
import { preferences } from '@kit.ArkData';
import { hilog } from '@kit.PerformanceAnalysisKit';

const permissions: Permissions[] = ['ohos.permission.READ_PASTEBOARD'];
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
const patterns: pasteboard.Pattern[] = [pasteboard.Pattern.URL, pasteboard.Pattern.EMAIL_ADDRESS];
let dataPreferences: preferences.Preferences | null = null;
// ...
async function isNeedGetPermissionFromUser(): Promise<boolean> {
  try {
    let hasData: boolean = await systemPasteboard.hasData();
    if (!hasData) {
      // 剪贴板不存在数据，无需申请权限
      return false;
    }
    // 获取剪贴板的内容变化次数
    let result: number = systemPasteboard.getChangeCount();
    hilog.info(0xFF00, '[Sample_pasteboard]', `Succeeded in getting the ChangeCount. Result: ${result}`);
    // 从 Preferences 中读取上次保存的 changeCount
    let storedChangeCount: number = dataPreferences ? Number(dataPreferences.getSync('pasteboardChangeCount', 0)) : 0;
    if (result === storedChangeCount) {
      // 剪贴板无数据变化，无需申请权限
      return false;
    }
  } catch (err) {
    hilog.error(0xFF00, '[Sample_pasteboard]', `Failed to get the ChangeCount. Cause: ${err.message}`);
    return false;
  };

  // 查询剪贴板是否存在应用所需数据类型
  try {
    // (可选)判断是否有应用需要的数据类型
    let result: boolean = systemPasteboard.hasDataType(pasteboard.MIMETYPE_TEXT_PLAIN);
    hilog.info(0xFF00, '[Sample_pasteboard]', `Succeeded in checking the DataType. Result: ${result}`);
    if (!result) {
      // 剪贴板不存在应用所需数据类型，无需申请权限
      return false;
    }
    // (可选)涉及口令等应用自身特殊复制内容的，使用detectPatterns过滤口令格式
    let data: pasteboard.Pattern[] = await systemPasteboard.detectPatterns(patterns);
    if (patterns.sort().join('') != data.sort().join('')) {
      hilog.info(0xFF00, '[Sample_pasteboard]', 'Not all needed patterns detected, no need to get data.');
      return false;
    }
  } catch (err) {
    hilog.error(0xFF00, '[Sample_pasteboard]', `Failed to check the DataType. Cause: ${err.message}`);
    return false;
  };
  return true;
}

@Entry
@Component
struct Index {
  // ...

  build() {
    Row() {
      Column() {
        // ...
        Button('粘贴')
          // ...
          .onClick(async () => {
            const context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
            if (!(await isNeedGetPermissionFromUser())) {
              hilog.info(0xFF00, '[Sample_pasteboard]', 'No need to bring up the permission pop-up window');
              return;
            }
            let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
            // requestPermissionsFromUser会判断权限的授权状态来决定是否唤起弹窗。
            try {
              let data = await atManager.requestPermissionsFromUser(context, permissions);
              let grantStatus: number[] = data.authResults;
              for (const status of grantStatus) {
                if (status === 0) {
                  // 用户授权，使用get操作读取剪贴板内容。
                  // ...
                  // 执行判断口令逻辑，如果是本应用口令，建议获取完数据后使用cleardata清除剪贴板口令内容
                  try {
                    await systemPasteboard.clearData();
                    hilog.info(0xFF00, '[Sample_pasteboard]', 'Succeeded in clearing the pasteboard.');
                  } catch (err) {
                    hilog.error(0xFF00, '[Sample_pasteboard]', `Failed to clear the pasteboard. Cause: ${err.message}`);
                  }
                  // 获取当前 ChangeCount
                  let currentChangeCount: number = systemPasteboard.getChangeCount();
                  hilog.info(0xFF00, '[Sample_pasteboard]', `Current ChangeCount: ${currentChangeCount}`);
                  // 更新 Preferences 中的 ChangeCount
                  if (dataPreferences) {
                    dataPreferences.putSync('pasteboardChangeCount', currentChangeCount);
                    dataPreferences.flushSync(); // 确保数据写入持久化存储
                    hilog.info(0xFF00, '[Sample_pasteboard]', `ChangeCount has been updated to: ${currentChangeCount}`);
                  }
                } else {
                  // 用户拒绝授权，提示用户必须授权才能访问当前页面的功能，并引导用户到系统设置中打开相应的权限。
                  return;
                }
              }
              // 授权成功。
            } catch (err) {
              hilog.error(0xFF00, '[Sample_pasteboard]', 'Failed to request permissions from user.');
            }
          })
        // ...
      }
      // ...
    }
    // ...
  }
}
```
