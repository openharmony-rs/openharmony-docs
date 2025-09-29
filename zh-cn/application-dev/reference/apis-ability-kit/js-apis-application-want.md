# @ohos.application.Want (Want)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

Want是对象间信息传递的载体，可以用于应用组件间的信息传递。Want的使用场景之一是作为startAbility的参数，其包含了指定的启动目标，以及启动时需携带的相关数据，如bundleName和abilityName字段分别指明目标Ability所在应用Bundle名称以及对应包内的Ability名称。当Ability A需要启动Ability B并传入一些数据时，可使用Want作为载体将这些数据传递给Ability B。

> **说明：**
>
> 本模块首批接口从API version 8 开始支持，从API version 9废弃，替换模块为[@ohos.app.ability.Want](js-apis-app-ability-want.md)。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import Want from '@ohos.application.Want';
```

## Want

**系统能力**：SystemCapability.Ability.AbilityBase

| 名称        | 类型                 | 只读 | 可选 | 说明                                                         |
| ----------- | -------------------- | ---- | ---- | ------------------------------------------------------------ |
| deviceId    | string               | 否   | 是   | 表示运行指定Ability的设备ID。如果未设置该字段，则表明指定本设备。                                |
| bundleName   | string               | 否   | 是   | 表示Bundle名称。 |
| abilityName  | string               | 否   | 是   | 表示待启动的Ability名称。如果在Want中该字段同时指定了BundleName和AbilityName，则Want可以直接匹配到指定的Ability。AbilityName需要在一个应用的范围内保证唯一。 |
| uri          | string               | 否   | 是   | 表示Uri描述。如果在Want中指定了Uri，则Want将匹配指定的Uri信息，包括scheme、schemeSpecificPart、authority和path信息。 |
| type         | string               | 否   | 是   | 表示MIME type类型描述，打开文件的类型，主要用于文管打开文件。比如：'text/xml' 、 'image/*'等，MIME定义参考：https://www.iana.org/assignments/media-types/media-types.xhtml?utm_source=ld246.com。   |
| flags        | number               | 否   | 是   | 表示处理Want的方式。默认传数字，具体参考：[flags说明](js-apis-ability-wantConstant.md#flags)。 |
| action      | string               | 否   | 是   | 表示要执行的通用操作（如：查看、分享、应用详情）。在隐式Want中，您可以定义该字段，配合uri或parameters来表示对数据要执行的操作。具体参考：[action说明](js-apis-ability-wantConstant.md#action)。隐式Want定义及匹配规则参考：[显式Want与隐式Want匹配规则](../../application-models/explicit-implicit-want-mappings.md)。                           |
| parameters   | { [key: string]: any } | 否   | 是   | 表示WantParams描述，由开发者自行决定传入的键值对。默认会携带以下key值：<br>ohos.aafwk.param.callerPid 表示拉起方的pid。<br>ohos.aafwk.param.callerToken 表示拉起方的token。<br>ohos.aafwk.param.callerUid 表示[bundleInfo](js-apis-bundle-BundleInfo.md#bundleinfodeprecated)中的uid，应用包里应用程序的uid。<br />- component.startup.newRules：表示是否启用新的管控规则。<br />- moduleName：表示拉起方的模块名，该字段的值即使定义成其他字符串，在传递到另一端时会被修改为正确的值。<br />- ohos.dlp.params.sandbox：表示dlp文件才会有。                                       |
| entities    | Array\<string>       | 否   | 是   | 表示目标Ability额外的类别信息（如：浏览器、视频播放器）。在隐式Want中是对action字段的补充。在隐式Want中，您可以定义该字段，来过滤匹配Ability类型。具体参考：[entity说明](js-apis-ability-wantConstant.md#entity)。                                    |

**示例：**

- 基础用法(在UIAbility对象中调用，其中示例中的context为UIAbility的上下文对象)。

    ```ts
    import Want from '@ohos.application.Want';
    import { BusinessError } from '@ohos.base';
    import UIAbility from '@ohos.app.ability.UIAbility';
    import AbilityConstant from '@ohos.app.ability.AbilityConstant';

    let want: Want = {
    'deviceId': '', // deviceId为空表示本设备
    'bundleName': 'com.example.myapplication',
    'abilityName': 'EntryAbility',
    };
    class MyAbility extends UIAbility{
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam){
        this.context.startAbility(want, (error: BusinessError) => {
        // 显式拉起Ability，通过bundleName、abilityName和moduleName可以唯一确定一个Ability
        console.error(`error.code = ${error.code}`);
        });
    }
    }
    ```

- 通过自定字段传递数据，以下为当前支持类型(在UIAbility对象中调用，其中示例中的context为UIAbility的上下文对象)。

    * 字符串（String）
        ```ts
        import Want from '@ohos.application.Want';

        let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
                keyForString: 'str',
            },
        };
        ```
    * 数字（Number）
        ```ts
        import Want from '@ohos.application.Want';

        let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
                keyForInt: 100,
                keyForDouble: 99.99,
            },
        };
        ```
    * 布尔（Boolean）
        ```ts
        import Want from '@ohos.application.Want';

        let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
                keyForBool: true,
            },
        };
        ```
    * 对象（Object）
        ```ts
        import Want from '@ohos.application.Want';

        let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
                keyForObject: {
                    keyForObjectString: 'str',
                    keyForObjectInt: -200,
                    keyForObjectDouble: 35.5,
                    keyForObjectBool: false,
                },
            },
        };
        ```
    * 数组（Array）
        ```ts
        import Want from '@ohos.application.Want';

        let want: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EntryAbility',
            parameters: {
                keyForArrayString: ['str1', 'str2', 'str3'],
                keyForArrayInt: [100, 200, 300, 400],
                keyForArrayDouble: [0.1, 0.2],
                keyForArrayObject: [{obj1: 'aaa'}, {obj2: 100}],
            },
        };
        ```
    * 文件描述符（FD）
        ```ts
        import fs from '@ohos.file.fs';
        import Want from '@ohos.application.Want';
        import { BusinessError } from '@ohos.base';
        import AbilityConstant from '@ohos.app.ability.AbilityConstant';
        import UIAbility from '@ohos.app.ability.UIAbility';


        let fd: number = 0;
        try {
        fd = fs.openSync('/data/storage/el2/base/haps/pic.png').fd;
        } catch(e) {
        console.error(`openSync fail: ${JSON.stringify(e)}`);
        }
        let want: Want = {
        deviceId: '', // deviceId为空表示本设备
        bundleName: 'com.example.myapplication',
        abilityName: 'EntryAbility',
        parameters: {
            'keyFd':{'type':'FD', 'value':fd}
        }
        };

        class MyAbility extends UIAbility{
        onCreate(want: Want, launchParam: AbilityConstant.LaunchParam){
            this.context.startAbility(want, (error: BusinessError) => {
            // 显式拉起Ability，通过bundleName、abilityName和moduleName可以唯一确定一个Ability
            console.error(`error.code = ${error.code}`);
            });
        }
        }
        ```
