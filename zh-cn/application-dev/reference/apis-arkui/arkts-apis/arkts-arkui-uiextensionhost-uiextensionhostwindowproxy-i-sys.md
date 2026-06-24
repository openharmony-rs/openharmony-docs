# UIExtensionHostWindowProxy（系统接口）

Transition Controller

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise<window.Window>
```

������UIExtensionHostWindowProxyʵ���µ��Ӵ��ڣ�ʹ��Promise�첽�ص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | �Ӵ��ڵ����֡� |
| subWindowOptions | window.SubWindowOptions | 是 | �Ӵ��ڲ����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;window.Window&gt; | Promise used to return the subwindow created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal. Possible causes:<br/>1. The window is not created or destroyed.<br/>2. Internal task error.<br/>3. The subWindow has been created and can not be created again.<br/>4. It is not allowed to create non-secure window when secure extension exists. |
| [1300035](../../errorcode-universal.md#1300035-Creating) | Creating a subwindow is not allowed in the current context. Possible cause:<br/>1. An AgentUIExtensionAbility cannot create a subwindow. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    const subWindowOpts: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionHostWindow.createSubWindowWithOptions('subWindowForHost', subWindowOpts)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) =>{
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data)=>{
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data)=>{
              if (err && err.code != 0) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code == 0) {
                  console.info(`The subwindow has been shown!`);
                } else {
                  console.error(`Failed to show the subwindow!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed: ${JSON.stringify(error)}`);
      })
  }
}

```

## createSubWindowWithOptions

```TypeScript
createSubWindowWithOptions(name: string, subWindowConfig: window.SubWindowOptions,
        followCreatorLifecycle: boolean): Promise<window.Window>
```

������UIExtensionHostWindowProxyʵ���µ��Ӵ��ڣ���ͨ������followCreatorLifecycle�������Ӵ��Ƿ���������EmbeddedComponent��
UIExtensionComponent�����������ڣ�ʹ��Promise�첽�ص���

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | �Ӵ��ڵ����֡� |
| subWindowConfig | window.SubWindowOptions | 是 | �Ӵ��ڲ����� |
| followCreatorLifecycle | boolean | 是 | �Ӵ����������Ƿ�������EmbeddedComponent��UIExtensionComponent������ͬ����true��ʾ���������ʱ��<br/>�Ӵ����أ��������ʾʱ�Ӵ���ʾ��false��ʾ�Ӵ������������������仯�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;window.Window&gt; | Promise used to return the subwindow. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |
| [1300002](../../errorcode-universal.md#1300002-This) | This window state is abnormal. Possible causes:<br/>1. The window is not created or destroyed.<br/>2. Internal task error.<br/>3. The subWindow has been created and can not be created again.<br/>4. It is not allowed to create non-secure window when secure extension exists. |
| [1300035](../../errorcode-universal.md#1300035-Creating) | Creating a subwindow is not allowed in the current context. Possible cause:<br/>1. An AgentUIExtensionAbility cannot create a subwindow. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    const subWindowConfig: window.SubWindowOptions = {
      title: 'This is a subwindow',
      decorEnabled: true
    };
    // 创建子窗口
    extensionHostWindow.createSubWindowWithOptions('subWindowForHost', subWindowConfig, true)
      .then((subWindow: window.Window) => {
        subWindow.setUIContent('pages/Index', (err, data) =>{
          if (err && err.code != 0) {
            return;
          }
          subWindow?.resize(300, 300, (err, data)=>{
            if (err && err.code != 0) {
              return;
            }
            subWindow?.moveWindowTo(100, 100, (err, data)=>{
              if (err && err.code != 0) {
                return;
              }
              subWindow?.showWindow((err, data) => {
                if (err && err.code == 0) {
                  console.info(`The subwindow has been shown!`);
                } else {
                  console.error(`Failed to show the subwindow!`);
                }
              });
            });
          });
        });
      }).catch((error: BusinessError) => {
        console.error(`Create subwindow failed: ${JSON.stringify(error)}`);
      })
  }
}

```

## getWindowAvoidArea

```TypeScript
getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea
```

��ȡ����Ӧ�ô������ݹ�ܵ�������ϵͳ��������������������������������������������������ص�ʱ����Ҫ�����������ݱ��õ�����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | window.AvoidAreaType | 是 | ��ʾ���������͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| window.AvoidArea | Avoidance area for the content of the host window. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. |

**示例：**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 获取宿主应用窗口的避让信息
    const avoidArea = extensionHostWindow.getWindowAvoidArea(window.AvoidAreaType.TYPE_SYSTEM);
    console.info(`avoidArea: ${JSON.stringify(avoidArea)}`);
  }
}

```

## hideNonSecureWindows

```TypeScript
hideNonSecureWindows(shouldHide: boolean): Promise<void>
```

�����Ƿ����ز���ȫ���ڣ�ʹ��Promise�첽�ص���

