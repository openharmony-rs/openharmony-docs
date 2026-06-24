# choose

## choose

```TypeScript
declare function choose(types?: string[]): Promise<string>
```

ͨ���ļ�������ѡ���ļ����첽�����ļ�URI��ʹ��promise��ʽ���ؽ����

**起始版本：** 6

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | string[] | 否 | �޶��ļ�ѡ������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | �첽�����ļ�URI��ע����ǰ���ش����룩 |


## choose

```TypeScript
declare function choose(callback: AsyncCallback<string>): void
```

ͨ���ļ�������ѡ���ļ����첽�����ļ�URI��ʹ��callback��ʽ���ؽ����

**起始版本：** 6

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | �첽��ȡ��Ӧ�ļ�URI��ע����ǰ���ش����룩 |


## choose

```TypeScript
declare function choose(types: string[], callback: AsyncCallback<string>): void
```

ͨ���ļ�������ѡ���ļ����첽�����ļ�URI��ʹ��callback��ʽ���ؽ����

**起始版本：** 6

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | string[] | 是 | �޶�ѡ���ļ������� |
| callback | AsyncCallback&lt;string&gt; | 是 | �첽��ȡ��Ӧ�ļ�URI��ע����ǰ���ش����룩 |

