# @ohos.bundle.appControl

��ģ���ṩӦ��������������Ӧ�����ô���״̬��Ӧ�ûᱻ��ֹ���У��û��������ͼ��ʱ�������Ӧ�õĴ���״̬����ת����Ӧ��ҳ�档��ģ��֧�ֶ�Ӧ�õĴ���״̬�������á���ȡ��ɾ����

> **˵����**
>
> ��ģ��Ϊϵͳ�ӿڡ�

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[deleteDisposedStatus](arkts-ability-appcontrol-deletedisposedstatus-f-sys.md#deleteDisposedStatus-1) | ɾ��Ӧ�õĴ���״̬��ʹ��callback�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��<br/> |
| <!--DelRow-->[deleteDisposedStatus](arkts-ability-appcontrol-deletedisposedstatus-f-sys.md#deleteDisposedStatus-2) | ɾ��Ӧ�õĴ���״̬��ʹ��promise�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��<br/> |
| <!--DelRow-->[deleteDisposedStatusSync](arkts-ability-appcontrol-deletedisposedstatussync-f-sys.md#deleteDisposedStatusSync-1) | ��ͬ������ɾ��ָ��Ӧ�û����Ӧ�õĴ���״̬���ɹ�����null��ʧ���׳���Ӧ�쳣��<br/> |
| <!--DelRow-->[deleteUninstallDisposedRule](arkts-ability-appcontrol-deleteuninstalldisposedrule-f-sys.md#deleteUninstallDisposedRule-1) | ɾ��ָ��Ӧ�û����Ӧ�õ�ж�ش��ù���<br/> |
| <!--DelRow-->[getAllDisposedRules](arkts-ability-appcontrol-getalldisposedrules-f-sys.md#getAllDisposedRules-1) | ��ȡ��ǰ�û��������õ��������ع���<br/> |
| <!--DelRow-->[getDisposedRule](arkts-ability-appcontrol-getdisposedrule-f-sys.md#getDisposedRule-1) | ��ȡָ��Ӧ�û����Ӧ�������õ����ع���<br/> |
| <!--DelRow-->[getDisposedRulesByBundle](arkts-ability-appcontrol-getdisposedrulesbybundle-f-sys.md#getDisposedRulesByBundle-1) | ��ȡָ��Ӧ�ó�������õ��������ع���<br/> |
| <!--DelRow-->[getDisposedStatus](arkts-ability-appcontrol-getdisposedstatus-f-sys.md#getDisposedStatus-1) | ��ȡָ��Ӧ�õĴ���״̬��ʹ��callback�첽�ص����ɹ�����Ӧ�õĴ���״̬��ʧ�ܷ��ض�Ӧ������Ϣ��<br/> |
| <!--DelRow-->[getDisposedStatus](arkts-ability-appcontrol-getdisposedstatus-f-sys.md#getDisposedStatus-2) | ��ȡָ��Ӧ�������õĴ���״̬��ʹ��Promise�첽�ص����ɹ�����Ӧ�õĴ���״̬��ʧ�ܷ��ض�Ӧ������Ϣ��<br/> |
| <!--DelRow-->[getDisposedStatusSync](arkts-ability-appcontrol-getdisposedstatussync-f-sys.md#getDisposedStatusSync-1) | ��ͬ��������ȡָ��Ӧ�������õĴ���״̬���ɹ�����Ӧ�õĴ���״̬��ʧ���׳���Ӧ�쳣��<br/> |
| <!--DelRow-->[getUninstallDisposedRule](arkts-ability-appcontrol-getuninstalldisposedrule-f-sys.md#getUninstallDisposedRule-1) | ��ȡָ��Ӧ�û����Ӧ�������õ����ȼ���ߵ�ж�ش��ù���<br/> |
| <!--DelRow-->[setDisposedRule](arkts-ability-appcontrol-setdisposedrule-f-sys.md#setDisposedRule-1) | ����ָ��Ӧ�û����Ӧ�õ����ع���<br/> |
| <!--DelRow-->[setDisposedRules](arkts-ability-appcontrol-setdisposedrules-f-sys.md#setDisposedRules-1) | ��������ָ��Ӧ�û����Ӧ�õ����ع���<br/> |
| <!--DelRow-->[setDisposedStatus](arkts-ability-appcontrol-setdisposedstatus-f-sys.md#setDisposedStatus-1) | ����Ӧ�õĴ���״̬��ʹ��callback�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��<br/> |
| <!--DelRow-->[setDisposedStatus](arkts-ability-appcontrol-setdisposedstatus-f-sys.md#setDisposedStatus-2) | ����Ӧ�õĴ���״̬��ʹ��Promise�첽�ص����ɹ�����null��ʧ�ܷ��ض�Ӧ������Ϣ��<br/> |
| <!--DelRow-->[setDisposedStatusSync](arkts-ability-appcontrol-setdisposedstatussync-f-sys.md#setDisposedStatusSync-1) | ��ͬ����������Ӧ�õĴ���״̬���ɹ�����null��ʧ���׳���Ӧ�쳣��<br/> |
| <!--DelRow-->[setUninstallDisposedRule](arkts-ability-appcontrol-setuninstalldisposedrule-f-sys.md#setUninstallDisposedRule-1) | ����ָ��Ӧ�û����Ӧ�õ�ж�ش��ù���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md) | ��ʶ���ع���<br/> |
| <!--DelRow-->[DisposedRuleConfiguration](arkts-ability-appcontrol-disposedruleconfiguration-i-sys.md) | ��ʶ�����������ع�������á�<br/> |
| <!--DelRow-->[UninstallDisposedRule](arkts-ability-appcontrol-uninstalldisposedrule-i-sys.md) | ��ʶж�ش��ù���<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[ComponentType](arkts-ability-appcontrol-componenttype-e-sys.md) | ��ʶ����������͡�<br/> |
| <!--DelRow-->[ControlType](arkts-ability-appcontrol-controltype-e-sys.md) | ��ʶ����ָ��Ӧ�ó���Ĳ�ͬ���ԡ�<br/> |
| <!--DelRow-->[DisposedType](arkts-ability-appcontrol-disposedtype-e-sys.md) | ��ʶ����Ӧ�ó���ķ�ʽ���������Ӧ�õ�ȫ������������Ӧ�õ�ָ�����������߲����á�<br/> |
| <!--DelRow-->[UninstallComponentType](arkts-ability-appcontrol-uninstallcomponenttype-e-sys.md) | ��ʶж��ʱ����������͡�<br/> |