> **˵����**
>
> - ����ȫ������ָ�����ڵ�[EmbeddedComponent](./@internal/component/ets/embedded_component)����
> [UIExtensionComponent](./@internal/component/ets/ui_extension_component)������Ĵ��ڣ���ȫ���������������Ӵ��ں�����������Dialog����
> ��������ϵͳӦ�ô������������ʹ��ڣ���
>
> - ��EmbeddedComponent����UIExtensionComponent�������������ʾ���в�����ʾ����ʱ������ѡ�����ز���ȫ���ڣ��������в�����ʾ���ݲ��ᱻ�ڵ�����EmbeddedComponent����
> UIExtensionComponent���������ʾ������ʱ������ȫ���ڻ�������ʾ��
>
> - ���PC/2in1�豸��������hideNonSecureWindows(true)ʱ������ȫ�����е�ȫ�����������ᱻ���ء�

**起始版本：** 11

**需要权限：** ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | ָʾ�Ƿ����ز���ȫ���ڣ�true��ʾ���أ�false��ʾ�����ء� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣡� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system<br/>API.&lt;br&gt;**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [1300002](../../errorcode-universal.md#1300002-Abnormal) | Abnormal state. Possible causes:<br/>1. Permission denied. Interface caller does not have permission "ohos.permission.ALLOW_SHOW_NON_SECURE_WINDOWS".<br/>2. The UIExtension window proxy is abnormal.&lt;br&gt;**适用版本：** 12+ |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally.&lt;br&gt;**适用版本：** 12+ |

**示例：**

```TypeScript
// ExtensionProvider.ets

import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 隐藏非安全窗口
    extensionHostWindow.hideNonSecureWindows(true).then(()=> {
      console.info(`Succeeded in hiding the non-secure windows.`);
    }).catch((err: BusinessError)=> {
      console.error(`Failed to hide the non-secure windows. Cause:${JSON.stringify(err)}`);
    })
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 取消隐藏非安全窗口
    extensionHostWindow.hideNonSecureWindows(false).then(()=> {
      console.info(`Succeeded in showing the non-secure windows.`);
    }).catch((err: BusinessError)=> {
      console.error(`Failed to show the non-secure windows. Cause:${JSON.stringify(err)}`);
    })
  }
}

```

## hidePrivacyContentForHost

```TypeScript
hidePrivacyContentForHost(shouldHide: boolean): Promise<void>
```

����UIExtension����ڷ�ϵͳ��ͼʱ����˽���ݱ������أ�ʹ��Promise�첽�ص���

> **˵����**
>
> ������ͼ��˽���ݱ�����ʹ�ô��ڽ�ͼ[window.snapshot](../../../../reference/apis-arkui/arkts-apis-window-Window.md#snapshot9)���������ͼ
> [UIContext.getComponentSnapshot](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)
> ���޷���ȡ����ǰ��������ݣ�������������´������Ӵ�����

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shouldHide | boolean | 是 | �Ƿ�����ͼ��˽������true��ʾ������false��ʾ�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [1300002](../../errorcode-universal.md#1300002-Abnormal) | Abnormal state. Possible causes:<br/>1. The UIExtension window proxy is abnormal.<br/>2. Not the UIExtensionAbility process calling. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 开启截图隐私内容保护
    extensionHostWindow.hidePrivacyContentForHost(true).then(() => {
      console.info(`Successfully enabled privacy protection for non-system screenshots.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed enabled privacy protection for non-system screenshots. Cause:${JSON.stringify(err)}`);
    })
  }
}

```

## off('avoidAreaChange')

```TypeScript
off(type: 'avoidAreaChange', callback?: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void
```

ע��ϵͳ�������仯�ļ�����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | 是 | ע�����¼����ͣ��̶�Ϊ'avoidAreaChange'����ϵͳ�������仯�¼��� |
| callback | Callback&lt;{ type: window.AvoidAreaType, area: window.AvoidArea }&gt; | 否 | �ص��������������ò�������رոü��������δ�����<br/>������ر�����ϵͳ�������仯�ļ����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [1300002](../../errorcode-universal.md#1300002-Abnormal) | Abnormal state. Possible causes:<br/>1. The listening type is not supported.<br/>2. The listening type is not registered.<br/>3. The listener has not been registered.<br/>4. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession} from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注销所有避让区变化的监听
    extensionHostWindow.off('avoidAreaChange');
  }
}

```

## off('windowSizeChange')

```TypeScript
off(type: 'windowSizeChange', callback?: Callback<window.Size>): void
```

ע�������EmbeddedComponent��UIExtensionComponent���ߴ�仯�ļ�����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | 是 | ע�����¼����ͣ��̶�ֵ��'windowSizeChange'���������EmbeddedComponent��UIExtensionComponent���ߴ�<br/>�仯�¼��� |
| callback | Callback&lt;window.Size&gt; | 否 | �ص����������ص�ǰ�������EmbeddedComponent��UIExtensionComponent���ߴ硣�������ò�������رո�<br/>���������δ�����������ر������EmbeddedComponent��UIExtensionComponent���ߴ�仯�ļ����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [1300002](../../errorcode-universal.md#1300002-Abnormal) | Abnormal state. Possible causes:<br/>1. The listening type is not supported.<br/>2. The listening type is not registered.<br/>3. The listener has not been registered.<br/>4. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注销组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionHostWindow.off('windowSizeChange');
  }
}

```

## on('avoidAreaChange')

```TypeScript
on(type: 'avoidAreaChange', callback: Callback<{ type: window.AvoidAreaType, area: window.AvoidArea }>): void
```

ע��ϵͳ�������仯�ļ�����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'avoidAreaChange' | 是 | �������¼����ͣ��̶�Ϊ'avoidAreaChange'����ϵͳ�������仯�¼��� |
| callback | Callback&lt;{ type: window.AvoidAreaType, area: window.AvoidArea }&gt; | 是 | �ص�������������ڽ��յ�ǰ����������Ϣ�����У�"<br/>type"��ʾ���ڱ��������ͣ�"area"��ʾ�������ݱ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [1300002](../../errorcode-universal.md#1300002-Abnormal) | Abnormal state. Possible causes:<br/>1. The listening type is not supported.<br/>2. The listener has been registered.<br/>3. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注册避让区变化的监听
    extensionHostWindow.on('avoidAreaChange', (info) => {
      console.info(`The avoid area of the host window is: ${JSON.stringify(info.area)}.`);
    });
  }
}

```

## on('windowSizeChange')

```TypeScript
on(type: 'windowSizeChange', callback: Callback<window.Size>): void
```

ע�������EmbeddedComponent��UIExtensionComponent���ߴ�仯�ļ�����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeChange' | 是 | �������¼����ͣ��̶�Ϊ'windowSizeChange'���������EmbeddedComponent��UIExtensionComponent���ߴ��<br/>���¼��� |
| callback | Callback&lt;window.Size&gt; | 是 | �ص�������������ڽ��յ�ǰ�����EmbeddedComponent��UIExtensionComponent���ĳߴ硣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [1300002](../../errorcode-universal.md#1300002-Abnormal) | Abnormal state. Possible causes:<br/>1. The listening type is not supported.<br/>2. The listener has been registered.<br/>3. The UIExtension window proxy is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 注册组件（EmbeddedComponent或UIExtensionComponent）大小变化的监听
    extensionHostWindow.on('windowSizeChange', (size) => {
      console.info(`The size of the component is: ${JSON.stringify(size)}.`);
    });
  }
}

