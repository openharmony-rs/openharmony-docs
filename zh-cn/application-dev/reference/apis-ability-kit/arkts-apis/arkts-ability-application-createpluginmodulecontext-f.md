# createPluginModuleContext

## createPluginModuleContext

```TypeScript
export function createPluginModuleContext(context: Context, pluginBundleName: string, pluginModuleName: string): Promise<Context>
```

根据入参Context、指定的插件包名和插件模块名，创建本应用下插件的Context，用于获取插件的基本信息。使用Promise异步回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 表示应用上下文。 |
| pluginBundleName | string | 是 | 表示应用的插件包名。 |
| pluginModuleName | string | 是 | 表示应用的插件模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Context&gt; | Promise对象。返回创建的Context。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, application, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let moduleContext: common.Context;
    try {
      application.createPluginModuleContext(this.context, 'com.example.pluginBundleName', 'pluginModuleName')
        .then((data: Context) => {
          moduleContext = data;
          console.info('createPluginModuleContext success!');
        })
        .catch((error: BusinessError) => {
          let code: number = (error as BusinessError).code;
          let message: string = (error as BusinessError).message;
          console.error(`createPluginModuleContext failed, error.code: ${code}, error.message: ${message}`);
        });
    } catch (error) {
      let code: number = (error as BusinessError).code;
      let message: string = (error as BusinessError).message;
      console.error(`createPluginModuleContext failed, error.code: ${code}, error.message: ${message}`);
    }
  }
}

```

