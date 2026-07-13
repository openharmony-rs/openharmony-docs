# ResourceManager

提供访问应用资源和系统资源的能力。

> **说明：**
>
> - ResourceManager涉及到的方法，仅限基于TS扩展的声明式开发范式使用。
>
> - 资源文件在工程的resources目录中定义，通过resName、resId、Resource对象等可以获取对应的字符串、字符串数组、颜色等资源值，resName为资源名称，resId可通过`$r(资源地址).id`的方式
> 获取，例如`$r('app.string.test').id`。
>
> - 单HAP包获取自身资源、跨HAP/HSP包获取资源，由于入参为Resource的接口相比于入参为resName、resId的接口耗时更长，因此更推荐使用参数为resName或resId的接口。跨HAP/HSP包获取资源，
> **需要先使用[createModuleContext](../../apis-ability-kit/arkts-apis/arkts-ability-createmodulecontext-f.md#createmodulecontext-1)创建对应module的context**
> ，再调用参数为resName或resId的接口。更多请参考[资源访问](../../../../quick-start/resource-categories-and-access.md#资源访问)。
>
> - 在API version 22及之前版本，中间码HAR、字节码HAR通过资源ID相关接口访问资源时，因ID无效会抛出异常；从API version 23开始，中间码HAR、字节码HAR通过资源ID相关接口可以正常访问资源，
> 更多请参考[资源访问](../../../../quick-start/resource-categories-and-access.md#资源访问)。
>
> - 示例代码中test文件的具体内容请参考[附录](../../../../reference/apis-localization-kit/js-apis-resource-manager.md#附录)。

**起始版本：** 6

**系统能力：** SystemCapability.Global.ResourceManager

## addResource

```TypeScript
addResource(path: string) : void
```

应用运行时加载指定的资源路径，实现资源覆盖。

> **说明**
>
> rawfile和resfile目录不支持资源覆盖。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 资源路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001010](../errorcode-resource-manager.md#9001010-无效的overlay路径) | Invalid overlay path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "/library1-default-signed.hsp"仅作示例，请替换为实际的文件路径
        let path = this.context.bundleCodeDir + "/library1-default-signed.hsp";
        try {
            this.context.resourceManager.addResource(path);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`addResource failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## closeRawFd

```TypeScript
closeRawFd(path: string, callback: _AsyncCallback<void>): void
```

关闭resources/rawfile目录下rawfile文件所在HAP的文件描述符（fd），使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |
| callback | _AsyncCallback&lt;void&gt; | 是 | 回调函数。当关闭rawfile所在HAP的文件描述符（fd）成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // "test.txt"仅作示例，请替换为实际使用的资源
      let rawfile = this.context.resourceManager.getRawFdSync("test.txt");
      // 根据实际业务场景，使用rawfile资源
      this.context.resourceManager.closeRawFd("test.txt", (error: BusinessError) => {
        if (error != null) {
          console.error("error is " + error);
          return;
        }
        console.info('closeRawFd success.');
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`callback closeRawFd failed, error code: ${code}, message: ${message}.`);
    }
  }
}

```

## closeRawFd

```TypeScript
closeRawFd(path: string): Promise<void>
```

关闭resources/rawfile目录下rawfile文件所在HAP的文件描述符（fd），使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // "test.txt"仅作示例，请替换为实际使用的资源
      let rawfile = this.context.resourceManager.getRawFdSync("test.txt");
      // 根据实际业务场景，使用rawfile资源
      this.context.resourceManager.closeRawFd("test.txt");
      console.info(`closeRawFd test success.`);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`promise closeRawFd failed, error code: ${code}, message: ${message}.`);
    }
  }
}

```

## closeRawFdSync

```TypeScript
closeRawFdSync(path: string): void
```

关闭resources/rawfile目录下rawfile文件所在HAP的文件描述符（fd），使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径 。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // "test.txt"仅作示例，请替换为实际使用的资源
      let rawfile = this.context.resourceManager.getRawFdSync("test.txt");
      // 根据实际业务场景，使用rawfile资源

      this.context.resourceManager.closeRawFdSync("test.txt");
      console.info(`closeRawFdSync test success.`);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`closeRawFdSync test failed, error code: ${code}, message: ${message}.`);
    }
  }
}

```

## closeRawFileDescriptor

```TypeScript
closeRawFileDescriptor(path: string, callback: AsyncCallback<void>): void
```

关闭resources/rawfile目录下rawfile文件的文件描述符（fd），使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeRawFd(path:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当关闭rawfile文件的文件描述符（fd）成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.closeRawFileDescriptor("test.txt", (error: Error) => {
        if (error != null) {
            console.error("error is " + error);
        }
    });
});

```

## closeRawFileDescriptor

```TypeScript
closeRawFileDescriptor(path: string): Promise<void>
```

关闭resources/rawfile目录下rawfile文件的文件描述符（fd），使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeRawFd(path:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.closeRawFileDescriptor("test.txt");
});

```

## getBoolean

```TypeScript
getBoolean(resId: number): boolean
```

