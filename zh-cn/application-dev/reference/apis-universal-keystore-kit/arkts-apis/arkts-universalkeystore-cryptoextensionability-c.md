# CryptoExtensionAbility

Class to be override for external crypto extension ability.

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## onAuthUkeyPin

```TypeScript
onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

����Ukey��֤PIN�롣ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��Դ����� |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0��authState��0����ʾ��֤����ɹ�������ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á�<br/>34800006 - Ukey PIN�����<br/>34800007 - Ukey PIN�뱻�� |

## onClearUkeyPinAuthState

```TypeScript
onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

���Ӧ��ά��PIN�����֤״̬��ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��Դ��� |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0����ʾ���PIN����֤״̬�ɹ�������ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á� |

## onCloseResource

```TypeScript
onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

���ݲ����е�handle���ر�Ukey����Կ��Դ��ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | �Ự����� |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | �������ص�promise��<br/>HuksCryptoExtensionResult.resultCode���ܾ�������ֵ��<br/>0-�����ɹ�<br/>34800000 -������չ�з������󡣿���ԭ��<br/>1.��������Ƿ���<br/>2.������չ�����޷������Ĵ���״̬��<br/>34800002-UKey���������������ζ��UKey���������з�����δ֪����<br/>34800004 -��������ڡ�����ԭ��<br/>1.����ľ����Ч��<br/>2.huks����ͼ�����չ��״̬��һ�¡������쳣��<br/>huks������еľ��û�б��ͷš�<br/>34800005 -��������ã���������Ϊ״̬��һ��<br/>�ڼ�����չ��UKey֮�䡣 |

## onEnumCertificates

```TypeScript
onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]):
      Promise<HuksCryptoExtensionResult>
```

ö��Extension������Ukey�豸��֤����Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 否 | �������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��certs��Ա�ǿգ�������ȡ������֤�顣����ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800001 - Ukey�����ڡ�<br/>34800002 - Ukey�������� |

## onExportCertificate

```TypeScript
onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

��ѯָ��resourceId�µ�֤�顣ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | ��ԴID�� |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 否 | �������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��certs��Ա�ǿգ�������ȡ�ĵ���֤�顣����ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800001 - Ukey�����ڡ�<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ� |

## onExportKeyItem

```TypeScript
onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

���ڵ���ָ����Կ�Ĺ�Կ��ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��������Կ����Դ��� |
| params | HuksCryptoExtensionParam[] | 是 | ������Կ���������Բ����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0��outDataЯ�������Ĺ�Կ���ݡ�����ʧ��ʱ��resultCodeЯ����������Ϣ��errInfoЯ����ϸ������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800001 - Ukey�����ڡ�<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á� |

## onFinishSession

```TypeScript
onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

����ʽ��Կ�Ự����������ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initHandle | string | 是 | ��Դ����� |
| params | huks.HuksOptions \| HuksCryptoExtensionParams | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0������ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800002 - Ukey��������<br/>34800003 - Ukey PIN��δ��֤��<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á�<br/>34800007 - Ukey PIN�뱻���� |

## onGenerateKeyItem

```TypeScript
onGenerateKeyItem(handle: string, params:HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

��������չ�豸��������Կ�ԡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��������Կ����Դ����� |
| params | HuksCryptoExtensionParam[] | 是 | ��Կ���ɲ��������Բ����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0����ʾ������Կ�ɹ�������ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800001 - Ukey�����ڡ�<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á� |

## onGetProperty

```TypeScript
onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

��ѯ�����ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | handle��ʾonOpenResource�򿪵ľ���� |
| propertyId | string | 是 | propertyId��ʾ���Ժ��������ƣ�GMT 0016-2023�ж��塣 |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | �������ص�promise��<br/>HuksCryptoExtensionResult.resultCode���ܾ�������ֵ��<br/>0-�����ɹ�<br/>34800000 -������չ�з������󡣿���ԭ��<br/>1.��������Ƿ���<br/>2.������չ�����޷������Ĵ���״̬��<br/>34800002-UKey���������������ζ��UKey���������з�����δ֪����<br/>34800003-UKey PINδ��Ȩ��������֤UKey PIN�롣<br/>34800004 -��������ڡ�����ԭ��<br/>1.����ľ����Ч��<br/>2.huks����ͼ�����չ��״̬��һ�¡������쳣��<br/>huks������еľ��û�б��ͷš�<br/>34800005 -��������ã���������Ϊ״̬��һ��<br/>�ڼ�����չ��UKey֮�䡣<br/>34800007-UKey PIN����������Ϊ�ѳ�������������Դ����� |

## onGetResourceId

```TypeScript
onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

�ص��Ի�ȡ������չ����ԴID��

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | HuksCryptoExtensionParam[] | 是 | ��ȡ��ԴID��������Բ����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | params - ��ȡ��ԴID��������Բ����� |

## onGetUkeyPinAuthState

```TypeScript
onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
      HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

��ȡUkey��PIN����֤״̬��ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��Դ����� |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0��HuksCryptoExtensionResult��authState��Ա�ǿգ�Ϊ��ȡ��PIN����֤״̬������ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á� |

## onImportCertificate

