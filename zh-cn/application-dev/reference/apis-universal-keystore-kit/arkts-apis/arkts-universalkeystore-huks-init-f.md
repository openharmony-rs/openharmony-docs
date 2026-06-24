# init

## init

```TypeScript
function init(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksHandle>): void
```

init������Կ�ӿڡ�ʹ��callback�첽�ص���

huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.initSession<sup>9+</sup>](arkts-universalkeystore-huks-initsession-f.md#initSession-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** initSession(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Init������Կ�ı����� |
| options | HuksOptions | 是 | Init�����Ĳ������ϡ� |
| callback | AsyncCallback&lt;HuksHandle&gt; | 是 | �ص�����������Կ����init�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksHandle������Ϊ�������<br/>HuksHandle��handle����init���ɵ�handle�� |


## init

```TypeScript
function init(keyAlias: string, options: HuksOptions): Promise<HuksHandle>
```

init������Կ�ӿڡ�ʹ��Promise�첽�ص���

huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.initSession<sup>9+</sup>](arkts-universalkeystore-huks-initsession-f.md#initSession-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** initSession(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Init������Կ�ı����� |
| options | HuksOptions | 是 | Init�������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksHandle&gt; | Promise���󣬷���HuksResult��HuksHandle��handle����init���ɵ�handle�� |

