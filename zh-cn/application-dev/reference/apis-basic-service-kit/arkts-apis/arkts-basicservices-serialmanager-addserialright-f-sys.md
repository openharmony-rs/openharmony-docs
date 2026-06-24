# addSerialRight（系统接口）

## addSerialRight

```TypeScript
function addSerialRight(tokenId: number, portId: number): void
```

ΪӦ�ó������ӷ��ʴ����豸Ȩ�ޡ�
serialManager.requestSerialRight�ᴥ�����������û���Ȩ��addSerialRight���ᴥ������������ֱ������Ӧ�ó�������豸��Ȩ�ޡ�Ӧ���˳��Զ��Ƴ��Դ����豸�ķ���Ȩ�ޣ���Ӧ����������Ҫ����������
Ȩ��

**起始版本：** 19

**需要权限：** ohos.permission.MANAGE_USB_CONFIG

**系统能力：** SystemCapability.USB.USBManager.Serial

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | number | 是 | ��Ҫ����Ȩ�޵�tokenId�� |
| portId | number | 是 | Ŀ���豸�Ķ˿ںţ�����[getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList-1)��ȡ�Ĵ��ڲ���SerialPort�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201) |  |
| [202](../../errorcode-universal.md#202) |  |
| [401](../../errorcode-universal.md#401) |  |
| [14400005](../../errorcode-universal.md#14400005) |  |
| [31400001](../../errorcode-universal.md#31400001) |  |
| [31400003](../../errorcode-universal.md#31400003) |  |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { JSON } from '@kit.ArkTS';
import { serialManager } from '@kit.BasicServicesKit';

// 获取串口列表
function addSerialRight() {
  let portList: serialManager.SerialPort[] = serialManager.getPortList();
  console.info('portList: ', JSON.stringify(portList));
  if (portList === undefined || portList.length === 0) {
    console.info('portList is empty');
    return;
  }

  let portId: number = portList[0].portId;
  // 串口增加权限
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;
  bundleManager.getBundleInfoForSelf(bundleFlags).then((bundleInfo) => {
    console.info('getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(bundleInfo));
    let tokenId = bundleInfo.appInfo.accessTokenId;
    try {
      serialManager.addSerialRight(tokenId, portId);
      console.info('addSerialRight success, portId: ' + portId);
    } catch (error) {
      console.error('addSerialRight error, ' + JSON.stringify(error));
    }
  }).catch((err : BusinessError) => {
    console.error('getBundleInfoForSelf failed');
  });
}

```

