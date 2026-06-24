# Screen（系统接口）

[������](../../../../displaymanager/display-terminology.md#������)��Ļʵ����

����APIʾ���ж�����ʹ��[getAllScreens()](arkts-arkui-screen-getallscreens-f-sys.md#getAllScreens-1)��
[createVirtualScreen()](arkts-arkui-screen-createvirtualscreen-f-sys.md#createVirtualScreen-1)
�е���һ������ȡ��Screenʵ������ͨ����ʵ�����ö�Ӧ������

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## setDensityDpi

```TypeScript
setDensityDpi(densityDpi: number, callback: AsyncCallback<void>): void
```

������Ļ�������ܶȣ�ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| densityDpi | number | 是 | �����ܶȡ�֧�ֵ����뷶ΧΪ[80, 640]���ò�����֧���������롣 |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص���������������Ļ�������ܶȳɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: number = 320;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  screenClass.setDensityDpi(densityDpi, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the pixel density of the screen to 320. Code:${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the density dpi.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});

```

## setDensityDpi

```TypeScript
setDensityDpi(densityDpi: number): Promise<void>
```

������Ļ�������ܶȣ�ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| densityDpi | number | 是 | �����ܶȡ�֧�ֵ����뷶ΧΪ[80, 640]���ò�����֧���������롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let densityDpi: number = 320;
class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  let promise: Promise<void> = screenClass.setDensityDpi(densityDpi);
  promise.then(() => {
    console.info('Succeeded in setting the pixel density of the screen to 320.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the pixel density of the screen to 320. Code:${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});

```

## setOrientation

```TypeScript
setOrientation(orientation: Orientation, callback: AsyncCallback<void>): void
```

������Ļ����ʹ��callback�첽�ص��������õķ������[Ӧ����ת����](../../../../quick-start/module-configuration-file.md#abilities��ǩ)����ͨ������
module.json5�ļ���abilities��ǩ��orientation�ֶ�����Ӧ����ת���ԣ�ʱ����Ļ����Żᷢ���ı䣻�����÷��򲻷���Ӧ����ת����ʱ����Ļ���򲻻ᷢ���仯���ҽӿڲ������쳣��

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | Orientation | 是 | ��Ļ����orientationֵ��������Orientationö�ٷ��� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص���������������Ļ����ɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  screenClass.setOrientation(screen.Orientation.VERTICAL, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set the vertical orientation. Code:${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the vertical orientation.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});

```

## setOrientation

```TypeScript
setOrientation(orientation: Orientation): Promise<void>
```

������Ļ����ʹ��Promise�첽�ص��������õķ������[Ӧ����ת����](../../../../quick-start/module-configuration-file.md#abilities��ǩ)����ͨ������
module.json5�ļ���abilities��ǩ��orientation�ֶ�����Ӧ����ת���ԣ�ʱ����Ļ����Żᷢ���ı䣻�����÷��򲻷���Ӧ����ת����ʱ����Ļ���򲻻ᷢ���仯���ҽӿڲ������쳣��

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | Orientation | 是 | ��Ļ����orientationֵ��������Orientationö�ٷ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let promise: Promise<void> = screenClass.setOrientation(screen.Orientation.VERTICAL);
  promise.then(() => {
    console.info('Succeeded in setting the vertical orientation.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the vertical orientation. Code:${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});

```

## setOrientation

```TypeScript
setOrientation(orientation: Orientation, orientationOptions?: OrientationOptions): Promise<void>
```

������Ļ����

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | Orientation | 是 | ��Ļ���򡣷���ֵ�������Է���ö��ֵ�� |
| orientationOptions | OrientationOptions | 否 | Options of setting orientation. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let orientationOptions : screen.OrientationOptions = {
  needAnimation: true,
  ignoreRotationLock: false,
};

let screenClass: screen.Screen | null = null;
let screensPromise: Promise<Array<screen.Screen>> = screen.getAllScreens();
screensPromise.then((data: Array<screen.Screen>) => {
  if (data.length > 0) {
    screenClass = data[0];
    let promise: Promise<void> = screenClass.setOrientation(screen.Orientation.VERTICAL, orientationOptions);
    promise.then(() => {
      console.info('Succeeded in setting the vertical orientation with orientationOptions.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set the vertical orientation with orientationOptions. Code:${err.code}, message is ${err.message}`);
    });
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get all screens. Code:${err.code}, message is ${err.message}`);
});

```

## setScreenActiveMode

```TypeScript
setScreenActiveMode(modeIndex: number, callback: AsyncCallback<void>): void
```

������Ļ��ǰ��ʾģʽ��ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modeIndex | number | 是 | ģʽ������ģʽ�����ĵ�ǰֵ��ֵ�ķ�Χ���������Ļ��ǰ�ֱ��ʡ�ˢ���ʺ��豸Ӳ����������仯���ò�����֧���������롣����Ϊscreen��<br/>[ScreenModeInfo](arkts-arkui-screen-screenmodeinfo-i-sys.md#ScreenModeInfo)���Ե�ģʽid�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص���������������Ļ��ǰ��ʾģʽ�ɹ���errΪundefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  screenClass.setScreenActiveMode(modeIndex, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set screen active mode 0. Code:${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Succeeded in setting the screen active mode 0.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});

```

## setScreenActiveMode

```TypeScript
setScreenActiveMode(modeIndex: number): Promise<void>
```

������Ļ��ǰ��ʾģʽ��ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modeIndex | number | 是 | ģʽ������ģʽ�����ĵ�ǰֵ��ֵ�ķ�Χ���������Ļ��ǰ�ֱ��ʡ�ˢ���ʺ��豸Ӳ����������仯���ò�����֧���������롣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class VirtualScreenOption {
  name : string = '';
  width : number =  0;
  height : number = 0;
  density : number = 0;
  surfaceId : string = '';
  supportsFocus ?: boolean = true;
}

let option : VirtualScreenOption = {
  name: 'screen01',
  width: 1080,
  height: 2340,
  density: 2,
  surfaceId: '',
  supportsFocus: false
};

screen.createVirtualScreen(option).then((data: screen.Screen) => {
  let screenClass: screen.Screen = data;
  console.info(`Succeeded in creating the virtual screen. Data: ${JSON.stringify(data)}`);
  let modeIndex: number = 0;
  let promise: Promise<void> = screenClass.setScreenActiveMode(modeIndex);
  promise.then(() => {
    console.info('Succeeded in setting screen active mode 0.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set screen active mode 0.Code:${err.code}, message is ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to create the virtual screen. Code:${err.code}, message is ${err.message}`);
});

```

## activeModeIndex

```TypeScript
readonly activeModeIndex: number
```

��ǰ��Ļ����ģʽ������ģʽ�����ĵ�ǰֵ��ֵ�ķ�Χ���������Ļ��ǰ�ֱ��ʡ�ˢ���ʺ��豸Ӳ����������仯���ò���Ϊ������

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## id

```TypeScript
readonly id: number
```

��Ļ��id���ò���ӦΪ������

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## orientation

```TypeScript
readonly orientation: Orientation
```

��Ļ����

**类型：** Orientation

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## parent

```TypeScript
readonly parent: number
```

��Ļ����Ⱥ���id���ò���Ϊ������

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## rsId

```TypeScript
readonly rsId: number
```

��Ļ�˿ڵ�id���ò���Ϊ������

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## serialNumber

```TypeScript
readonly serialNumber?: string
```

��չ��Ļ�����кţ�Ĭ�Ϸ���Ϊ���ַ�����

**类型：** string

**起始版本：** 15

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## sourceMode

```TypeScript
readonly sourceMode: ScreenSourceMode
```

��Ļ��Դģʽ��

**类型：** ScreenSourceMode

**起始版本：** 10

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## supportedModeInfo

```TypeScript
readonly supportedModeInfo: Array<ScreenModeInfo>
```

��Ļ֧�ֵ�ģʽ���ϡ�

**类型：** Array<ScreenModeInfo>

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

