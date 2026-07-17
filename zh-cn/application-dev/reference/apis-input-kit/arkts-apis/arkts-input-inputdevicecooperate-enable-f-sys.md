# enable（系统接口）

## 导入模块

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## enable

```TypeScript
function enable(enable: boolean, callback: AsyncCallback<void>): void
```

开启、关闭键鼠穿越，使用callback异步回调。

> **说明：**  
>  
> 从 API version 9开始支持，从API version 23开始废弃。建议使用  
> [cooperate.prepareCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate-1)、  
> [cooperate.unprepareCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unpreparecooperate-1)  
> 替代。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** prepareCooperate

<!--Device-inputDeviceCooperate-function enable(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-inputDeviceCooperate-function enable(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 键鼠穿越使能状态。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当开启键鼠穿越成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
           inputDeviceCooperate.enable(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to enable keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in enabling keyboard mouse crossing.`);
            });
          } catch (error) {
            console.error(`Failed to enable keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## enable

```TypeScript
function enable(enable: boolean): Promise<void>
```

开启、关闭键鼠穿越，使用Promise异步回调。

> **说明：**  
>  
> 从 API version 9开始支持，从API version 23开始废弃。建议使用  
> [cooperate.prepareCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-preparecooperate-f-sys.md#preparecooperate-2)、  
> [cooperate.unprepareCooperate](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-unpreparecooperate-f-sys.md#unpreparecooperate-2)替代。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** prepareCooperate

<!--Device-inputDeviceCooperate-function enable(enable: boolean): Promise<void>--><!--Device-inputDeviceCooperate-function enable(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 键鼠穿越使能状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          inputDeviceCooperate.enable(true).then(() => {
            console.info(`Succeeded in enabling keyboard mouse crossing.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to enable keyboard mouse crossing, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}

```

