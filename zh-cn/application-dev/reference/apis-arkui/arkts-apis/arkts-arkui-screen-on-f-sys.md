# on（系统接口）

## on

```TypeScript
function on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback<number>): void
```

������Ļ״̬�仯�ļ�����

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'connect' \| 'disconnect' \| 'change' | 是 | �����¼���<br/>-eventTypeΪ"connect"��ʾ��Ļ�����¼���<br/>-eventTypeΪ"<br/>disconnect"��ʾ�Ͽ���Ļ�����¼���<br/>-eventTypeΪ"change"��ʾ��Ļ״̬�ı��¼��� |
| callback | Callback&lt;number&gt; | 是 | �ص�������������Ļ��id���ò���Ϊ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in registering the callback for screen changes. Data: ${data}`)
};
screen.on('connect', callback);

```


## on

```TypeScript
function on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback<number>): void
```

������Ļ״̬�仯�ļ�����

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'connect' \| 'disconnect' \| 'change' | 是 | �����¼���<br/>-eventTypeΪ"connect"��ʾ��Ļ�����¼���<br/>-eventTypeΪ"<br/>disconnect"��ʾ�Ͽ���Ļ�����¼���<br/>-eventTypeΪ"change"��ʾ��Ļ״̬�ı��¼��� |
| callback | Callback&lt;number&gt; | 是 | �ص�������������Ļ��id���ò���Ϊ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in registering the callback for screen changes. Data: ${data}`)
};
screen.on('connect', callback);

```


## on

```TypeScript
function on(eventType: 'connect' | 'disconnect' | 'change', callback: Callback<number>): void
```

������Ļ״̬�仯�ļ�����

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | 'connect' \| 'disconnect' \| 'change' | 是 | �����¼���<br/>-eventTypeΪ"connect"��ʾ��Ļ�����¼���<br/>-eventTypeΪ"<br/>disconnect"��ʾ�Ͽ���Ļ�����¼���<br/>-eventTypeΪ"change"��ʾ��Ļ״̬�ı��¼��� |
| callback | Callback&lt;number&gt; | 是 | �ص�������������Ļ��id���ò���Ϊ������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |

**示例：**

```TypeScript
let callback: Callback<number> = (data: number) => {
  console.info(`Succeeded in registering the callback for screen changes. Data: ${data}`)
};
screen.on('connect', callback);

```