```TypeScript
onImportCertificate(handle: string, params: HuksCryptoExtensionParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult>
```

����ָ����Դ�����֤�顣ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ����֤�����Դ����� |
| params | HuksCryptoExtensionParam[] | 是 | Indicates<br/>the needed properties for the import certificate operation. |
| certInfo | HuksCryptoExtensionCertInfo | 是 | �������֤����Ϣ����ָ��֤�����ͣ�purpose�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0����ʾ����֤��ɹ�������ʧ��ʱ��resultCodeЯ����������Ϣ��errInfoЯ����ϸ������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800001 - Ukey�����ڡ�<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á� |

## onImportWrappedKeyItem

```TypeScript
onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[],
      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult>
```

���ڵ�����ܷ�װ����Կ�ԡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��������Կ����Դ����� |
| wrappingHandle | string | 是 | ��������Կ����Դ����� |
| params | HuksCryptoExtensionParam[] | 是 | ������Կ��������� |
| wrappedKey | Uint8Array | 是 | ��װ��Կ���ݣ���ʽ����Կ��չ���塣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0����ʾ������Կ�ɹ�������ʧ��ʱ��resultCodeЯ����������Ϣ��errInfoЯ����ϸ������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800001 - Ukey�����ڡ�<br/>34800002 - Ukey��������<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á� |

## onInitSession

```TypeScript
onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

����ʽ��ʼ����Կ�Ự������ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��Դ����� |
| params | huks.HuksOptions \| HuksCryptoExtensionParams | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0��handle��Ա�ǿա�����ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800002 - Ukey��������<br/>34800003 - Ukey PIN��δ��֤��<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á�<br/>34800007 - Ukey PIN�뱻���� |

## onOpenResource

```TypeScript
onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> |
     HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult>
```

����Դ����ص����ڼ��ܲ���֮ǰ�����Դ����ȡ�����ע�⣺���صľ�����뱻onCloseResource�رա�

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceId | string | 是 | resourceId��ʾ��ԴID |
| params | Array&lt;huksExternalCrypto.HuksExternalCryptoParam&gt; \| HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | �������ص�promise��<br/>HuksCryptoExtensionResult.resultCode���ܾ�������ֵ��<br/>0-�����ɹ�<br/>34800000 -������չ�з������󡣿���ԭ��<br/>1.��������Ƿ���<br/>2.������չ�����޷������Ĵ���״̬��<br/>34800001-UKey�����ڡ�����ԭ��<br/>1.UKey�Ѿ����Ƴ���<br/>2.������չά����һ�������UKey״̬��<br/>34800002-UKey���������������ζ��UKey���������з�����δ֪����<br/>34800004-resourceId�����ڡ���˵��resourceId���豸���ơ�Ӧ�����ƻ��������ƴ��� |

## onSetProperty

```TypeScript
onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]):
      Promise<HuksCryptoExtensionResult>
```

���ݲ����е�handle��propertyId�������ԡ�ʹ��Promise�첽�ص���

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | string | 是 | ��Դ����� |
| propertyId | string | 是 | ���Ҳ������������ƣ���GMT 0016-2023�ж����SKF�ӿ�����Ҫҵ����Խӿ������䡣 |
| params | HuksCryptoExtensionParam[] | 是 | �������ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise���ڷ���HuksCryptoExtensionResult��<br/>HuksCryptoExtensionResult.resultCode���ܾ�������ֵ��<br/>0-�����ɹ���<br/>34800000 -������չ�з������󡣿���ԭ��<br/>1.��������Ƿ���<br/>2.������չ�����޷������Ĵ���״̬��<br/>34800002 -����UKey�����ӿ�ʧ�ܡ�����UKey���Ӻ���������״̬��<br/>34800003-UKey PINδ��Ȩ��������֤UKey PIN�롣<br/>34800004 -��������ڡ�����ԭ��<br/>1.����ľ����Ч��<br/>2.HUKS����ͼ�����չ��״̬��һ�¡������쳣��<br/>HUKS������еľ��û���ͷš�<br/>34800005 -��������ã���������Ϊ״̬��һ��<br/>�ڼ�����չ��UKey֮�䡣<br/>34800007-UKey PIN����������Ϊ�ѳ�������������Դ����� |

## onUpdateSession

```TypeScript
onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams):
      Promise<HuksCryptoExtensionResult>
```

����ʽ��Կ�Ự�������ݲ�����ʹ��Promise�첽�ص���

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initHandle | string | 是 | ��Դ����� |
| params | huks.HuksOptions \| HuksCryptoExtensionParams | 是 | params indicates the<br/>properties of the operation[since 26.0.0]. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksCryptoExtensionResult&gt; | Promise����<br/>�����óɹ�ʱ��resultCodeΪ0������ʧ��ʱ��resultCodeЯ����������Ϣ��<br/>���ܷ��صĴ�����ֵ��<br/>0 - ���óɹ���<br/>34800000 - ��Կ��չ����<br/>34800002 - Ukey��������<br/>34800003 - Ukey PIN��δ��֤��<br/>34800004 - ��������ڡ�<br/>34800005 - ��������á�<br/>34800007 - Ukey PIN�뱻���� |

