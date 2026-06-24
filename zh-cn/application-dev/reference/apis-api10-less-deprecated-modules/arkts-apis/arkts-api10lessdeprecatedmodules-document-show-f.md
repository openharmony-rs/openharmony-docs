# show

## show

```TypeScript
declare function show(uri: string, type: string): Promise<void>
```

�첽��URI��Ӧ���ļ���ʹ��promise��ʽ���ؽ����

**起始版本：** 6

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ���򿪵��ļ�URI |
| type | string | 是 | �����ļ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�ص�����void��ʾ�ɹ����ļ���ע����ǰ���ش����룩 |


## show

```TypeScript
declare function show(uri: string, type: string, callback: AsyncCallback<void>): void
```

�첽��URI��Ӧ���ļ���ʹ��callback��ʽ���ؽ����

**起始版本：** 6

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ���򿪵��ļ�URI |
| type | string | 是 | �����ļ������� |
| callback | AsyncCallback&lt;void&gt; | 是 | �첽��uri��Ӧ�ļ���ע����ǰ���ش����룩 |

