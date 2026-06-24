# setVirtualScreenSurface（系统接口）

## setVirtualScreenSurface

```TypeScript
function setVirtualScreenSurface(screenId:number, surfaceId: string, callback: AsyncCallback<void>): void
```

����������Ļ��surface����ʾ��ǰ������������ʾ��Ӧsurface�е����ݣ�ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.CAPTURE_SCREEN

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | ��Ļ��id���ò�����֧���������롣 |
| surfaceId | string | 是 | ����������Ļ��surface��ʶ����surfaceIdֵ�����ж��壬���û�ָ��ĳһʵ�ʴ��ڵ�surface��Ӧ��surfaceId�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص�������������������Ļsurface�ɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    screen.setVirtualScreenSurface(screenId, surfaceId, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the surface for the virtual screen. Code:${err.code}, message is ${err.message}`);
      return;
    }
      console.info('Succeeded in setting the surface for the virtual screen.');
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick((event: ClickEvent) => {
          this.setVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}

```


## setVirtualScreenSurface

```TypeScript
function setVirtualScreenSurface(screenId:number, surfaceId: string): Promise<void>
```

����������Ļ��surface����ʾ��ǰ������������ʾ��Ӧsurface�е����ݣ�ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.CAPTURE_SCREEN

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| screenId | number | 是 | ��Ļ��id���ò�����֧���������롣 |
| surfaceId | string | 是 | ����������Ļ��surface��ʶ����surfaceIdֵ�����ж��壬���û�ָ��ĳһʵ�ʴ��ڵ�surface��Ӧ��surfaceId�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400001](../../errorcode-universal.md#1400001-Invalid) | Invalid display or screen. |

**示例：**

```TypeScript
// Index.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  xComponentController: XComponentController = new XComponentController();

  setVirtualScreenSurface = () => {
    let screenId: number = 1;
    let surfaceId = this.xComponentController.getXComponentSurfaceId();
    screen.setVirtualScreenSurface(screenId, surfaceId).then(() => {
      console.info('Succeeded in setting the surface for the virtual screen.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the surface for the virtual screen. Code:${err.code}, message is ${err.message}`);
    });
  }
  build() {
    RelativeContainer() {
      XComponent({
        type: XComponentType.SURFACE,
        controller: this.xComponentController
      })
      Button('setSurface')
        .onClick((event: ClickEvent) => {
          this.setVirtualScreenSurface();
      }).width('100%')
      .height(20)
    }
    .width('100%')
    .height('100%')
  }
}

```