```

## setWaterMarkFlag

```TypeScript
setWaterMarkFlag(enable: boolean): Promise<void>
```

Ϊ��ǰ�������ӻ�ɾ����ȫˮӡ��־��ʹ��Promise�첽�ص���

> **˵����**
>
> ���Ӱ�ȫˮӡ��־�󣬴�����ǰ̨ʱ�Ὣ��ǰȫ��Ļ����ˮӡ��ȫ�����������������ȳ�����ֻҪ�������˰�ȫˮӡ��־�Ĵ�����ǰ̨���ͻ���ʾȫ��ˮӡ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | �Ƿ�Դ������ӱ�־λ��true��ʾ���ӣ�false��ʾɾ���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300002](../../errorcode-universal.md#1300002-The) | The UIExtension window proxy is abnormal. |
| [1300003](../../errorcode-universal.md#1300003-This) | This window manager service works abnormally. |
| [1300008](../../errorcode-universal.md#1300008-The) | The display device is abnormal. |

**示例：**

```TypeScript
// ExtensionProvider.ets
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 添加安全水印标志
    extensionHostWindow.setWaterMarkFlag(true).then(() => {
      console.info(`Succeeded in setting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to setting water mark flag of window. Cause:${JSON.stringify(err)}`);
    })
  }
  onSessionDestroy(session: UIExtensionContentSession) {
    const extensionHostWindow = session.getUIExtensionHostWindowProxy();
    // 删除安全水印标志
    extensionHostWindow.setWaterMarkFlag(false).then(() => {
      console.info(`Succeeded in deleting water mark flag of window.`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to deleting water mark flag of window. Cause:${JSON.stringify(err)}`);
    })
  }
}

```

## properties

```TypeScript
properties: UIExtensionHostWindowProxyProperties
```

UIExtensionComponent����Լ��������ڵ���Ϣ��

**Լ����** ���ڼܹ�Լ������������
[onSessionCreate](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensionability-c.md#onSessionCreate-1)�׶�ͬ����ȡ��ֵ���������յ�
[on('windowSizeChange')](arkts-arkui-uiextensionhost-uiextensionhostwindowproxy-i-sys.md#on-2)
�ص�֮���ȡ��

**类型：** UIExtensionHostWindowProxyProperties

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

