# SerialPort

���ڶ����ṩ�����豸��Ϣ��ͨ���������

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

## close

```TypeScript
close(): Promise<void>
```

�رմ��ڡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## drain

```TypeScript
drain(): Promise<void>
```

�ȴ�����д��������ɡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## flush

```TypeScript
flush(): Promise<void>
```

flush���ڻ�������ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## getCts

```TypeScript
getCts(): Promise<boolean>
```

��ȡcts�ź�״̬��ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | - Promise���󣬷���CTS�ź�״̬����ʾ�Ƿ������������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## getDsr

```TypeScript
getDsr(): Promise<boolean>
```

��ȡDSR�ź�״̬��ʹ��Promise�첽����

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | DSR�ź�״̬��true��ʾ�Զ��Ѿ�����false��ʾ�Զ�δ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## offDataRead

```TypeScript
offDataRead(callback?: Callback<Uint8Array>): void
```

ȡ���������ڶ˿ڽ��������¼���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;Uint8Array&gt; | 否 | �ص����������ش��ڶ˿ڽ��յ�������<br/><br/>Ĭ��ֵ:ȱʡ��Ϊ��������ڶ˿ڽ��������¼������м����� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## offDisconnect

```TypeScript
offDisconnect(callback?: Callback<void>): void
```

ȡ������USB���⴮�ڶϿ��¼���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 否 | USB���⴮�ڶϿ��Ļص�������<br/><br/>Ĭ��ֵ���������USB���⴮�ڶϿ��¼��Ļص������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## onDataRead

```TypeScript
onDataRead(callback: Callback<Uint8Array>): void
```

�������ڶ˿ڽ��յ������ݡ�ʹ��Callback�첽�ص���
����{@link close}�ӿ�ʱ��������ȫ���ص�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;Uint8Array&gt; | 是 | �ص����������ش��ڶ˿ڽ��յ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## onDisconnect

```TypeScript
onDisconnect(callback: Callback<void>): void
```

����USB���⴮�ڶϿ��¼���ʹ��Callback�첽�ص���
����{@link close}�ӿ�ʱ��������ȫ���ص�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | USB���⴮�ڶϿ��¼��Ļص������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## open

```TypeScript
open(config?: SerialConfigs): Promise<void>
```

�򿪶˿ڡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | SerialConfigs | 否 | ����ͨ�Ų���<br/><br/>Ĭ��ֵ:Ĭ��ֵ���ο�SerialConfigs��Ĭ��ֵ��<br/><br/>Default value: Refer to the default value of SerialConfigs.. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700002](../../errorcode-universal.md#35700002-Invalid) | Invalid parameter. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700004](../../errorcode-universal.md#35700004-Port) | Port already in use. |
| [35700007](../../errorcode-universal.md#35700007-User) | User authorization required. |

## sendBrk

```TypeScript
sendBrk(): Promise<void>
```

����brk�źš�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## setDtr

```TypeScript
setDtr(enable: boolean): Promise<void>
```

����DTR�ź�״̬��ʹ��Promise�첽����

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | DTR�ź�״̬����ʾ�����Ƿ������ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - �������κ�ֵ��Promise�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## setRts

```TypeScript
setRts(enable: boolean): Promise<void>
```

����rts�źš�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | RTS�ź�״̬����ʾ�Ƿ������͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise�����޷��ؽ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |

## write

```TypeScript
write(data: Uint8Array, timeout?: number): Promise<number>
```

�������ݡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Uint8Array | 是 | Ҫ���͵�����<br/><br/>���ȷ�Χ:(0,4096]�� |
| timeout | number | 否 | ��ʱʱ��<br/><br/>���ȷ�Χ:[0,300000]��ȡֵ�޶�Ϊ��������λ:���롣Ĭ��ֵ:0��<br/><br/>��ʾ�˿��޷�д������ʱ���ȴ���ֱ�ӷ��ء� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | - Promise���󣬷��سɹ�д��ĳ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [35700001](../../errorcode-universal.md#35700001-Service) | Service error. |
| [35700002](../../errorcode-universal.md#35700002-Invalid) | Invalid parameter. |
| [35700003](../../errorcode-universal.md#35700003-Virtual) | Virtual serial port disconnected. |
| [35700005](../../errorcode-universal.md#35700005-Port) | Port not open. |
| [35700006](../../errorcode-universal.md#35700006-Transmission) | Transmission timeout. |

## portInfo

```TypeScript
readonly portInfo: SerialPortInfo
```

���ڶ˿���Ϣ

**类型：** SerialPortInfo

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BusManager.Serial

