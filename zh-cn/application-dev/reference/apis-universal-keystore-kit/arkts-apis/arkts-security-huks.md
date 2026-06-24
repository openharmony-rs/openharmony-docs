# @ohos.security.huks

��Ӧ���ṩ��Կ��������������Կ��������Կ������ѧ�����ȹ��ܡ�

HUKS����������Կ������Ӧ�õ��������Ӧ�õ���HUKS�ӿ����ɡ�

**起始版本：** 8

**系统能力：** SystemCapability.Security.Huks.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-universalkeystore-huks-abort-f.md#abort-1) | abort��ֹ��Կ������ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.abortSession&lt;sup&gt;9+&lt;/sup&gt;](huks.abortSession(handle: number, options: HuksOptions, callback: AsyncCallback&lt;void&gt;))<br/>&gt; �����<br/> |
| [abort](arkts-universalkeystore-huks-abort-f.md#abort-2) | abort��ֹ��Կ������ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.abortSession&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-abortsession-f.md#abortSession-2)�����<br/> |
| [abortSession](arkts-universalkeystore-huks-abortsession-f.md#abortSession-1) | abortSession��ֹ��Կ������ʹ��callback�첽�ص���<br/> |
| [abortSession](arkts-universalkeystore-huks-abortsession-f.md#abortSession-2) | abortSession��ֹ��Կ������ʹ��Promise�첽�ص���<br/> |
| [anonAttestKeyItem](arkts-universalkeystore-huks-anonattestkeyitem-f.md#anonAttestKeyItem-1) | ��ȡ��������Կ֤�顣ʹ��callback�첽�ص���<br/><br/>�ò�����Ҫ�������У��Һ�ʱ�ϳ�������12000012������ʱ�����������������쳣���¡���ʱ���û����������Ҫ��ʾ�û�����û�����ӣ�����Ѿ��������������������綶������ʧ�ܣ��������ԡ�<br/><br/>&lt;!--RP1--&gt;&lt;!--RP1End--&gt;<br/> |
| [anonAttestKeyItem](arkts-universalkeystore-huks-anonattestkeyitem-f.md#anonAttestKeyItem-2) | ��ȡ��������Կ֤�顣ʹ��Promise�첽�ص���<br/><br/>�ò�����Ҫ�������У��Һ�ʱ�ϳ�������12000012������ʱ�����������������쳣���¡���ʱ���û����������Ҫ��ʾ�û�����û�����ӣ�����Ѿ��������������������綶������ʧ�ܣ��������ԡ�<br/><br/>&lt;!--RP1--&gt;&lt;!--RP1End--&gt;<br/> |
| <!--DelRow-->[anonAttestKeyItemAsUser](arkts-universalkeystore-huks-anonattestkeyitemasuser-f-sys.md#anonAttestKeyItemAsUser-1) | ָ���û����ݻ�ȡ��������Կ֤�飬ʹ��Promise��ʽ�첽���ؽ����<br/><br/>�ò�����Ҫ�������У��Һ�ʱ�ϳ���<br/> |
| [anonAttestKeyItemOffline](arkts-universalkeystore-huks-anonattestkeyitemoffline-f.md#anonAttestKeyItemOffline-1) | ����ģʽ�»�ȡ��������Կ֤�顣ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; - ������Կ֤���������磬��Ҫ��������ʹ�øýӿ��Ը�������֤�飬�Ƽ�����ʹ������������Կ֤����<br/>&gt;<br/>&gt; - ����������Կ֤���豣֤����ʱ����׼ȷ�ģ�������ܵ��¶Զ�У��֤�鳬��ʧ�ܡ�<br/><br/>&gt; **˵��**<br/>&gt; &gt;<br/>&gt; - Offline key attestation depends on the network. You need to periodically connect to the network to use this API<br/>&gt; to update the offline certificate. Offline anonymous key attestation is recommended.<br/>&gt; &gt;<br/>&gt; - Offline anonymous key attestation requires that the local time be accurate. Otherwise, the peer end may fail to<br/>&gt; verify the certificate expiration��<br/> |
| <!--DelRow-->[anonAttestKeyItemOfflineAsUser](arkts-universalkeystore-huks-anonattestkeyitemofflineasuser-f-sys.md#anonAttestKeyItemOfflineAsUser-1) | ���߻�ȡ����֤��֤�顣�ýӿ�ʹ��promise���ؽ�����˲�������Ҫÿ�ζ���Ҫ�������ӣ�<br/>��anonAttestKeyItemAsUser�������ܸߡ�<br/><br/>&gt; **˵��**<br/>&gt; &gt;<br/>&gt; -������Կ֤�����������硣����Ҫ���������������ʹ�ô�API��������֤�顣<br/>&gt; &gt;<br/>&gt; -����������Կ֤��Ҫ�󱾵�ʱ��׼ȷ�����򣬿��ܵ��¶Զ��޷�������������֤֤����ڡ�<br/> |
| [attestKeyItem](arkts-universalkeystore-huks-attestkeyitem-f.md#attestKeyItem-1) | ��ȡ��Կ֤�顣ʹ��callback�첽�ص���<br/><br/>&lt;!--RP6--&gt;<br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��ʹ�÷�����֤����Կ֤��ʱ���ɵ�֤�������ܰ����豸��ʶ��������ʵ��������ȷ�ϣ���������豸��ʶ������ʹ�á����桢�����ɿ����߾��������鿪����������˽�����ж���ʹ��Ŀ�ġ�������Ժ����ٷ�ʽ����˵����<br/>&lt;!--RP6End--&gt;<br/> |
| [attestKeyItem](arkts-universalkeystore-huks-attestkeyitem-f.md#attestKeyItem-2) | ��ȡ��Կ֤�顣ʹ��Promise�첽�ص���<br/><br/>&lt;!--RP6--&gt;<br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��ʹ�÷�����֤����Կ֤��ʱ���ɵ�֤�������ܰ����豸��ʶ��������ʵ��������ȷ�ϣ���������豸��ʶ������ʹ�á����桢�����ɿ����߾��������鿪����������˽�����ж���ʹ��Ŀ�ġ�������Ժ����ٷ�ʽ����˵����<br/>&lt;!--RP6End--&gt;<br/> |
| <!--DelRow-->[attestKeyItemAsUser](arkts-universalkeystore-huks-attestkeyitemasuser-f-sys.md#attestKeyItemAsUser-1) | ָ���û����ݻ�ȡ��Կ֤�飬ʹ��Promise��ʽ�첽���ؽ����<br/> |
| [decapsulate](arkts-universalkeystore-huks-decapsulate-f.md#decapsulate-1) | Post-Quantum Cryptography��Կ���װ������֧��HUKS��Կ����<br/>����Ӧ�ó��������������Ӧ�ó���ѡ�������Կ��<br/>�Գ���Կ������HuksReturnResult��outData�ֶ��С�<br/> |
| [deleteKey](arkts-universalkeystore-huks-deletekey-f.md#deleteKey-1) | ɾ����Կ��ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.deleteKeyItem&lt;sup&gt;9+&lt;/sup&gt;](huks.deleteKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;))<br/>&gt; �����<br/> |
| [deleteKey](arkts-universalkeystore-huks-deletekey-f.md#deleteKey-2) | ɾ����Կ��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.deleteKeyItem&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-deletekeyitem-f.md#deleteKeyItem-2)�����<br/> |
| [deleteKeyItem](arkts-universalkeystore-huks-deletekeyitem-f.md#deleteKeyItem-1) | ɾ����Կ��ʹ��callback�첽�ص���<br/> |
| [deleteKeyItem](arkts-universalkeystore-huks-deletekeyitem-f.md#deleteKeyItem-2) | ɾ����Կ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[deleteKeyItemAsUser](arkts-universalkeystore-huks-deletekeyitemasuser-f-sys.md#deleteKeyItemAsUser-1) | ָ���û�����ɾ����Կ��ʹ��Promise��ʽ�첽���ؽ����<br/> |
| [encapsulate](arkts-universalkeystore-huks-encapsulate-f.md#encapsulate-1) | �����Ӽ�����Կ��װ������֧��HUKS��Կ����<br/>����Ӧ�ó��������������Ӧ�ó���ѡ�������Կ��<br/>�Գ���ԿЯ����HuksReturnResult��outData�ֶ��С�<br/> |
| [exportKey](arkts-universalkeystore-huks-exportkey-f.md#exportKey-1) | ������Կ��ʹ��Callback��ʽ�ص��첽���صĽ����<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.exportKeyItem&lt;sup&gt;9+&lt;/sup&gt;](huks.exportKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt;))<br/>&gt; �����<br/> |
| [exportKey](arkts-universalkeystore-huks-exportkey-f.md#exportKey-2) | ������Կ��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.exportKeyItem&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-exportkeyitem-f.md#exportKeyItem-2)�����<br/> |
| [exportKeyItem](arkts-universalkeystore-huks-exportkeyitem-f.md#exportKeyItem-1) | ������Կ��ʹ��callback�첽�ص���<br/> |
| [exportKeyItem](arkts-universalkeystore-huks-exportkeyitem-f.md#exportKeyItem-2) | ������Կ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[exportKeyItemAsUser](arkts-universalkeystore-huks-exportkeyitemasuser-f-sys.md#exportKeyItemAsUser-1) | ָ���û����ݵ�����Կ��ʹ��Promise��ʽ�ص��첽���صĽ����<br/> |
| [finish](arkts-universalkeystore-huks-finish-f.md#finish-1) | finish������Կ�ӿڡ�ʹ��callback�첽�ص���<br/><br/>huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.finishSession&lt;sup&gt;9+&lt;/sup&gt;](huks.finishSession(handle: number, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt;))<br/>&gt; �����<br/> |
| [finish](arkts-universalkeystore-huks-finish-f.md#finish-2) | finish������Կ�ӿڡ�ʹ��Promise�첽�ص���<br/><br/>huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.finishSession&lt;sup&gt;9+&lt;/sup&gt;](huks.finishSession( handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback&lt;HuksReturnResult&gt; ))<br/>&gt; �����<br/> |
| [finishSession](arkts-universalkeystore-huks-finishsession-f.md#finishSession-1) | finishSession������Կ�ӿڡ�ʹ��callback�첽�ص���<br/><br/>huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| [finishSession](arkts-universalkeystore-huks-finishsession-f.md#finishSession-2) | Finishes the key operation. This API uses an asynchronous callback to return the result.<br/>huks.initSession, huks.updateSession, and huks.finishSession must be used together.<br/> |
| [finishSession](arkts-universalkeystore-huks-finishsession-f.md#finishSession-3) | finishSession������Կ�ӿڡ�ʹ��Promise�첽�ص���<br/><br/>huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| [generateKey](arkts-universalkeystore-huks-generatekey-f.md#generateKey-1) | ������Կ��ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.generateKeyItem&lt;sup&gt;9+&lt;/sup&gt;](huks.generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;))<br/>&gt; �����<br/> |
| [generateKey](arkts-universalkeystore-huks-generatekey-f.md#generateKey-2) | ������Կ��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.generateKeyItem&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-generatekeyitem-f.md#generateKeyItem-2)�����<br/> |
| [generateKeyItem](arkts-universalkeystore-huks-generatekeyitem-f.md#generateKeyItem-1) | ������Կ��ʹ��callback�첽�ص���<br/><br/>������Կ����[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#����ִ�л���tee)ԭ�򣬴˽ӿڲ��᷵����Կ�������ݣ�ֻ���ڱ�ʾ�˴ε����Ƿ�ɹ���<br/> |
| [generateKeyItem](arkts-universalkeystore-huks-generatekeyitem-f.md#generateKeyItem-2) | ������Կ��ʹ��Promise�첽�ص���<br/><br/>������Կ����[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#����ִ�л���tee)ԭ�򣬴˽ӿڲ��᷵����Կ�������ݣ�ֻ���ڱ�ʾ�˴ε����Ƿ�ɹ���<br/> |
| <!--DelRow-->[generateKeyItemAsUser](arkts-universalkeystore-huks-generatekeyitemasuser-f-sys.md#generateKeyItemAsUser-1) | ָ���û�����������Կ��ʹ��Promise��ʽ�첽���ؽ����������Կ����[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#����ִ�л���tee)ԭ��ͨ��<br/>promise���᷵����Կ�������ݣ�ֻ���ڱ�ʾ�˴ε����Ƿ�ɹ���<br/> |
| [getKeyItemProperties](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getKeyItemProperties-1) | Obtains key properties. This API uses an asynchronous callback to return the result.<br/> |
| [getKeyItemProperties](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getKeyItemProperties-2) | ��ȡ��Կ���ԡ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getKeyItemPropertiesAsUser](arkts-universalkeystore-huks-getkeyitempropertiesasuser-f-sys.md#getKeyItemPropertiesAsUser-1) | Get properties of the key as user.<br/> |
| [getKeyProperties](arkts-universalkeystore-huks-getkeyproperties-f.md#getKeyProperties-1) | ��ȡ��Կ���ԡ�ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.getKeyItemProperties&lt;sup&gt;9+&lt;/sup&gt;](huks.getKeyItemProperties( keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt; ))<br/>&gt; �����<br/> |
| [getKeyProperties](arkts-universalkeystore-huks-getkeyproperties-f.md#getKeyProperties-2) | ��ȡ��Կ���ԡ�ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.getKeyItemProperties&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getKeyItemProperties-2)<br/>&gt; �����<br/> |
| [getSdkVersion](arkts-universalkeystore-huks-getsdkversion-f.md#getSdkVersion-1) | ��ȡ��ǰϵͳsdk�汾��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 11��ʼ������<br/> |
| [hasKeyItem](arkts-universalkeystore-huks-haskeyitem-f.md#hasKeyItem-1) | �ж���Կ�Ƿ���ڡ�ʹ��callback�첽�ص���<br/><br/>����Կ�����ڣ���ͨ��callback����false��<br/> |
| [hasKeyItem](arkts-universalkeystore-huks-haskeyitem-f.md#hasKeyItem-2) | �ж���Կ�Ƿ���ڡ�ʹ��Promise�첽�ص���<br/><br/>����Կ�����ڣ���ͨ��Promise����false��<br/> |
| <!--DelRow-->[hasKeyItemAsUser](arkts-universalkeystore-huks-haskeyitemasuser-f-sys.md#hasKeyItemAsUser-1) | ָ���û������ж���Կ�Ƿ���ڣ�ʹ��Promise�ص��첽���ؽ����<br/> |
| [importKey](arkts-universalkeystore-huks-importkey-f.md#importKey-1) | ����������Կ��ʹ��Callback��ʽ�ص��첽���ؽ����<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.importKeyItem&lt;sup&gt;9+&lt;/sup&gt;](huks.importKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;))<br/>&gt; �����<br/> |
| [importKey](arkts-universalkeystore-huks-importkey-f.md#importKey-2) | ����������Կ��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.importKeyItem&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-importkeyitem-f.md#importKeyItem-2)�����<br/> |
| [importKeyItem](arkts-universalkeystore-huks-importkeyitem-f.md#importKeyItem-1) | Imports a key in plaintext. This API uses an asynchronous callback to return the result.<br/> |
| [importKeyItem](arkts-universalkeystore-huks-importkeyitem-f.md#importKeyItem-2) | Imports a key in plaintext. This API uses a promise to return the result.<br/> |
| <!--DelRow-->[importKeyItemAsUser](arkts-universalkeystore-huks-importkeyitemasuser-f-sys.md#importKeyItemAsUser-1) | ָ���û����ݵ���������Կ��ʹ��Promise��ʽ�첽���ؽ����<br/> |
| [importWrappedKeyItem](arkts-universalkeystore-huks-importwrappedkeyitem-f.md#importWrappedKeyItem-1) | Imports a wrapped key. This API uses an asynchronous callback to return the result.<br/> |
| [importWrappedKeyItem](arkts-universalkeystore-huks-importwrappedkeyitem-f.md#importWrappedKeyItem-2) | Imports a wrapped key. This API uses a promise to return the result.<br/> |
| <!--DelRow-->[importWrappedKeyItemAsUser](arkts-universalkeystore-huks-importwrappedkeyitemasuser-f-sys.md#importWrappedKeyItemAsUser-1) | Import Wrapped Key As User.<br/> |
| [init](arkts-universalkeystore-huks-init-f.md#init-1) | init������Կ�ӿڡ�ʹ��callback�첽�ص���<br/><br/>huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.initSession&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-initsession-f.md#initSession-2)�����<br/> |
| [init](arkts-universalkeystore-huks-init-f.md#init-2) | init������Կ�ӿڡ�ʹ��Promise�첽�ص���<br/><br/>huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.initSession&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-initsession-f.md#initSession-2)�����<br/> |
| [initSession](arkts-universalkeystore-huks-initsession-f.md#initSession-1) | initSession������Կ�ӿڡ�ʹ��callback�첽�ص���<br/><br/>huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| [initSession](arkts-universalkeystore-huks-initsession-f.md#initSession-2) | initSession������Կ�ӿڡ�ʹ��Promise�첽�ص���<br/><br/>huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| <!--DelRow-->[initSessionAsUser](arkts-universalkeystore-huks-initsessionasuser-f-sys.md#initSessionAsUser-1) | ָ���û����ݲ�����Կ�ӿڣ�ʹ��Promise��ʽ�첽���ؽ����huks.initSessionAsUser, huks.updateSession, huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| [isKeyExist](arkts-universalkeystore-huks-iskeyexist-f.md#isKeyExist-1) | �ж���Կ�Ƿ���ڡ�ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.isKeyItemExist&lt;sup&gt;9+&lt;/sup&gt;](huks.isKeyItemExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;boolean&gt;))<br/>&gt; �����<br/> |
| [isKeyExist](arkts-universalkeystore-huks-iskeyexist-f.md#isKeyExist-2) | �ж���Կ�Ƿ���ڡ�ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.isKeyItemExist&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist-2)�����<br/> |
| [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist-1) | �ж���Կ�Ƿ���ڡ�ʹ��callback�첽�ص���<br/><br/>����Կ�����ڣ����׳�������Ϊ12000011���쳣��<br/> |
| [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist-2) | �ж���Կ�Ƿ���ڡ�ʹ��Promise�첽�ص���<br/><br/>����Կ�����ڣ����׳�������Ϊ12000011���쳣��<br/> |
| [listAliases](arkts-universalkeystore-huks-listaliases-f.md#listAliases-1) | ��ѯ��Կ�������ӿڡ�ʹ��Promise�첽�ص���<br/> |
| [unwrapKeyItem](arkts-universalkeystore-huks-unwrapkeyitem-f.md#unwrapKeyItem-1) | ���ܵ�����Կ��ʹ��Promise�첽�ص���<br/><br/>&lt;!--Del--&gt;�ù����ݲ�֧�֡�&lt;!--DelEnd--&gt;<br/> |
| [update](arkts-universalkeystore-huks-update-f.md#update-1) | update������Կ�ӿڡ�ʹ��callback�첽�ص���<br/><br/>huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.updateSession&lt;sup&gt;9+&lt;/sup&gt;](huks.updateSession( handle: long, options: HuksOptions, token: Uint8Array, callback: AsyncCallback&lt;HuksReturnResult&gt; ))<br/>&gt; �����<br/> |
| [update](arkts-universalkeystore-huks-update-f.md#update-2) | update������Կ�ӿڡ�ʹ��Promise�첽�ص���<br/><br/>huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [huks.updateSession&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-updatesession-f.md#updateSession-3)<br/>&gt; �����<br/> |
| [updateSession](arkts-universalkeystore-huks-updatesession-f.md#updateSession-1) | updateSession������Կ�ӿڡ�ʹ��callback�첽�ص���<br/><br/>huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| [updateSession](arkts-universalkeystore-huks-updatesession-f.md#updateSession-2) | Updates the key operation by segment. This API uses an asynchronous callback to return the result.<br/>huks.initSession, huks.updateSession, and huks.finishSession must be used together.<br/> |
| [updateSession](arkts-universalkeystore-huks-updatesession-f.md#updateSession-3) | updateSession������Կ�ӿڡ�ʹ��Promise�첽�ص���<br/><br/>huks.initSession��huks.updateSession��huks.finishSessionΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�<br/> |
| [wrapKeyItem](arkts-universalkeystore-huks-wrapkeyitem-f.md#wrapKeyItem-1) | ���ܵ�����Կ��ʹ��Promise�첽�ص���<br/><br/>&lt;!--Del--&gt;�ù����ݲ�֧�֡�&lt;!--DelEnd--&gt;<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [HuksHandle](arkts-universalkeystore-huks-hukshandle-i.md) | huks Handle�ṹ�塣<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 9��ʼ����������ʹ��[HuksSessionHandle&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-hukssessionhandle-i.md#HuksSessionHandle)�����<br/> |
| [HuksListAliasesReturnResult](arkts-universalkeystore-huks-hukslistaliasesreturnresult-i.md) | ���ص���Կ�������顣<br/> |
| [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | ���ýӿ�ʹ�õ�options��<br/> |
| [HuksParam](arkts-universalkeystore-huks-huksparam-i.md) | ���ýӿ�ʹ�õ�options�е�properties�����е�param��<br/> |
| [HuksResult](arkts-universalkeystore-huks-huksresult-i.md) | ���ýӿڷ��ص�result��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; - ��API version 8��ʼ����API version 9��ʼ����������ʹ��[HuksReturnResult&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-huksreturnresult-i.md#HuksReturnResult)�����<br/>&gt;<br/>&gt; - errorCode�ľ�����Ϣ����ο�[HUKS������](../../../../reference/apis-universal-keystore-kit/errorcode-huks.md)��<br/> |
| [HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md) | ���ýӿڷ��ص�result��<br/> |
| [HuksSessionHandle](arkts-universalkeystore-huks-hukssessionhandle-i.md) | HUKS handle�ṹ�塣<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HuksAuthAccessType](arkts-universalkeystore-huks-huksauthaccesstype-e.md) | ��ʾ��ȫ���ʿ������͡�<br/> |
| [HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md) | ��ʾ���ɻ�����Կʱ��ָ������Կ�Ĵ洢��ȫ�ȼ���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ҵ����ʹ�ô洢�ȼ�ΪECE����Կʱ������ͨ����֪<br/>&gt; [�����¼�](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_screen_locked)<br/>&gt; ������ʹ�ø���Կ�����ĻỰ��Դ���Ա�֤��ȫ�ԡ�<br/> |
| [HuksChallengePosition](arkts-universalkeystore-huks-hukschallengeposition-e.md) | ��ʾchallenge����Ϊ�û��Զ�������ʱ�����ɵ�challenge��Ч���Ƚ�Ϊ8�ֽ����������ݣ��ҽ�֧��4��λ�á�<br/> |
| [HuksChallengeType](arkts-universalkeystore-huks-hukschallengetype-e.md) | ��ʾ��Կʹ��ʱ����challenge�����͡�<br/> |
| [HuksCipherMode](arkts-universalkeystore-huks-huksciphermode-e.md) | ��ʾ����ģʽ��<br/> |
| [HuksErrorCode](arkts-universalkeystore-huks-hukserrorcode-e.md) | ��ʾ�������ö�١�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 9��ʼ����������ʹ��[HuksExceptionErrCode&lt;sup&gt;9+&lt;/sup&gt;](arkts-universalkeystore-huks-huksexceptionerrcode-e.md#HuksExceptionErrCode)�����<br/> |
| [HuksExceptionErrCode](arkts-universalkeystore-huks-huksexceptionerrcode-e.md) | ��ʾ�������ö���Լ���Ӧ�Ĵ�����Ϣ���������ʾ�������ͣ�������Ϣչʾ�������顣<br/><br/>���ڴ�����ľ�����Ϣ������[ͨ�ô�����](../../../../reference/errorcode-universal.md)��<br/>[HUKS������](../../../../reference/apis-universal-keystore-kit/errorcode-huks.md)�в鿴��<br/> |
| [HuksImportKeyType](arkts-universalkeystore-huks-huksimportkeytype-e.md) | ��ʾ������Կ����Կ���ͣ�Ĭ��Ϊ���빫Կ������Գ���Կʱ����Ҫ���ֶΡ�<br/> |
| [HuksKeyAlg](arkts-universalkeystore-huks-hukskeyalg-e.md) | ��ʾ��Կʹ�õ��㷨��<br/> |
| [HuksKeyClassType](arkts-universalkeystore-huks-hukskeyclasstype-e.md) | ��ʾ��Կ����Դ��<br/> |
| [HuksKeyDigest](arkts-universalkeystore-huks-hukskeydigest-e.md) | ��ʾժҪ�㷨��<br/> |
| [HuksKeyFlag](arkts-universalkeystore-huks-hukskeyflag-e.md) | ��ʾ��Կ�Ĳ�����ʽ��<br/> |
| [HuksKeyGenerateType](arkts-universalkeystore-huks-hukskeygeneratetype-e.md) | ��ʾ������Կ�����͡�<br/> |
| [HuksKeyPadding](arkts-universalkeystore-huks-hukskeypadding-e.md) | ��ʾ����㷨��<br/> |
| [HuksKeyPurpose](arkts-universalkeystore-huks-hukskeypurpose-e.md) | ��ʾ��Կ��;��<br/><br/>һ����Կ�������ڵ�����;�����ܼ����ڼӽ���������ǩ����ǩ��<br/> |
| [HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md) | ��ʾ��Կ��ȫ�����ö�١�<br/> |
| [HuksKeySize](arkts-universalkeystore-huks-hukskeysize-e.md) | ��ʾ��Կ���ȡ�<br/> |
| [HuksKeyStorageType](arkts-universalkeystore-huks-hukskeystoragetype-e.md) | ��ʾ��Կ�洢��ʽ��<br/> |
| [HuksKeyWrapType](arkts-universalkeystore-huks-hukskeywraptype-e.md) | ��ʾ��Կ�������ͣ����ܵ���������Կ����ö�١�<br/> |
| [HuksRsaPssSaltLenType](arkts-universalkeystore-huks-huksrsapsssaltlentype-e.md) | ��ʾRsa��ǩ����ǩ��paddingΪpssʱ��ָ����salt_len���͡�<br/> |
| [HuksSecureSignType](arkts-universalkeystore-huks-hukssecuresigntype-e.md) | ��ʾ���ɻ�����Կʱ��ָ������Կ��ǩ�����͡�<br/> |
| [HuksSendType](arkts-universalkeystore-huks-hukssendtype-e.md) | ��ʾ����TAG�ķ�ʽ��<br/> |
| [HuksTag](arkts-universalkeystore-huks-hukstag-e.md) | ��ʾ���ò�����Tag��<br/> |
| [HuksTagType](arkts-universalkeystore-huks-hukstagtype-e.md) | ��ʾTag���������͡�<br/> |
| [HuksUnwrapSuite](arkts-universalkeystore-huks-huksunwrapsuite-e.md) | ��ʾ��ȫ������Կ���㷨�׼���<br/> |
| [HuksUserAuthMode](arkts-universalkeystore-huks-huksuserauthmode-e.md) | ��ʾ�û���֤ģʽ��<br/> |
| [HuksUserAuthType](arkts-universalkeystore-huks-huksuserauthtype-e.md) | ��ʾ�û���֤���͡�<br/> |

