# createPluginModuleContextForHostBundle（系统接口）

## 导入模块

```TypeScript
import { application } from '@kit.AbilityKit';
```

<a id="createpluginmodulecontextforhostbundle"></a>
## createPluginModuleContextForHostBundle

```TypeScript
export function createPluginModuleContextForHostBundle(context: Context, pluginBundleName: string, pluginModuleName: string,
    hostBundleName: string): Promise<Context>
```

根据入参Context、插件包名和插件模块名和应用包名，创建对应插件的Context，用于获取插件的基本信息。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-application-export function createPluginModuleContextForHostBundle(context: Context, pluginBundleName: string, pluginModuleName: string,
    hostBundleName: string): Promise<Context>--><!--Device-application-export function createPluginModuleContextForHostBundle(context: Context, pluginBundleName: string, pluginModuleName: string,
    hostBundleName: string): Promise<Context>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 表示应用上下文。 |
| pluginBundleName | string | 是 | 表示应用的插件包名。 |
| pluginModuleName | string | 是 | 表示应用的插件模块名。 |
| hostBundleName | string | 是 | 表示安装插件的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Context&gt; | Promise对象。返回创建的Context，返回的Context中的属性processName和config与入参Context中的属性processName和config的值相同。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createPluginModuleContextForHostBundle(this.context, 'com.example.pluginBundleName', 'pluginModuleName', 'com.example.hostBundleName')
        .then((data: Context) => {
          moduleContext = data;
          console.info('createPluginModuleContextForHostBundle success!');
        })
        .catch((error: BusinessError) => {
          let code: number = (error as BusinessError).code;
          let message: string = (error as BusinessError).message;
          console.error(`createPluginModuleContextForHostBundle failed, error.code: ${code}, error.message: ${message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`createPluginModuleContextForHostBundle failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}

```