获取指定资源ID值对应的布尔值，使用同步方式返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 资源ID值对应的布尔值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/boolean.json
{
  "boolean": [
    {
      "name": "boolean_test",
      "value": true
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.boolean.boolean_test'仅作示例，请替换为实际使用的资源
            let boolTest = this.context.resourceManager.getBoolean($r('app.boolean.boolean_test').id);
            console.info(`getBoolean, result: ${boolTest}`);
            // 打印输出结果: getBoolean, result: true
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getBoolean failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getBoolean

```TypeScript
getBoolean(resource: Resource): boolean
```

获取指定resource对象对应的布尔值，使用同步方式返回。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getBoolean(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | resource对象对应的布尔值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/boolean.json
{
  "boolean": [
    {
      "name": "boolean_test",
      "value": true
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.boolean.boolean_test').id
};
try {
  let boolTest = this.context.resourceManager.getBoolean(resource);
  console.info(`getBoolean, result: ${boolTest}`);
  // 打印输出结果: getBoolean, result: true
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getBoolean failed, error code: ${code}, message: ${message}.`);
}

```

## getBooleanByName

```TypeScript
getBooleanByName(resName: string): boolean
```

获取指定资源名称对应的布尔值，使用同步方式返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 资源名称对应的布尔值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/boolean.json
{
  "boolean": [
    {
      "name": "boolean_test",
      "value": true
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "boolean_test"仅作示例，请替换为实际使用的资源
            let boolTest = this.context.resourceManager.getBooleanByName("boolean_test");
            console.info(`getBooleanByName, result: ${boolTest}`);
            // 打印输出结果: getBooleanByName, result: true
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getBooleanByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getColor

```TypeScript
getColor(resId: number, callback: _AsyncCallback<number>): void
```

获取指定资源ID对应的颜色值，使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | _AsyncCallback&lt;number&gt; | 是 | 回调函数，返回资源ID值对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

## getColor

```TypeScript
getColor(resId: number): Promise<number>
```

获取指定资源ID对应的颜色值，使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回资源ID值对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // 'app.color.test'仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getColor($r('app.color.test').id)
            .then((value: number) => {
                console.info(`getColor, result: ${value}`);
                // 打印输出结果: getColor, result: 4294967295
            })
            .catch((error: BusinessError) => {
                console.error(`promise getColor failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}

```

## getColor

```TypeScript
getColor(resource: Resource, callback: _AsyncCallback<number>): void
```

获取指定resource对象对应的颜色值，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getColor(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| callback | _AsyncCallback&lt;number&gt; | 是 | 回调函数，返回resource对象对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
this.context.resourceManager.getColor(resource, (error: BusinessError, value: number) => {
  if (error != null) {
    console.error(`callback getColor failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getColor, result: ${value}`);
    // 打印输出结果: getColor, result: 4294967295
  }
});

```

## getColor

```TypeScript
getColor(resource: Resource): Promise<number>
```

获取指定resource对象对应的颜色值，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getColor(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回resource对象对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
this.context.resourceManager.getColor(resource)
  .then((value: number) => {
    console.info(`getColor, result: ${value}`);
    // 打印输出结果: getColor, result: 4294967295
  })
  .catch((error: BusinessError) => {
    console.error(`promise getColor failed, error code: ${error.code}, message: ${error.message}.`);
  });

```

## getColorByName

```TypeScript
getColorByName(resName: string, callback: _AsyncCallback<number>): void
```

获取指定资源名称对应的颜色值，使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| callback | _AsyncCallback&lt;number&gt; | 是 | 回调函数，返回资源名称对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "test"仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getColorByName("test", (error: BusinessError, value: number) => {
            if (error != null) {
                console.error(`callback getColorByName failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                console.info(`getColorByName, result: ${value}`);
                // 打印输出结果: getColorByName, result: 4294967295
            }
        });
    }
}

```

## getColorByName

```TypeScript
getColorByName(resName: string): Promise<number>
```

获取指定资源名称对应的颜色值，使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回资源名称对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "test"仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getColorByName("test")
            .then((value: number) => {
                console.info(`getColorByName, result: ${value}`);
                // 打印输出结果: getColorByName, result: 4294967295
            })
            .catch((error: BusinessError) => {
                console.error(`promise getColorByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}

```

## getColorByNameSync

```TypeScript
getColorByNameSync(resName: string) : number
```

获取指定资源名称对应的颜色值，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 资源名称对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            let colorValue = this.context.resourceManager.getColorByNameSync("test");
            console.info(`getColorByNameSync, result: ${colorValue}`);
            // 打印输出结果: getColorByNameSync, result: 4294967295
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getColorByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getColorSync

```TypeScript
getColorSync(resId: number) : number
```

获取指定资源ID对应的颜色值，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 资源ID值对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.color.test'仅作示例，请替换为实际使用的资源
            let colorValue = this.context.resourceManager.getColorSync($r('app.color.test').id);
            console.info(`getColorSync, result: ${colorValue}`);
            // 打印输出结果: getColorSync, result: 4294967295
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getColorSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getColorSync

```TypeScript
getColorSync(resource: Resource) : number
```

获取指定resource对象对应的颜色值，使用同步方式返回。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getColorSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | resource对象对应的颜色值（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
try {
  let colorValue = this.context.resourceManager.getColorSync(resource);
  console.info(`getColorSync, result: ${colorValue}`);
  // 打印输出结果: getColorSync, result: 4294967295
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getColorSync failed, error code: ${code}, message: ${message}.`);
}

```

## getConfiguration

```TypeScript
getConfiguration(callback: _AsyncCallback<Configuration>): void
```

获取设备的Configuration，使用callback异步回调。

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | _AsyncCallback&lt;Configuration&gt; | 是 | 回调函数，返回设备的Configuration。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getConfiguration((error: BusinessError, config: resourceManager.Configuration) => {
                if (error != null) {
                    console.error("getConfiguration callback error is " + error);
                } else {
                    let direction = config.direction;
                    let locale = config.locale;
                }
            });
        } catch (error) {
            console.error("getConfiguration callback error is " + error);
        }
    }
}

```

## getConfiguration

```TypeScript
getConfiguration(): Promise<Configuration>
```

获取设备的Configuration，使用Promise异步回调。

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Configuration&gt; | Promise对象，返回设备的Configuration。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getConfiguration().then((config: resourceManager.Configuration) => {
                let direction = config.direction;
                let locale = config.locale;
            }).catch((error: BusinessError) => {
                console.error("getConfiguration promise error is " + error);
            });
        } catch (error) {
            console.error("getConfiguration promise error is " + error);
        }
    }
}

```

## getConfigurationSync

```TypeScript
getConfigurationSync(): Configuration
```

获取设备的Configuration，使用同步形式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Configuration | 设备的Configuration。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let value = this.context.resourceManager.getConfigurationSync();
            let direction = value.direction;
            let locale = value.locale;
        } catch (error) {
            console.error("getConfigurationSync error is " + error);
        }
    }
}

```

## getDeviceCapability

```TypeScript
getDeviceCapability(callback: _AsyncCallback<DeviceCapability>): void
```

获取设备的DeviceCapability，使用callback异步回调。

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | _AsyncCallback&lt;DeviceCapability&gt; | 是 | 回调函数，返回设备的DeviceCapability。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getDeviceCapability((error: BusinessError, value: resourceManager.DeviceCapability) => {
                if (error != null) {
                    console.error("getDeviceCapability callback error is " + error);
                } else {
                    let screenDensity = value.screenDensity;
                    let deviceType = value.deviceType;
                }
            });
        } catch (error) {
            console.error("getDeviceCapability callback error is " + error);
        }
    }
}

```

## getDeviceCapability

```TypeScript
getDeviceCapability(): Promise<DeviceCapability>
```

获取设备的DeviceCapability，使用Promise异步回调。

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DeviceCapability&gt; | Promise对象，返回设备的DeviceCapability。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getDeviceCapability().then((value: resourceManager.DeviceCapability) => {
                let screenDensity = value.screenDensity;
                let deviceType = value.deviceType;
            }).catch((error: BusinessError) => {
                console.error("getDeviceCapability promise error is " + error);
            });
        } catch (error) {
            console.error("getDeviceCapability promise error is " + error);
        }
    }
}

```

## getDeviceCapabilitySync

```TypeScript
getDeviceCapabilitySync(): DeviceCapability
```

获取设备的DeviceCapability，使用同步形式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DeviceCapability | 设备的DeviceCapability。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let value = this.context.resourceManager.getDeviceCapabilitySync();
            let screenDensity = value.screenDensity;
            let deviceType = value.deviceType;
        } catch (error) {
            console.error("getDeviceCapabilitySync error is " + error);
        }
    }
}

```

## getDoublePluralStringByNameSync

```TypeScript
getDoublePluralStringByNameSync(resName: string, num: number, ...args: Array<string | number>): string
```

获取指定资源名称对应的[单复数](../../../../internationalization/l10n-singular-plural.md)字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

> **说明**
>
> - 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。
>
> - 在英语、德语等语言中，单复数类型包括基数词（如1、2、3）和序数词（如1st、2nd、3rd），本接口仅支持在基数词类型下使用。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| num | number | 是 | 数量值（浮点数）。根据当前语言的[单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)获取该数量值对应的字符串。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源名称对应的格式化单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001008](../errorcode-resource-manager.md#9001008-根据当前名称获取的资源格式化失败) | Failed to format the resource obtained based on the resource name. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 根据语言单复数规则，参数num取值为2.1，英文环境下对应单复数类别为other
            // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为other的字符串
            // "format_test"仅作示例，请替换为实际使用的资源
            let pluralStr = this.context.resourceManager.getDoublePluralStringByNameSync("format_test", 2.1, 2, "basket", 0.6);
            console.info(`getDoublePluralStringByNameSync, result: ${pluralStr}`);
            // 打印输出结果: getDoublePluralStringByNameSync, result: There are 2 apples in the basket, the total amount is 0.6 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDoublePluralStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getDoublePluralStringValueSync

```TypeScript
getDoublePluralStringValueSync(resId: number, num: number, ...args: Array<string | number>): string
```

获取指定资源ID对应的[单复数](../../../../internationalization/l10n-singular-plural.md)字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

> **说明**
>
> - 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。
>
> - 在英语、德语等语言中，单复数类型包括基数词（如1、2、3）和序数词（如1st、2nd、3rd），本接口仅支持在基数词类型下使用。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值（浮点数）。根据当前语言的[单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)获取该数量值对应的字符串。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源ID值对应的格式化单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-根据当前id获取的资源格式化失败) | Failed to format the resource obtained based on the resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 根据语言单复数规则，参数num取值为2.1，英文环境下对应单复数类别为other
            // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为other的字符串
            // 'app.plural.format_test'仅作示例，请替换为实际使用的资源
            let pluralStr = this.context.resourceManager.getDoublePluralStringValueSync($r('app.plural.format_test').id, 2.1, 2, "basket", 0.6);
            console.info(`getDoublePluralStringValueSync, result: ${pluralStr}`);
            // 打印输出结果: getDoublePluralStringValueSync, result: There are 2 apples in the basket, the total amount is 0.6 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDoublePluralStringValueSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getDoublePluralStringValueSync

```TypeScript
getDoublePluralStringValueSync(resource: Resource, num: number, ...args: Array<string | number>): string
```

获取指定resource对象对应的[单复数](../../../../internationalization/l10n-singular-plural.md)字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** getDoublePluralStringValueSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| num | number | 是 | 数量值（浮点数）。根据当前语言的[单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)获取该数量值对应的字符串。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | resource对象对应的格式化单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-根据当前id获取的资源格式化失败) | Failed to format the resource obtained based on the resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.format_test').id
};

try {
  // 根据语言单复数规则，参数num取值为2.1，英文环境下对应单复数类别为other
  // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为other的字符串
  let pluralStr = this.context.resourceManager.getDoublePluralStringValueSync(resource, 2.1, 2, "basket", 0.6);
  console.info(`getDoublePluralStringValueSync, result: ${pluralStr}`);
  // 打印输出结果: getIntPluralStringValueSync, result: There are 2 apples in the basket, the total amount is 0.6 kg.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDoublePluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}

```

## getDrawableDescriptor

```TypeScript
getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor
```

获取指定资源ID对应的DrawableDescriptor对象，用于图标的显示，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |
| type | number | 否 | 图标类型。默认值为0。<br>0：表示获取应用自身图标资源。<br>1：表示获取主题资源包中应用的分层图标资源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DrawableDescriptor | 资源ID值对应的DrawableDescriptor对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DrawableDescriptor } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.icon'仅作示例，请替换为实际使用的资源
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor($r('app.media.icon').id);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // 'app.media.icon'仅作示例，请替换为实际使用的资源
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor($r('app.media.icon').id, 120);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // 'app.media.icon'仅作示例，请替换为实际使用的资源
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor($r('app.media.icon').id, 0, 1);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getDrawableDescriptor

```TypeScript
getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor
```

获取指定resource对应的DrawableDescriptor对象，用于图标的显示，使用同步方式返回。

> **说明**
>
> 从API version 10开始支持，从API version 20开始废弃，建议使用
> [getDrawableDescriptorByName](arkts-localization-resourcemanager-i.md#getdrawabledescriptorbyname-1)或
> [getDrawableDescriptor](arkts-localization-resourcemanager-i.md#getdrawabledescriptor-1)
> 替代。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getDrawableDescriptor(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |
| type | number | 否 | 图标类型。默认值为0。<br>0：表示获取应用自身图标资源。<br>1：表示获取主题资源包中应用的分层图标资源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DrawableDescriptor | 资源ID值对应的DrawableDescriptor对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DrawableDescriptor } from '@kit.ArkUI';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.icon').id
};
try {
  let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor(resource);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
}
try {
  let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor(resource, 120);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
}
try {
  let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor(resource, 0, 1);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
}

```

## getDrawableDescriptorByName

```TypeScript
getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor
```

获取指定资源名称对应的DrawableDescriptor对象，用于图标的显示，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |
| type | number | 否 | 图标类型。默认值为0。<br>0：表示获取应用自身图标资源。<br>1：表示获取主题资源包中应用的分层图标资源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DrawableDescriptor | 资源名称对应的DrawableDescriptor对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DrawableDescriptor } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "icon"仅作示例，请替换为实际使用的资源
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptorByName('icon');
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptorByName failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // "icon"仅作示例，请替换为实际使用的资源
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptorByName('icon', 120);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptorByName failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // "icon"仅作示例，请替换为实际使用的资源
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptorByName('icon', 0, 1);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptorByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getIntPluralStringByNameSync

```TypeScript
getIntPluralStringByNameSync(resName: string, num: number, ...args: Array<string | number>): string
```

获取指定资源名称对应的[单复数](../../../../internationalization/l10n-singular-plural.md)字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

> **说明**
>
> - 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。
>
> - 在英语、德语等语言中，单复数类型包括基数词（如1、2、3）和序数词（如1st、2nd、3rd），本接口仅支持在基数词类型下使用。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| num | number | 是 | 数量值（整数）。根据当前语言的[单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)获取该数量值对应的字符串。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源名称对应的格式化单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001008](../errorcode-resource-manager.md#9001008-根据当前名称获取的资源格式化失败) | Failed to format the resource obtained based on the resource name. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
            // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
            // "format_test"仅作示例，请替换为实际使用的资源
            let pluralStr = this.context.resourceManager.getIntPluralStringByNameSync("format_test", 1, 1, "basket", 0.3);
            console.info(`getIntPluralStringByNameSync, result: ${pluralStr}`);
            // 打印输出结果: getIntPluralStringByNameSync, result: There is 1 apple in the basket, the total amount is 0.3 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getIntPluralStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getIntPluralStringValueSync

```TypeScript
getIntPluralStringValueSync(resId: number, num: number,...args: Array<string | number>): string
```

获取指定资源ID对应的[单复数](../../../../internationalization/l10n-singular-plural.md)字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

> **说明**
>
> - 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。
>
> - 在英语、德语等语言中，单复数类型包括基数词（如1、2、3）和序数词（如1st、2nd、3rd），本接口仅支持在基数词类型下使用。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值（整数）。根据当前语言的[单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)获取该数量值对应的字符串。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源ID值对应的格式化单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-根据当前id获取的资源格式化失败) | Failed to format the resource obtained based on the resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
            // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
            // 'app.plural.format_test'仅作示例，请替换为实际使用的资源
            let pluralStr = this.context.resourceManager.getIntPluralStringValueSync($r('app.plural.format_test').id, 1, 1, "basket", 0.3);
            console.info(`getIntPluralStringValueSync, result: ${pluralStr}`);
            // 打印输出结果: getIntPluralStringValueSync, result: There is 1 apple in the basket, the total amount is 0.3 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getIntPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getIntPluralStringValueSync

```TypeScript
getIntPluralStringValueSync(resource: Resource, num: number, ...args: Array<string | number>): string
```

获取指定resource对象对应的[单复数](../../../../internationalization/l10n-singular-plural.md)字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** getIntPluralStringValueSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| num | number | 是 | 数量值（整数）。根据当前语言的[单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)获取该数量值对应的字符串。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | resource对象对应的格式化单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-根据当前id获取的资源格式化失败) | Failed to format the resource obtained based on the resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.format_test').id
};

try {
  // 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
  // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
  let pluralStr = this.context.resourceManager.getIntPluralStringValueSync(resource, 1, 1, "basket", 0.3);
  console.info(`getIntPluralStringValueSync, result: ${pluralStr}`);
  // 打印输出结果: getIntPluralStringValueSync, result: There is 1 apple in the basket, the total amount is 0.3 kg.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getIntPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}

```

## getLocales

```TypeScript
getLocales(includeSystem?: boolean): Array<string>
```

获取应用的语言列表。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| includeSystem | boolean | 否 | 是否包含系统资源，默认值为false。<br> - false：表示仅获取应用资源的语言列表。<br> - true：表示获取系统资源和应用资源的语言列表。<br>当使用系统资源管理对象获取语言列表时，includeSystem值无效，始终返回系统资源语言列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回获取的语言列表，列表中的字符串由语言、脚本（可选）、地区（可选），按照顺序使用中划线“-”连接组成。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getLocales(); // 仅获取应用资源语言列表
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getLocales failed, error code: ${code}, message: ${message}.`);
        }

        try {
            resourceManager.getSysResourceManager().getLocales(); // 仅获取系统资源语言列表
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getLocales failed, error code: ${code}, message: ${message}.`);
        }

        try {
            this.context.resourceManager.getLocales(true); // 获取应用资源和系统资源语言列表
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getLocales failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMedia

```TypeScript
getMedia(resId: number, callback: AsyncCallback<Uint8Array>): void
```

获取指定资源ID对应的媒体文件内容，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getMediaContent(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回资源ID值对应的媒体文件内容。 |

**示例：**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getMedia($r('app.media.test').id, (error: Error, value: Uint8Array) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let media = value;
        }
    });
});

```

## getMedia

```TypeScript
getMedia(resId: number): Promise<Uint8Array>
```

获取指定资源ID对应的媒体文件内容，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getMediaContent(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回资源ID值对应的媒体文件内容。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getMedia($r('app.media.test').id).then((value: Uint8Array) => {
        let media = value;
    }).catch((error: BusinessError) => {
        console.error("getMedia promise error is " + error);
    });
});

```

## getMediaBase64

```TypeScript
getMediaBase64(resId: number, callback: AsyncCallback<string>): void
```

获取指定资源ID对应的图片资源Base64编码，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getMediaContentBase64(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源ID值对应的图片资源Base64编码。 |

**示例：**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getMediaBase64($r('app.media.test').id, ((error: Error, value: string) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let media = value;
        }
    });
});

```

## getMediaBase64

```TypeScript
getMediaBase64(resId: number): Promise<string>
```

获取指定资源ID对应的图片资源Base64编码，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getMediaContentBase64(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的图片资源Base64编码。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getMediaBase64($r('app.media.test').id).then((value: string) => {
        let media = value;
    }).catch((error: BusinessError) => {
        console.error("getMediaBase64 promise error is " + error);
    });
});

```

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string, callback: _AsyncCallback<string>): void
```

获取指定资源名称对应的图片资源Base64编码，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源名称的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaBase64ByName("test", (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string, density: number, callback: _AsyncCallback<string>): void
```

获取指定资源名称对应的指定屏幕密度图片资源Base64编码，使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源名称的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaBase64ByName("test", 120, (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error(`callback getMediaBase64ByName failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string): Promise<string>
```

获取指定资源名称对应的图片资源Base64编码，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源名称对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaBase64ByName("test").then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaBase64ByName promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string, density: number): Promise<string>
```

获取指定资源名称对应的指定屏幕密度图片资源Base64编码，使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源名称对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaBase64ByName("test", 120).then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaBase64ByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaBase64ByNameSync

```TypeScript
getMediaBase64ByNameSync(resName: string, density?: number): string
```

获取指定资源名称对应的默认或指定的屏幕密度图片资源Base64编码，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源名称对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaBase64ByNameSync("test"); // 默认屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaBase64ByNameSync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaBase64ByNameSync("test", 120); // 指定屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaBase64ByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaByName

```TypeScript
getMediaByName(resName: string, callback: _AsyncCallback<Uint8Array>): void
```

获取指定资源名称对应的媒体文件内容，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回资源名称对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaByName("test", (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaByName

```TypeScript
getMediaByName(resName: string, density: number, callback: _AsyncCallback<Uint8Array>): void
```

获取指定资源名称对应的指定屏幕密度媒体文件内容，使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回资源名称对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaByName("test", 120, (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error(`callback getMediaByName failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaByName

```TypeScript
getMediaByName(resName: string): Promise<Uint8Array>
```

获取指定资源名称对应的媒体文件内容，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回资源名称对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaByName("test").then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaByName promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaByName

```TypeScript
getMediaByName(resName: string, density: number): Promise<Uint8Array>
```

获取指定资源名称对应的指定屏幕密度媒体文件内容，使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回资源名称对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaByName("test", 120).then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaByNameSync

```TypeScript
getMediaByNameSync(resName: string, density?: number): Uint8Array
```

获取指定资源名称对应的默认或指定的屏幕密度媒体文件内容，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 资源名称对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaByNameSync("test"); // 默认屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaByNameSync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // "test"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaByNameSync("test", 120); // 指定屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContent

```TypeScript
getMediaContent(resource: Resource, callback: _AsyncCallback<Uint8Array>): void
```

获取指定resource对象对应的媒体文件内容，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMediaContent(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回resource对象对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource, (error: BusinessError, value: Uint8Array) => {
    if (error != null) {
      console.error("error is " + error);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContent

```TypeScript
getMediaContent(resource: Resource, density: number, callback: _AsyncCallback<Uint8Array>): void
```

获取指定resource对象对应的指定屏幕密度媒体文件内容，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMediaContent(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回resource对象对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource, 120, (error: BusinessError, value: Uint8Array) => {
    if (error != null) {
      console.error(`callback getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContent

```TypeScript
getMediaContent(resource: Resource): Promise<Uint8Array>
```

获取指定resource对象对应的媒体文件内容，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMediaContent(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回resource对象对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource).then((value: Uint8Array) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error("getMediaContent promise error is " + error);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContent

```TypeScript
getMediaContent(resource: Resource, density: number): Promise<Uint8Array>
```

获取指定resource对象对应的指定屏幕密度媒体文件内容，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMediaContent(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回resource对象对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource, 120).then((value: Uint8Array) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error(`promise getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContent

```TypeScript
getMediaContent(resId: number, callback: _AsyncCallback<Uint8Array>): void
```

获取指定资源ID对应的媒体文件内容，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回资源ID对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContent($r('app.media.test').id,
                (error: BusinessError, value: Uint8Array) => {
                    if (error != null) {
                        console.error("error is " + error);
                    } else {
                        let media = value;
                    }
                });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContent

```TypeScript
getMediaContent(resId: number, density: number, callback: _AsyncCallback<Uint8Array>): void
```

获取指定资源ID对应的指定屏幕密度媒体文件内容，使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回资源ID对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContent($r('app.media.test').id, 120, (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error(`callback getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContent

```TypeScript
getMediaContent(resId: number): Promise<Uint8Array>
```

获取指定资源ID对应的媒体文件内容，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回资源ID值对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContent($r('app.media.test').id).then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaContent promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContent

```TypeScript
getMediaContent(resId: number, density: number): Promise<Uint8Array>
```

获取指定资源ID对应的指定屏幕密度媒体文件内容，使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回资源ID值对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContent($r('app.media.test').id, 120).then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource, callback: _AsyncCallback<string>): void
```

获取指定resource对象对应的图片资源Base64编码，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMediaContentBase64(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回resource对象对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource, (error: BusinessError, value: string) => {
    if (error != null) {
      console.error("error is " + error);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource, density: number, callback: _AsyncCallback<string>): void
```

获取指定resource对象对应的指定屏幕密度图片资源Base64编码，使用callback异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMediaContentBase64(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回resource对象对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource, 120, (error: BusinessError, value: string) => {
    if (error != null) {
      console.error(`callback getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource): Promise<string>
```

获取指定resource对象对应的图片资源Base64编码，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getMediaContentBase64(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回resource对象对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource).then((value: string) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error("getMediaContentBase64 promise error is " + error);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource, density: number): Promise<string>
```

获取指定resource对象对应的指定屏幕密度图片资源Base64编码，使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMediaContentBase64(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回resource对象对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource, 120).then((value: string) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error(`promise getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number, callback: _AsyncCallback<string>): void
```

获取指定资源ID对应的图片资源Base64编码，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源ID值对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id, (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number, density: number, callback: _AsyncCallback<string>): void
```

获取指定资源ID对应的指定屏幕密度图片资源Base64编码，使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源ID值对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id, 120, (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error(`callback getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number): Promise<string>
```

获取指定资源ID对应的图片资源Base64编码，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id).then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaContentBase64 promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number, density: number): Promise<string>
```

获取指定资源ID对应的指定屏幕密度图片资源Base64编码，使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 是 | 资源获取需要的屏幕密度，0表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id, 120).then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentBase64Sync

```TypeScript
getMediaContentBase64Sync(resId: number, density?: number): string
```

获取指定资源ID对应的默认或指定的屏幕密度图片资源Base64编码，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源ID对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentBase64Sync($r('app.media.test').id); // 默认屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentBase64Sync($r('app.media.test').id, 120); // 指定屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentBase64Sync

```TypeScript
getMediaContentBase64Sync(resource: Resource, density?: number): string
```

获取指定resource对象对应的默认或指定的屏幕密度图片资源Base64编码，使用同步方式返回。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMediaContentBase64Sync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | resource对象对应的图片资源Base64编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64Sync(resource); // 默认屏幕密度
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
}

try {
  this.context.resourceManager.getMediaContentBase64Sync(resource, 120); // 指定屏幕密度
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
}

```

## getMediaContentSync

```TypeScript
getMediaContentSync(resId: number, density?: number): Uint8Array
```

获取指定资源ID对应的默认或指定的屏幕密度媒体文件内容，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 资源ID对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Incorrect parameter types;2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentSync($r('app.media.test').id); // 默认屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // 'app.media.test'仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getMediaContentSync($r('app.media.test').id, 120); // 指定屏幕密度
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getMediaContentSync

```TypeScript
getMediaContentSync(resource: Resource, density?: number): Uint8Array
```

获取指定resource对象对应的默认或指定的屏幕密度媒体文件内容，使用同步方式返回。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getMediaContentSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| density | number | 否 | 资源获取需要的屏幕密度，0或缺省表示默认屏幕密度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | resource对象对应的媒体文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentSync(resource); // 默认屏幕密度
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
}

try {
  this.context.resourceManager.getMediaContentSync(resource, 120); // 指定屏幕密度
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
}

```

## getNumber

```TypeScript
getNumber(resId: number): number
```

获取指定资源ID对应的integer数值或者float数值，使用同步方式返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 资源ID值对应的数值。integer对应的是原数值，float不带单位时对应的是原数值，带"vp","fp"单位时对应的是px值，具体参考示例代码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/integer.json
{
  "integer": [
    {
      "name": "integer_test",
      "value": 100
    }
  ]
}

```

```TypeScript
// 资源文件路径: src/main/resources/base/element/float.json
{
  "float": [
    {
      "name": "float_test",
      "value": "30.6vp"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // integer对应返回的是原数值
            // 'app.integer.integer_test'仅作示例，请替换为实际使用的资源
            let intValue = this.context.resourceManager.getNumber($r('app.integer.integer_test').id);
            console.info(`getNumber, int value: ${intValue}`);
            // 打印输出结果: getNumber, int value: 100
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumber failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // float对应返回的是真实像素点值，带"vp","fp"单位的像素值 = 原数值 * densityPixels
            // 'app.float.float_test'仅作示例，请替换为实际使用的资源
            let floatValue = this.context.resourceManager.getNumber($r('app.float.float_test').id);
            console.info(`getNumber, densityPixels: ${display.getDefaultDisplaySync().densityPixels}, float value: ${floatValue}`);
            // 打印输出结果: getNumber, densityPixels: 3.25, float value: 99.45000457763672
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumber failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getNumber

```TypeScript
getNumber(resource: Resource): number
```

获取指定resource对象对应的integer数值或者float数值，使用同步方式返回。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getNumber(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | resource对象对应的数值。integer对应的是原数值，float不带单位时对应的是原数值，带"vp","fp"单位时对应的是px值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/integer.json
{
  "integer": [
    {
      "name": "integer_test",
      "value": 100
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.integer.integer_test').id
};

try {
  let intValue = this.context.resourceManager.getNumber(resource);
  console.info(`getNumber, int value: ${intValue}`);
  // 打印输出结果: getNumber, int value: 100
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getNumber failed, error code: ${code}, message: ${message}.`);
}

```

## getNumberByName

```TypeScript
getNumberByName(resName: string): number
```

获取指定资源名称对应的integer数值或者float数值，使用同步方式返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 资源名称对应的数值。integer对应的是原数值，float不带单位时对应的是原数值，带"vp","fp"单位时对应的是px值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/integer.json
{
  "integer": [
    {
      "name": "integer_test",
      "value": 100
    }
  ]
}

```

```TypeScript
// 资源文件路径: src/main/resources/base/element/float.json
{
  "float": [
    {
      "name": "float_test",
      "value": "30.6vp"
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // integer对应返回的是原数值
            // "integer_test"仅作示例，请替换为实际使用的资源
            let intValue = this.context.resourceManager.getNumberByName("integer_test");
            console.info(`getNumberByName, int value: ${intValue}`);
            // 打印输出结果: getNumberByName, int value: 100
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumberByName failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // float对应返回的是真实像素点值，带"vp","fp"单位的像素值 = 原数值 * densityPixels
            // "float_test"仅作示例，请替换为实际使用的资源
            let floatValue = this.context.resourceManager.getNumberByName("float_test");
            console.info(`getNumberByName, densityPixels: ${display.getDefaultDisplaySync().densityPixels}, float value: ${floatValue}`);
            // 打印输出结果: getNumberByName, densityPixels: 3.25, float value: 99.45000457763672
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumberByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getOverrideConfiguration

```TypeScript
getOverrideConfiguration(): Configuration
```

获取差异化资源的配置，使用同步方式返回。普通资源管理对象与通过它的
[getOverrideResourceManager](arkts-localization-resourcemanager-i.md#getoverrideresourcemanager-1)接口获取的差异化资源管理对象调用该方法
可获得相同的返回值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Configuration | 差异化资源的配置。 |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let resMgr = this.context.resourceManager;
            let overrideConfig = resMgr.getOverrideConfiguration();
            overrideConfig.colorMode = resourceManager.ColorMode.DARK;
            let overrideResMgr = resMgr.getOverrideResourceManager(overrideConfig);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getOverrideResourceManager failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getOverrideResourceManager

```TypeScript
getOverrideResourceManager(configuration?: Configuration): ResourceManager
```

获取可以加载差异化资源的资源管理对象，使用同步方式返回。
普通的资源管理对象获取的资源的配置（语言、深浅色、分辨率、横竖屏等）是由系统决定的，而通过该接口返回的对象，应用可以获取符合指定配置的资源，即差异化资源，比如在浅色模式时可以获取深色资源。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | Configuration | 否 | 指定想要获取的资源配置。<br>通过[getOverrideConfiguration](arkts-localization-resourcemanager-i.md#getoverrideconfiguration-1)获取差异化配置后，根据需求修改配置项，再作为参数传入该函数。<br>若缺省则表示使用当前系统的configuration。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ResourceManager | 可以加载差异化资源的资源管理对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let resMgr = this.context.resourceManager;
            let overrideConfig = resMgr.getOverrideConfiguration();
            overrideConfig.colorMode = resourceManager.ColorMode.DARK;
            let overrideResMgr = resMgr.getOverrideResourceManager(overrideConfig);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getOverrideResourceManager failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getPluralString

```TypeScript
getPluralString(resId: number, num: number, callback: AsyncCallback<string>): void
```

获取指定资源ID，指定资源数量的单复数字符串，使用callback异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getPluralStringValue(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源ID值对应的指定数量的单复数字符串。 |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getPluralString($r("app.plural.test").id, 1, (error: Error, value: string) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let str = value;
        }
    });
});

```

## getPluralString

```TypeScript
getPluralString(resId: number, num: number): Promise<string>
```

获取指定资源ID，指定资源数量的单复数字符串，使用Promise异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getPluralStringValue(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的指定数量的单复数字符串。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getPluralString($r("app.plural.test").id, 1).then((value: string) => {
        let str = value;
    }).catch((error: BusinessError) => {
        console.error("getPluralString promise error is " + error);
    });
});

```

## getPluralStringByName

```TypeScript
getPluralStringByName(resName: string, num: number, callback: _AsyncCallback<string>): void
```

获取指定资源名称，指定资源数量的单复数字符串，使用callback异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** getIntPluralStringByNameSync(resName:

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源名称对应的指定数量的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
// 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
this.context.resourceManager.getPluralStringByName("test", 1, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getPluralStringByName failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getPluralStringByName, result: ${value}`);
    // 打印输出结果: getPluralStringByName, result: 1 apple
  }
});

```

## getPluralStringByName

```TypeScript
getPluralStringByName(resName: string, num: number): Promise<string>
```

获取指定资源名称，指定资源数量的单复数字符串，使用Promise异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** getIntPluralStringByNameSync(resName:

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 根据传入的数量值，获取资源名称对应的字符串资源。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
// 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
this.context.resourceManager.getPluralStringByName("test", 1)
  .then((value: string) => {
    console.info(`getPluralStringByName, result: ${value}`);
    // 打印输出结果: getPluralStringByName, result: 1 apple
  })
  .catch((error: BusinessError) => {
    console.error(`promise getPluralStringByName failed, error code: ${error.code}, message: ${error.message}.`);
  });

```

## getPluralStringByNameSync

```TypeScript
getPluralStringByNameSync(resName: string, num: number): string
```

获取指定资源名称，指定资源数量的单复数字符串，使用同步方式返回。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getIntPluralStringByNameSync(resName:

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 根据指定数量获取指定资源名称表示的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
  // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
  let pluralValue = this.context.resourceManager.getPluralStringByNameSync("test", 1);
  console.info(`getPluralStringByNameSync, result: ${pluralValue}`);
  // 打印输出结果: getPluralStringByNameSync, result: 1 apple
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getPluralStringByNameSync failed, error code: ${code}, message: ${message}.`);
}

```

## getPluralStringValue

```TypeScript
getPluralStringValue(resource: Resource, num: number, callback: _AsyncCallback<string>): void
```

获取指定资源信息，指定资源数量的单复数字符串，使用callback异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** getIntPluralStringValueSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回resource对象对应的指定数量的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.test').id
};
// 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
// 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
this.context.resourceManager.getPluralStringValue(resource, 1,
  (error: BusinessError, value: string) => {
    if (error != null) {
      console.error(`callback getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      console.info(`getPluralStringValue, result: ${value}`);
      // 打印输出结果: getPluralStringValue, result: 1 apple
    }
  });

```

## getPluralStringValue

```TypeScript
getPluralStringValue(resource: Resource, num: number): Promise<string>
```

获取指定资源信息，指定资源数量的单复数字符串，使用Promise异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** getIntPluralStringValueSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回resource对象对应的指定数量的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.test').id
};
// 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
// 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
this.context.resourceManager.getPluralStringValue(resource, 1)
  .then((value: string) => {
    console.info(`getPluralStringValue, result: ${value}`);
    // 打印输出结果: getPluralStringValue, result: 1 apple
  })
  .catch((error: BusinessError) => {
    console.error(`promise getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  });

```

## getPluralStringValue

```TypeScript
getPluralStringValue(resId: number, num: number, callback: _AsyncCallback<string>): void
```

获取指定资源ID，指定资源数量的单复数字符串，使用callback异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** getIntPluralStringValueSync(resId:

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源ID值对应的指定数量的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
// 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
this.context.resourceManager.getPluralStringValue($r("app.plural.test").id, 1,
  (error: BusinessError, value: string) => {
    if (error != null) {
      console.error(`callback getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      console.info(`getPluralStringValue, result: ${value}`);
      // 打印输出结果: getPluralStringValue, result: 1 apple
    }
  });

```

## getPluralStringValue

```TypeScript
getPluralStringValue(resId: number, num: number): Promise<string>
```

获取指定资源ID，指定资源数量的单复数字符串，使用Promise异步回调。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** getIntPluralStringValueSync(resId:

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的指定数量的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
// 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
this.context.resourceManager.getPluralStringValue($r("app.plural.test").id, 1)
  .then((value: string) => {
    console.info(`getPluralStringValue, result: ${value}`);
    // 打印输出结果: getPluralStringValue, result: 1 apple
  })
  .catch((error: BusinessError) => {
    console.error(`promise getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  });

```

## getPluralStringValueSync

```TypeScript
getPluralStringValueSync(resId: number, num: number): string
```

获取指定资源ID，指定资源数量的单复数字符串，使用同步方式返回。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getIntPluralStringValueSync(resId:

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 根据指定数量获取指定ID字符串表示的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
  // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
  let pluralValue = this.context.resourceManager.getPluralStringValueSync($r('app.plural.test').id, 1);
  console.info(`getPluralStringValueSync, result: ${pluralValue}`);
  // 打印输出结果: getPluralStringValueSync, result: 1 apple
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}

```

## getPluralStringValueSync

```TypeScript
getPluralStringValueSync(resource: Resource, num: number): string
```

获取指定资源信息，指定资源数量的单复数字符串，使用同步方式返回。

> **说明**
>
> 中文环境下，字符串不区分单复数；其他语言环境下，字符串区分单复数，具体规则参考
> [语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getIntPluralStringValueSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| num | number | 是 | 数量值。根据当前语言的复数规则获取该数量值对应的字符串数字，语言的复数规则参见[语言单复数规则](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 根据指定数量获取指定resource对象表示的单复数字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.test').id
};
try {
  // 根据语言单复数规则，参数num取值为1，英文环境下对应单复数类别为one
  // 在资源文件中用quantity字段表示单复数类别，因此会获取quantity为one的字符串
  let pluralValue = this.context.resourceManager.getPluralStringValueSync(resource, 1);
  console.info(`getPluralStringValueSync, result: ${pluralValue}`);
  // 打印输出结果: getPluralStringValueSync, result: 1 apple
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}

```

## getRawFd

```TypeScript
getRawFd(path: string, callback: _AsyncCallback<RawFileDescriptor>): void
```

获取resources/rawfile目录下对应rawfile文件所在HAP的文件描述符（fd），使用callback异步回调。

> **说明**
>
> 文件描述符（fd）使用完毕后需调用[closeRawFdSync](arkts-localization-resourcemanager-i.md#closerawfdsync-1)或
> [closeRawFd](arkts-localization-resourcemanager-i.md#closerawfd-1)关闭
> fd，避免资源泄露。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |
| callback | _AsyncCallback&lt;RawFileDescriptor&gt; | 是 | 回调函数，返回的rawfile文件所在HAP的文件描述符（fd）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test.txt"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getRawFd("test.txt", (error: BusinessError, value: resourceManager.RawFileDescriptor) => {
                if (error != null) {
                    console.error(`callback getRawFd failed error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let fd = value.fd;
                    let offset = value.offset;
                    let length = value.length;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getRawFd failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getRawFd

```TypeScript
getRawFd(path: string): Promise<RawFileDescriptor>
```

获取resources/rawfile目录下rawfile文件所在HAP的文件描述符（fd），使用Promise异步回调。

> **说明**
>
> 文件描述符（fd）使用完毕后需调用[closeRawFdSync](arkts-localization-resourcemanager-i.md#closerawfdsync-1)或
> [closeRawFd](arkts-localization-resourcemanager-i.md#closerawfd-1)关闭
> fd，避免资源泄露。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RawFileDescriptor&gt; | Promise对象，返回rawfile文件所在HAP的文件描述符（fd）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test.txt"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getRawFd("test.txt").then((value: resourceManager.RawFileDescriptor) => {
                let fd = value.fd;
                let offset = value.offset;
                let length = value.length;
            }).catch((error: BusinessError) => {
                console.error(`promise getRawFd error error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getRawFd failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getRawFdSync

```TypeScript
getRawFdSync(path: string): RawFileDescriptor
```

获取resources/rawfile目录下rawfile文件所在HAP的文件描述符（fd），使用同步方式返回。

> **说明**
>
> 文件描述符（fd）使用完毕后需调用[closeRawFdSync](arkts-localization-resourcemanager-i.md#closerawfdsync-1)或
> [closeRawFd](arkts-localization-resourcemanager-i.md#closerawfd-1)关闭
> fd，避免资源泄露。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RawFileDescriptor | rawfile文件所在HAP的文件描述符（fd）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test.txt"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getRawFdSync("test.txt");
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getRawFdSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getRawFile

```TypeScript
getRawFile(path: string, callback: AsyncCallback<Uint8Array>): void
```

获取resources/rawfile目录下对应的rawfile文件内容，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getRawFileContent(path:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |
| callback | AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回rawfile文件内容。 |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFile("test.txt", (error: Error, value: Uint8Array) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let rawFile = value;
        }
    });
});

```

## getRawFile

```TypeScript
getRawFile(path: string): Promise<Uint8Array>
```

获取resources/rawfile目录下对应的rawfile文件内容，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getRawFileContent(path:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回rawfile文件内容。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFile("test.txt").then((value: Uint8Array) => {
        let rawFile = value;
    }).catch((error: BusinessError) => {
        console.error("getRawFile promise error is " + error);
    });
});

```

## getRawFileContent

```TypeScript
getRawFileContent(path: string, callback: _AsyncCallback<Uint8Array>): void
```

获取resources/rawfile目录下对应的rawfile文件内容，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |
| callback | _AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数，返回获取的rawfile文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test.txt"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getRawFileContent("test.txt", (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let rawFile = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getRawFileContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getRawFileContent

```TypeScript
getRawFileContent(path: string): Promise<Uint8Array>
```

获取resources/rawfile目录下对应的rawfile文件内容，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回获取的rawfile文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test.txt"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getRawFileContent("test.txt").then((value: Uint8Array) => {
                let rawFile = value;
            }).catch((error: BusinessError) => {
                console.error("getRawFileContent promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getRawFileContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getRawFileContentSync

```TypeScript
getRawFileContentSync(path: string): Uint8Array
```

获取resources/rawfile目录下对应的rawfile文件内容，使用同步形式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回获取的rawfile文件内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test.txt"仅作示例，请替换为实际使用的资源
            this.context.resourceManager.getRawFileContentSync("test.txt");
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getRawFileContentSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getRawFileDescriptor

```TypeScript
getRawFileDescriptor(path: string, callback: AsyncCallback<RawFileDescriptor>): void
```

获取resources/rawfile目录下对应rawfile文件的文件描述符（fd），使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getRawFd(path:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |
| callback | AsyncCallback&lt;RawFileDescriptor&gt; | 是 | 回调函数，返回rawfile文件的文件描述符（fd）。 |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFileDescriptor("test.txt", (error: Error, value: resourceManager.RawFileDescriptor) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let fd = value.fd;
            let offset = value.offset;
            let length = value.length;
        }
    });
});

```

## getRawFileDescriptor

```TypeScript
getRawFileDescriptor(path: string): Promise<RawFileDescriptor>
```

获取resources/rawfile目录下对应rawfile文件的文件描述符（fd），使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getRawFd(path:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RawFileDescriptor&gt; | Promise对象，返回rawfile文件的文件描述符（fd）。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFileDescriptor("test.txt").then((value: resourceManager.RawFileDescriptor) => {
        let fd = value.fd;
        let offset = value.offset;
        let length = value.length;
    }).catch((error: BusinessError) => {
        console.error("getRawFileDescriptor promise error is " + error);
    });
});

```

## getRawFileList

```TypeScript
getRawFileList(path: string, callback: _AsyncCallback<Array<string>>): void
```

获取resources/rawfile目录下文件夹及文件列表，使用callback异步回调。

> **说明**
>
> 若文件夹中无文件，则抛出异常；若文件夹中有文件，则返回文件夹及文件列表。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件夹路径。 |
| callback | _AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回rawfile文件目录下的文件夹及文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // 传入""表示获取rawfile根目录下的文件列表，假设rawfile根目录下存在test.txt文件
        // 传入""仅作示例，请替换为rawfile目录下实际的文件路径
        this.context.resourceManager.getRawFileList("", (error: BusinessError, value: Array<string>) => {
            if (error != null) {
                console.error(`callback getRawFileList failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                console.info(`getRawFileList, result: ${JSON.stringify(value)}`);
                // 打印输出结果: getRawFileList, result: ["test.txt"]
            }
        });
    }
}

```

## getRawFileList

```TypeScript
getRawFileList(path: string): Promise<Array<string>>
```

获取resources/rawfile目录下文件夹及文件列表，使用Promise异步回调。

> **说明**
>
> 若文件夹中无文件，则抛出异常；若文件夹中有文件，则返回文件夹及文件列表。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件夹路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回rawfile文件目录下的文件夹及文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // 传入""表示获取rawfile根目录下的文件列表，假设rawfile根目录下存在test.txt文件
        // 传入""仅作示例，请替换为rawfile目录下实际的文件路径
        this.context.resourceManager.getRawFileList("")
            .then((value: Array<string>) => {
                console.info(`getRawFileList, result: ${JSON.stringify(value)}`);
                // 打印输出结果: getRawFileList, result: ["test.txt"]
            })
            .catch((error: BusinessError) => {
                console.error(`promise getRawFileList failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}

```

## getRawFileListSync

```TypeScript
getRawFileListSync(path: string): Array<string>
```

获取resources/rawfile目录下文件夹及文件列表，使用同步形式返回。

> **说明**
>
> 若文件夹中无文件，则抛出异常；若文件夹中有文件，则返回文件夹及文件列表。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile文件夹路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | rawfile文件目录下的文件夹及文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 传入""表示获取rawfile根目录下的文件列表，假设rawfile根目录下存在test.txt文件
            // 传入""仅作示例，请替换为rawfile目录下实际的文件路径
            let fileList: Array<string> = this.context.resourceManager.getRawFileListSync("");
            console.info(`getRawFileListSync, result: ${JSON.stringify(fileList)}`);
            // 打印输出结果: getRawFileListSync, result: ["test.txt"] 
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getRawFileListSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getResourceName

```TypeScript
getResourceName(resId: number): string
```

获取指定资源ID对应的资源名称。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源ID值对应的资源名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.string.test'仅作示例，请替换为实际使用的资源
            let resName: string = this.context.resourceManager.getResourceName($r('app.string.test').id);
            console.info(`getResourceName, result: ${resName}`);
            // 打印输出结果: getResourceName, result: test
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getResourceName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getString

```TypeScript
getString(resId: number, callback: AsyncCallback<string>): void
```

获取指定资源ID对应的字符串，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getStringValue(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回资源ID值对应的字符串。 |

**示例：**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getString($r('app.string.test').id, (error: Error, value: string) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let str = value;
        }
    });
});

```

## getString

```TypeScript
getString(resId: number): Promise<string>
```

获取指定资源ID对应的字符串，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getStringValue(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的字符串。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getString($r('app.string.test').id).then((value: string) => {
        let str = value;
    }).catch((error: BusinessError) => {
        console.error("getstring promise error is " + error);
    });
});

```

## getStringArray

```TypeScript
getStringArray(resId: number, callback: AsyncCallback<Array<string>>): void
```

获取指定资源ID对应的字符串数组，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getStringArrayValue(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回资源ID值对应的字符串数组。 |

**示例：**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getStringArray($r('app.strarray.test').id, (error: Error, value: Array<string>) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let strArray = value;
        }
    });
});

```

## getStringArray

```TypeScript
getStringArray(resId: number): Promise<Array<string>>
```

获取指定资源ID对应的字符串数组，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getStringArrayValue(resId:

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回资源ID值对应的字符串数组。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
      mgr.getStringArray($r('app.strarray.test').id).then((value: Array<string>) => {
        let strArray = value;
    }).catch((error: BusinessError) => {
        console.error("getStringArray promise error is " + error);
    });
});

```

## getStringArrayByName

```TypeScript
getStringArrayByName(resName: string, callback: _AsyncCallback<Array<string>>): void
```

获取指定资源名称对应的字符串数组，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| callback | _AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回资源名称对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "test"仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringArrayByName("test", (error: BusinessError, value: Array<string>) => {
            if (error != null) {
                console.error(`callback getStringArrayByName failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                let strArray = value;
                console.info(`getStringArrayByName, result: ${value[0]}`);
                // 打印输出结果: getStringArrayByName, result: I'm one of the array's values.
            }
        });
    }
}

```

## getStringArrayByName

```TypeScript
getStringArrayByName(resName: string): Promise<Array<string>>
```

获取指定资源名称对应的字符串数组，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回资源名称对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "test"仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringArrayByName("test")
            .then((value: Array<string>) => {
                console.info(`getStringArrayByName, result: ${value[0]}`);
                // 打印输出结果: getStringArrayByName, result: I'm one of the array's values.
            })
            .catch((error: BusinessError) => {
                console.error(`promise getStringArrayByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}

```

## getStringArrayByNameSync

```TypeScript
getStringArrayByNameSync(resName: string): Array<string>
```

获取指定资源名称对应的字符串数组，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 对应资源名称的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            let strArray: Array<string> = this.context.resourceManager.getStringArrayByNameSync("test");
            console.info(`getStringArrayByNameSync, result: ${strArray[0]}`);
            // 打印输出结果: getStringArrayByNameSync, result: I'm one of the array's values.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringArrayByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getStringArrayValue

```TypeScript
getStringArrayValue(resource: Resource, callback: _AsyncCallback<Array<string>>): void
```

获取指定resource对象对应的字符串数组，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getStringArrayValue(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| callback | _AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回resource对象对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.strarray.test').id
};
this.context.resourceManager.getStringArrayValue(resource, (error: BusinessError, value: Array<string>) => {
  if (error != null) {
    console.error(`callback getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringArrayValue, result: ${value[0]}`);
    // 打印输出结果: getStringArrayValue, result: I'm one of the array's values.
  }
});

```

## getStringArrayValue

```TypeScript
getStringArrayValue(resource: Resource): Promise<Array<string>>
```

获取指定resource对象对应的字符串数组，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getStringArrayValue(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回resource对象对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.strarray.test').id
};
this.context.resourceManager.getStringArrayValue(resource)
  .then((value: Array<string>) => {
    console.info(`getStringArrayValue, result: ${value[0]}`);
    // 打印输出结果: getStringArrayValue, result: I'm one of the array's values.
  })
  .catch((error: BusinessError) => {
    console.error(`promise getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
  });

```

## getStringArrayValue

```TypeScript
getStringArrayValue(resId: number, callback: _AsyncCallback<Array<string>>): void
```

获取指定资源ID对应的字符串数组，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | _AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回资源ID值对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // 'app.strarray.test'仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringArrayValue($r('app.strarray.test').id,
            (error: BusinessError, value: Array<string>) => {
                if (error != null) {
                    console.error(`callback getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    console.info(`getStringArrayValue, result: ${value[0]}`);
                    // 打印输出结果: getStringArrayValue, result: I'm one of the array's values.
                }
            });
    }
}

```

## getStringArrayValue

```TypeScript
getStringArrayValue(resId: number): Promise<Array<string>>
```

获取指定资源ID对应的字符串数组，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回资源ID值对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // 'app.strarray.test'仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringArrayValue($r('app.strarray.test').id)
            .then((value: Array<string>) => {
                console.info(`getStringArrayValue, result: ${value[0]}`);
                // 打印输出结果: getStringArrayValue, result: I'm one of the array's values.
            })
            .catch((error: BusinessError) => {
                console.error(`promise getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}

```

## getStringArrayValueSync

```TypeScript
getStringArrayValueSync(resId: number): Array<string>
```

获取指定资源ID对应的字符串数组，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 资源ID值对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.strarray.test'仅作示例，请替换为实际使用的资源
            let strArray: Array<string> = this.context.resourceManager.getStringArrayValueSync($r('app.strarray.test').id);
            console.info(`getStringArrayValueSync, result: ${strArray[0]}`);
            // 打印输出结果: getStringArrayValueSync, result: I'm one of the array's values.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringArrayValueSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getStringArrayValueSync

```TypeScript
getStringArrayValueSync(resource: Resource): Array<string>
```

获取指定resource对象对应的字符串数组，使用同步方式返回。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getStringArrayValueSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | resource对象对应的字符串数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.strarray.test').id
};
try {
  let strArray: Array<string> = this.context.resourceManager.getStringArrayValueSync(resource);
  console.info(`getStringArrayValueSync, result: ${strArray[0]}`);
  // 打印输出结果: getStringArrayValueSync, result: I'm one of the array's values.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getStringArrayValueSync failed, error code: ${code}, message: ${message}.`);
}

```

## getStringByName

```TypeScript
getStringByName(resName: string, callback: _AsyncCallback<string>): void
```

获取指定资源名称对应的字符串，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 返回获取的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "test"仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringByName("test", (error: BusinessError, value: string) => {
            if (error != null) {
                console.error(`callback getStringByName failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                console.info(`getStringByName, result: ${value}`);
                // 打印输出结果: getStringByName, result: I'm a test string resource.
            }
        });
    }
}

```

## getStringByName

```TypeScript
getStringByName(resName: string): Promise<string>
```

获取指定资源名称对应的字符串，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源名称对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "test"仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringByName("test").then((value: string) => {
            console.info(`getStringByName, result: ${value}`);
            // 打印输出结果: getStringByName, result: I'm a test string resource.
        }).catch((error: BusinessError) => {
            console.error(`promise getStringByName failed, error code: ${error.code}, message: ${error.message}.`);
        });
    }
}

```

## getStringByNameSync

```TypeScript
getStringByNameSync(resName: string): string
```

获取指定资源名称对应的字符串，使用同步方式返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源名称对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            let testStr = this.context.resourceManager.getStringByNameSync("test");
            console.info(`getStringByNameSync, result: ${testStr}`);
            // 打印输出结果: getStringByNameSync, result: I'm a test string resource.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getStringByNameSync

```TypeScript
getStringByNameSync(resName: string, ...args: Array<string | number>): string
```

获取指定资源名称对应的字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001008](../errorcode-resource-manager.md#9001008-根据当前名称获取的资源格式化失败) | Failed to format the resource obtained based on the resource Name. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a %1$s, format int: %2$d, format float: %3$f."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "test"仅作示例，请替换为实际使用的资源
            let testStr = this.context.resourceManager.getStringByNameSync("test", "format string", 10, 98.78);
            console.info(`getStringByNameSync, result: ${testStr}`);
            // 打印输出结果: getStringByNameSync, result: I'm a format string, format int: 10, format float: 98.78.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getStringSync

```TypeScript
getStringSync(resId: number): string
```

获取指定资源ID对应的字符串，使用同步方式返回。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源ID值对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.string.test'仅作示例，请替换为实际使用的资源
            let testStr = this.context.resourceManager.getStringSync($r('app.string.test').id);
            console.info(`getStringSync, result: ${testStr}`);
            // 打印输出结果: getStringSync, result: I'm a test string resource.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getStringSync

```TypeScript
getStringSync(resId: number, ...args: Array<string | number>): string
```

获取指定资源ID对应的字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 资源ID值对应的格式化字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-根据当前id获取的资源格式化失败) | Failed to format the resource obtained based on the resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a %1$s, format int: %2$d, format float: %3$f."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'app.string.test'仅作示例，请替换为实际使用的资源
            let testStr = this.context.resourceManager.getStringSync($r('app.string.test').id, "format string", 10, 98.78);
            console.info(`getStringSync, result: ${testStr}`);
            // 打印输出结果: getStringSync, result: I'm a format string, format int: 10, format float: 98.78.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getStringSync

```TypeScript
getStringSync(resource: Resource): string
```

获取指定resource对象对应的字符串，使用同步方式返回。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getStringSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | resource对象对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
try {
  let testStr = this.context.resourceManager.getStringSync(resource);
  console.info(`getStringSync, result: ${testStr}`);
  // 打印输出结果: getStringSync, result: I'm a test string resource.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
}

```

## getStringSync

```TypeScript
getStringSync(resource: Resource, ...args: Array<string | number>): string
```

获取指定resource对象对应的字符串，并根据args参数对字符串进行格式化，使用同步方式返回。

**起始版本：** 10

**废弃版本：** 20

**替代接口：** getStringSync(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| args | Array&lt;string \| number&gt; | 是 | 格式化字符串资源参数。<br>支持参数类型：`%d`、`%f`、`%s`、`%%`、`%数字$d`、`%数字$f`、`%数字$s`。<br>说明：`%%`转义为`%`; `%数字$d`中的数字表示使用args中的第几个参数。<br>举例：`%%d`格式化后为`%d`字符串; `%1$d`表示使用第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | resource对象对应的格式化字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-根据当前id获取的资源格式化失败) | Failed to format the resource obtained based on the resource ID. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a %1$s, format int: %2$d, format float: %3$f."
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
try {
  let testStr = this.context.resourceManager.getStringSync(resource, "format string", 10, 98.78);
  console.info(`getStringSync, result: ${testStr}`);
  // 打印输出结果: getStringSync, result: I'm a format string, format int: 10, format float: 98.78.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
}

```

## getStringValue

```TypeScript
getStringValue(resource: Resource, callback: _AsyncCallback<string>): void
```

获取指定resource对象对应的字符串，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getStringValue(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回resource对象对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
this.context.resourceManager.getStringValue(resource, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringValue, result: ${value}`);
    // 打印输出结果: getStringValue, result: I'm a test string resource.
  }
});

```

## getStringValue

```TypeScript
getStringValue(resource: Resource): Promise<string>
```

获取指定resource对象对应的字符串，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 20

**替代接口：** getStringValue(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回resource对象对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
this.context.resourceManager.getStringValue(resource, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringValue, result: ${value}`);
    // 打印输出结果: getStringValue, result: I'm a test string resource.
  }
});

```

## getStringValue

```TypeScript
getStringValue(resId: number, callback: _AsyncCallback<string>): void
```

获取指定资源ID对应的字符串，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |
| callback | _AsyncCallback&lt;string&gt; | 是 | 回调函数，返回获取的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

## getStringValue

```TypeScript
getStringValue(resId: number): Promise<string>
```

获取指定资源ID对应的字符串，使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回资源ID值对应的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // 'app.string.test'仅作示例，请替换为实际使用的资源
        this.context.resourceManager.getStringValue($r('app.string.test').id).then((value: string) => {
            console.info(`getStringValue, result: ${value}`);
            // 打印输出结果: getStringValue, result: I'm a test string resource.
        }).catch((error: BusinessError) => {
            console.error(`promise getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
        });
    }
}

```

## getSymbol

```TypeScript
getSymbol(resId: number) : number
```

获取指定资源ID对应的[Symbol字符](https://developer.huawei.com/consumer/cn/design/harmonyos-symbol)Unicode码，使用同步方式返回。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resId | number | 是 | 资源ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 资源ID值对应的Symbol字符Unicode码（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 'sys.symbol.message'仅作示例，请替换为实际使用的资源
            let symbolValue = this.context.resourceManager.getSymbol($r('sys.symbol.message').id);
            console.info(`getSymbol, result: ${symbolValue}`);
            // 打印输出结果: getSymbol, result: 983183
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getSymbol failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## getSymbol

```TypeScript
getSymbol(resource: Resource) : number
```

获取指定resource对象对应的[Symbol字符](https://developer.huawei.com/consumer/cn/design/harmonyos-symbol)Unicode码，使用同步方式返回。

**起始版本：** 11

**废弃版本：** 20

**替代接口：** getSymbol(resId:

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | 资源信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | resource对象对应的Symbol字符Unicode码（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-无效的资源id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-根据当前资源id未找到匹配的资源) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('sys.symbol.message').id
};
try {
  let symbolValue = this.context.resourceManager.getSymbol(resource);
  console.info(`getSymbol, result: ${symbolValue}`);
  // 打印输出结果: getSymbol, result: 983183
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getSymbol failed, error code: ${code}, message: ${message}.`);
}

```

## getSymbolByName

```TypeScript
getSymbolByName(resName: string) : number
```

获取指定资源名称对应的[Symbol字符](https://developer.huawei.com/consumer/cn/design/harmonyos-symbol)Unicode码，使用同步方式返回。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resName | string | 是 | 资源名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 资源名称对应的Symbol字符Unicode码（十进制）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-无效的资源名称) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-根据当前资源名称未找到匹配的资源) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-资源存在循环引用) | The resource is referenced cyclically. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // "message"仅作示例，请替换为实际使用的资源
            let symbolValue = this.context.resourceManager.getSymbolByName("message");
            console.info(`getSymbolByName, result: ${symbolValue}`);
            // 打印输出结果: getSymbolByName, result: 983183
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getSymbolByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## isRawDir

```TypeScript
isRawDir(path: string): boolean
```

判断指定路径是否为rawfile下的目录，使用同步方式返回。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | rawfile路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否为rawfile下的目录。- true：表示是rawfile下的目录。- false：表示非rawfile下的目录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-无效的相对路径) | Invalid relative path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // 假设rawfile根目录下存在非空文件夹sub，则isRawDir返回结果为true
            // "sub"仅作示例，请替换为实际使用的目录名称
            let isRawDir = this.context.resourceManager.isRawDir("sub");
            // 打印输出结果: sub isRawDir, result: true
            console.info(`sub isRawDir, result: ${isRawDir}`);

            // 假设rawfile根目录下存在test.txt文件，则isRawDir返回结果为false
            // "test.txt"仅作示例，请替换为实际使用的资源
            isRawDir = this.context.resourceManager.isRawDir("test.txt");
            // 打印输出结果: test.txt isRawDir, result: false
            console.info(`test.txt isRawDir, result: ${isRawDir}`);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`isRawDir failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## release

```TypeScript
release()
```

释放创建的resourceManager, 此接口暂不支持。

**起始版本：** 7

**废弃版本：** 12

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**示例：**

```TypeScript
try {
  this.context.resourceManager.release();
} catch (error) {
  console.error("release error is " + error);
}

```

## removeResource

```TypeScript
removeResource(path: string) : void
```

应用运行时移除指定的资源路径，还原被覆盖前的资源。

> **说明**
>
> rawfile和resfile目录不支持资源覆盖。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 资源路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |
| [9001010](../errorcode-resource-manager.md#9001010-无效的overlay路径) | Invalid overlay path. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // "/library1-default-signed.hsp"仅作示例，请替换为实际的文件路径
        let path = this.context.bundleCodeDir + "/library1-default-signed.hsp";
        try {
            this.context.resourceManager.removeResource(path);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`removeResource failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

## updateOverrideConfiguration

```TypeScript
updateOverrideConfiguration(configuration: Configuration): void
```

更新差异化资源配置。普通资源管理对象与通过它的
[getOverrideResourceManager](arkts-localization-resourcemanager-i.md#getoverrideresourcemanager-1)接口获取的差异化资源管理对象调用该方法
均可更新差异化资源管理对象的配置。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | Configuration | 是 | 指定差异化资源的配置。通过[getOverrideConfiguration](arkts-localization-resourcemanager-i.md#getoverrideconfiguration-1)获取差异化配置后，根据需求修改配置项，再作为参数传入。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: Incorrect parameter types. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let resMgr = this.context.resourceManager;
            let overrideConfig = resMgr.getOverrideConfiguration();
            overrideConfig.colorMode = resourceManager.ColorMode.DARK;
            let overrideResMgr = resMgr.updateOverrideConfiguration(overrideConfig);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`updateOverrideConfiguration failed, error code: ${code}, message: ${message}.`);
        }
    }
}

```

