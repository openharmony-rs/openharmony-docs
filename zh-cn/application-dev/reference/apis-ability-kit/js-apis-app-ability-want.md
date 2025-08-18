# @ohos.app.ability.Want (Want)

Want是对象间信息传递的载体，可以用于应用组件间的信息传递。

其典型应用场景之一是，当UIAbilityA启动UIAbilityB、并需要传入一些数据时，可使用Want作为载体。例如在startAbility接口的入参want中，可以通过abilityName指定启动的目标Ability，也可以通过parameters等字段携带其他数据。

> **说明：**
>
> 本模块首批接口从API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 约束限制

启动Ability受IPC通信的限制，Want字段中支持传递的最大数据为100KB。

## 导入模块

```ts
import { Want } from '@kit.AbilityKit';
```

## Want

**原子化服务API**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityBase

| 名称        | 类型                 | 只读 | 可选 | 说明                                                         |
| ----------- | -------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| deviceId    | string               | 否 | 是 | 设备ID。在应用启动场景中表示被拉起方的设备ID，如果未设置该字段，则表示指定该设备。               |
| bundleName   | string               | 否 | 是  | 应用包名。在应用启动场景中表示被拉起方的应用包名。 |
| moduleName | string | 否 | 是 | 应用模块名。在应用启动场景中表示被拉起方的应用模块名。<br/>**说明：**<br/> 若待启动的Ability所属的模块为[HAR](../../quick-start/har-package.md)，则moduleName需为依赖该HAR的[HAP](../../quick-start/hap-package.md)/[HSP](../../quick-start/in-app-hsp.md)的moduleName。 |
| abilityName  | string               | 否 | 是  | 应用的Ability组件名。在应用启动场景中表示被拉起方的Ability组件名。如果在Want中该字段同时指定了BundleName和AbilityName，则Want可以直接匹配到指定的Ability。AbilityName需要在一个应用的范围内保证唯一。 |
| action | string               | 否 | 是  | 表示要执行的通用操作（如：查看、分享、应用详情）。在隐式Want中，开发者可以定义该字段，配合uri或parameters来表示对数据执行的操作。隐式Want定义及匹配规则请参见[显式Want与隐式Want匹配规则](../../application-models/explicit-implicit-want-mappings.md)。      |
| entities | Array\<string> | 否 | 是 | 表示目标Ability额外的类别信息（如：浏览器、视频播放器）。在隐式Want中是对action字段的补充。在隐式Want中，您可以定义该字段，来过滤匹配Ability类型。 |
| uri | string | 否 | 是 | 统一资源标识符，一般在应用启动场景中配合type使用，指明待处理的数据类型。如果在Want中指定了uri，则Want将匹配指定的Uri信息，包括`scheme`、`schemeSpecificPart`、`authority`和`path`信息。 |
| type | string | 否 | 是 | 表示MIME type类型描述，打开文件的类型，主要用于文管打开文件。比如：'text/xml' 、 'image/*'等，MIME定义请参见[Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com)。 |
| parameters   | Record\<string, Object> | 否 | 是  | 表示WantParams描述。<br />一、以下Key均由系统赋值，开发者手动修改也不会生效，系统在数据传递时会自动修改为实际值。<br />- ohos.aafwk.param.callerPid：表示拉起方的pid，值为字符串类型。<br />- ohos.aafwk.param.callerBundleName：表示拉起方的BundleName，值为字符串类型。<br />- ohos.aafwk.param.callerAbilityName：表示拉起方的AbilityName，值为字符串类型。<br />- ohos.aafwk.param.callerNativeName：表示native调用时拉起方的进程名，值为字符串类型。<br />- ohos.aafwk.param.callerAppId：表示拉起应用的AppId信息，值为字符串类型。<br />- ohos.aafwk.param.callerAppIdentifier：表示拉起应用的AppIdentifier信息，值为字符串类型。<br />- ohos.aafwk.param.callerToken：表示拉起方的token，值为字符串类型。<br />- ohos.aafwk.param.callerUid：表示[BundleInfo](js-apis-bundleManager-bundleInfo.md#bundleinfo-1)中的uid，应用包里应用程序的uid，值为数值类型。<br />- ohos.param.callerAppCloneIndex：表示拉起方应用的分身索引，值为数值类型。<br />- component.startup.newRules：表示是否启用新的管控规则，值为布尔类型。<br />- moduleName：表示拉起方的moduleName，值为字符串类型。<br />- ohos.ability.params.abilityRecoveryRestart：表示当前Ability是否发生了故障恢复重启，值为布尔类型。<br />- ohos.extra.param.key.showMode：表示拉起原子化服务的展示模式，值为枚举类型[wantConstant.ShowMode](js-apis-app-ability-wantConstant.md#showmode12)。<br /><br />二、提供了一些由系统定义、开发者按需赋值的Key。具体的key值与对应说明详见[wantConstant.Params](js-apis-app-ability-wantConstant.md#params)<!--Del-->以及[wantConstant.Params(仅系统应用可用)](js-apis-app-ability-wantConstant-sys.md#params)<!--DelEnd-->。<br /><br />三、除了上述情况，应用间还可以相互约定传入的键值对。<br /><br />**说明**：<br/>want的Params操作的常量的具体信息请参考[wantConstant](js-apis-app-ability-wantConstant.md)。<br/>需注意，WantParams支持传输的最大数据量约为100KB。当数据量超过100KB时，请使用[WriteRawDataBuffer](../apis-ipc-kit/js-apis-rpc.md#writerawdatabuffer11)或[uri](../apis-arkts/js-apis-uri.md)的方式进行数据传输。<br/>parameters的Value值仅支持基本数据类型：String、Number、Boolean、Object、undefined和null，不支持传递Object内部的function。 |
| [flags](js-apis-app-ability-wantConstant.md#flags) | number | 否 | 是 | 表示处理Want的方式。默认传数字。<br />例如取值为0x00000001（即wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION）表示临时授予接收方读取该URI指向的数据的权限。 |
| fds<sup>15+</sup> | Record\<string, number> | 是 | 是 | 表示文件描述符，在启动场景中拉起方写入的FD，会设置到该参数中。<br>**原子化服务API**：从API version 15开始，该接口支持在原子化服务中使用。 |

**示例：**

- 基础用法：在UIAbility对象中调用，示例中的context的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

  ```ts
  import { UIAbility, Want } from '@kit.AbilityKit';
  import { window } from '@kit.ArkUI';
  import { BusinessError } from '@kit.BasicServicesKit';

  export default class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage): void {
      let want: Want = {
        deviceId: '', // deviceId为空表示本设备
        bundleName: 'com.example.myapplication',
        abilityName: 'FuncAbility',
        moduleName: 'entry' // moduleName非必选
      };

      this.context.startAbility(want, (err: BusinessError) => {
        if (err.code) {
          // 显式拉起Ability，通过bundleName、abilityName和moduleName可以唯一确定一个Ability
          console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
        }
      });
    }
  }
  ```

- 目前支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等。

    * 字符串（String）
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForString: 'str',
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * 数字（Number）
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForInt: 100,
                keyForDouble: 99.99,
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * 布尔（Boolean）
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForBool: true,
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * 对象（Object）
        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForObject: {
                  keyForObjectString: 'str',
                  keyForObjectInt: -200,
                  keyForObjectDouble: 35.5,
                  keyForObjectBool: false,
                },
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * 数组（Array）

        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                keyForArrayString: ['str1', 'str2', 'str3'],
                keyForArrayInt: [100, 200, 300, 400],
                keyForArrayDouble: [0.1, 0.2],
                keyForArrayObject: [{ obj1: 'aaa' }, { obj2: 100 }],
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```

    * 文件描述符（FD）

        ```ts
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';
        import { fileIo } from '@kit.CoreFileKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let fd: number = 0;

            try {
              fd = fileIo.openSync('/data/storage/el2/base/haps/pic.png').fd;
            } catch (err) {
              let code = (err as BusinessError).code;
              let message = (err as BusinessError).message;
              console.error(`Failed to openSync. Code: ${code}, message: ${message}`);
            }
            let want: Want = {
              deviceId: '', // deviceId为空表示本设备
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              moduleName: 'entry', // moduleName非必选
              parameters: {
                'keyFd': { 'type': 'FD', 'value': fd } // {'type':'FD', 'value':fd}是固定用法，用于表示该数据是FD
              }
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```

    * parameters参数用法：parameters携带开发者自定义参数，由UIAbilityA传递给UIAbilityB，并在UIAbilityB中进行获取。

        ```ts
        // (1) UIAbilityA通过startability启动UIAbilityB
        import { UIAbility, Want } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'UIAbilityB',
              parameters: {
                developerParameters: 'parameters',
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```

        ```ts
        // (2) 以UIAbilityB实例首次启动为例，会进入到UIAbilityB的onCreate生命周期
        import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

        class UIAbilityB extends UIAbility {
          onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
            console.log(`onCreate, want parameters: ${want.parameters?.developerParameters}`);
          }
        }
        ```
    * parameters参数中[wantConstant](js-apis-app-ability-wantConstant.md)的Key的使用方法。

        ```ts
        import { UIAbility, Want, wantConstant } from '@kit.AbilityKit';
        import { window } from '@kit.ArkUI';
        import { BusinessError } from '@kit.BasicServicesKit';

        export default class EntryAbility extends UIAbility {
          onWindowStageCreate(windowStage: window.WindowStage): void {
            let want: Want = {
              bundleName: 'com.example.myapplication',
              abilityName: 'FuncAbility',
              parameters: {
                [wantConstant.Params.CONTENT_TITLE_KEY]: 'contentTitle',
              },
            };

            this.context.startAbility(want, (err: BusinessError) => {
              if (err.code) {
                console.error(`Failed to startAbility. Code: ${err.code}, message: ${err.message}`);
              }
            });
          }
        }
        ```
    * parameters参数中获取拉起方的信息。

      详见[获取UIAbility拉起方的信息](../../application-models/uiability-usage.md#获取uiability拉起方的信息)。
