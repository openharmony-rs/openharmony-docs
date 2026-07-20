# setKeyDownDuration（系统接口）

## 导入模块

```TypeScript
import { shortKey } from '@kit.InputKit';
```

<a id="setkeydownduration"></a>
## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: number, callback: AsyncCallback<void>): void
```

设置快捷键拉起Ability的延迟时间，使用callback异步回调。

**起始版本：** 10

<!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void--><!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.ShortKey

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessKey | string | 是 | 业务在多模侧注册的唯一标识，与ability_launch_config.json中的businessId对应。调用接口前自行查询。 |
| delay | number | 是 | 按下快捷键多长时间后拉起Ability，单位：ms，仅支持快捷键按下触发。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置快捷键拉起Ability的延迟时间成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { shortKey } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 设置延迟拉起时间500ms
            shortKey.setKeyDownDuration('businessId', 500, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting key down duration.`);
            });
          } catch (error) {
            console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        });
    }
  }
}

```


<a id="setkeydownduration-1"></a>
## setKeyDownDuration

```TypeScript
function setKeyDownDuration(businessKey: string, delay: number): Promise<void>
```

设置快捷键拉起Ability的延迟时间，使用Promise异步回调。

**起始版本：** 10

<!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int): Promise<void>--><!--Device-shortKey-function setKeyDownDuration(businessKey: string, delay: int): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.ShortKey

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessKey | string | 是 | 业务在多模侧注册的唯一标识，与ability_launch_config.json中的businessId对应。调用接口前自行查询。 |
| delay | number | 是 | 按下快捷键多长时间后拉起Ability，单位：ms，仅支持快捷键按下触发。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Returns the result through a promise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { shortKey } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 设置延迟拉起时间500ms
            shortKey.setKeyDownDuration('businessId', 500).then(() => {
              console.info(`Succeeded in setting key down duration.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set key down duration, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

