# @ohos.file.cloudSync

��ģ����Ӧ���ṩ����ͬ����������������/ֹͣ����ͬ���Լ�����/ֹͣԭͼ���ع��ܡ�

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCoreFileSyncState](arkts-corefile-cloudsync-getcorefilesyncstate-f.md#getCoreFileSyncState-1) | ͬ��������ȡ�����ļ�ͬ������״̬��<br/> |
| <!--DelRow-->[getFileSyncState](arkts-corefile-cloudsync-getfilesyncstate-f-sys.md#getFileSyncState-1) | �첽������ȡ�ļ�ͬ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getFileSyncState](arkts-corefile-cloudsync-getfilesyncstate-f-sys.md#getFileSyncState-2) | �첽������ȡ�ļ�ͬ��״̬��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getFileSyncState](arkts-corefile-cloudsync-getfilesyncstate-f-sys.md#getFileSyncState-3) | ��ȡ�ļ�ͬ��״̬��<br/> |
| <!--DelRow-->[optimizeStorage](arkts-corefile-cloudsync-optimizestorage-f-sys.md#optimizeStorage-1) | �Ż�ͼ����ͬ���ƿռ�ı�����Դ�����ձ���ʣ��ռ�ִ���Զ��ϻ����ԡ�ʹ��Promise�첽�ص���<br/> |
| [registerChange](arkts-corefile-cloudsync-registerchange-f.md#registerChange-1) | ���ļ���ָ���ļ��ı仯֪ͨ��callback���ظ��ĵ����ݡ�<br/> |
| <!--DelRow-->[startOptimizeSpace](arkts-corefile-cloudsync-startoptimizespace-f-sys.md#startOptimizeSpace-1) | �Ż�ͼ����ͬ���ƿռ�ı�����Դ��ִ�������Ż��ռ���ԣ����ϻ�����ǰδ���ʵı���ͼƬ/��Ƶ�����Ż���ʹ��Promise�첽�ص���callback�����Ż����ȡ�<br/><br/>startOptimizeSpace��ʹ�ú�stopOptimizeSpace��������һһ��Ӧ���ظ�����������������������ִ�еĴ�����Ϣ��22400006����<br/> |
| <!--DelRow-->[stopOptimizeSpace](arkts-corefile-cloudsync-stopoptimizespace-f-sys.md#stopOptimizeSpace-1) | ͬ������ֹͣͼ����ͼ��Դ�ռ��Ż�����startOptimizeSpace���ʹ�á�<br/> |
| [unregisterChange](arkts-corefile-cloudsync-unregisterchange-f.md#unregisterChange-1) | ȡ�����ļ���ָ���ļ��ı仯֪ͨ��<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [CloudFileCache](arkts-corefile-cloudsync-cloudfilecache-c.md) | �����ļ������������֧���ļ�����Ӧ��ԭ�ļ��������̡�<br/> |
| <!--DelRow-->[CloudFileCache](arkts-corefile-cloudsync-cloudfilecache-c-sys.md) | �����ļ������������֧���ļ�����Ӧ��ԭ�ļ��������̡�<br/> |
| <!--DelRow-->[Download](arkts-corefile-cloudsync-download-c-sys.md) | ���ļ����ض�������֧��ͼ��Ӧ��ԭͼ�ļ��������̡���ʹ��ǰ����Ҫ�ȴ���Downloadʵ����<br/> |
| [FileSync](arkts-corefile-cloudsync-filesync-c.md) | ����ͬ����������֧���ļ�������Ӧ����������ļ��Ķ���ͬ�����̡���ʹ��ǰ����Ҫ�ȴ���FileSyncʵ����<br/> |
| <!--DelRow-->[FileSync](arkts-corefile-cloudsync-filesync-c-sys.md) | ����ͬ����������֧���ļ�������Ӧ����������ļ��Ķ���ͬ�����̡���ʹ��ǰ����Ҫ�ȴ���FileSyncʵ����<br/> |
| [FileVersion](arkts-corefile-cloudsync-fileversion-c.md) | �����ļ��汾�����ࡣ֧�ֶԶ����ļ�����ʷ�汾���й������ṩ��ȡ�ļ���ʷ�汾��Ϣ�б���������ͨ����ʷ�汾��Ϣ���ɽ���ʷ�汾���ص����أ����ṩ��ʷ�汾�ļ��滻��ǰ�����ļ�����������԰汾��ͻ���ṩ��ѯ��ͻ��־�������ͻ��־��������<br/> |
| <!--DelRow-->[GallerySync](arkts-corefile-cloudsync-gallerysync-c-sys.md) | ��ͼͬ����������֧��ͼ��Ӧ��ý����Դ����ͬ�����̡���ʹ��ǰ����Ҫ�ȴ���GallerySyncʵ����<br/> |
| [MultiDownloadProgress](arkts-corefile-cloudsync-multidownloadprogress-c.md) | ���ļ���������Ľ�����Ϣ��<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChangeData](arkts-corefile-cloudsync-changedata-i.md) | ���������ݡ�<br/> |
| [DownloadProgress](arkts-corefile-cloudsync-downloadprogress-i.md) | ���ļ����ع��̡�<br/> |
| [FailedFileInfo](arkts-corefile-cloudsync-failedfileinfo-i.md) | ���ļ���������ʧ���б���ʧ��ԭ��<br/> |
| [HistoryVersion](arkts-corefile-cloudsync-historyversion-i.md) | �����ļ���ʷ�汾��Ϣ�����ö����ļ��汾������[FileVersion](arkts-corefile-cloudsync-fileversion-c.md#FileVersion)��<br/>[gethistoryversionlist](arkts-corefile-cloudsync-fileversion-c.md#getHistoryVersionList-1)����ʱ����ʷ�汾�б��е����ԡ�<br/> |
| <!--DelRow-->[OptimizeSpaceParam](arkts-corefile-cloudsync-optimizespaceparam-i-sys.md) | �����Ż��ռ����ò����������Ż��ܿռ���ϻ�������<br/> |
| <!--DelRow-->[OptimizeSpaceProgress](arkts-corefile-cloudsync-optimizespaceprogress-i-sys.md) | �����Ż��ռ�״̬�͵�ǰ���ȡ�<br/> |
| [SyncProgress](arkts-corefile-cloudsync-syncprogress-i.md) | ����ͬ�����̡�<br/> |
| <!--DelRow-->[UploadProgress](arkts-corefile-cloudsync-uploadprogress-i-sys.md) | �ļ��ϴ�������Ϣ��<br/> |
| [VersionDownloadProgress](arkts-corefile-cloudsync-versiondownloadprogress-i.md) | ��ʷ�汾�ļ�����״̬�ͽ�����Ϣ�����ö����ļ��汾������[FileVersion](arkts-corefile-cloudsync-fileversion-c.md#FileVersion)��<br/>[downloadHistoryVersion](arkts-corefile-cloudsync-fileversion-c.md#downloadHistoryVersion-1)����ʱ���ص�������������͡�<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DownloadErrorType](arkts-corefile-cloudsync-downloaderrortype-e.md) | �������ش������ͣ�Ϊö�����͡�<br/> |
| [DownloadFileType](arkts-corefile-cloudsync-downloadfiletype-e.md) | ���̻����ļ����͵�ö�١�<br/> |
| [ErrorType](arkts-corefile-cloudsync-errortype-e.md) | ����ͬ��ʧ�����ͣ�Ϊö�����͡�<br/><br/>- ��ǰ�׶Σ�ͬ�������У�������������ʹ���ƶ��������磬�ƶ����������WIFI��������ʱ���Ż᷵��NETWORK_UNAVAILABLE������������ʹ���ƶ��������磬����һ������������ã���������ͬ����<br/>- ͬ�������У��ǳ�糡���£���������10%����ɵ�ǰ������ͬ����ֹͣͬ�������ص͵�����<br/>- ����ͬ��ʱ���ǳ�糡���£�����������10%��������ͬ��<br/>- ����ʱ�����ƶ˿ռ䲻�㣬���ļ�����ʧ�ܣ��ƶ��޸��ļ���¼��<br/> |
| <!--DelRow-->[ErrorType](arkts-corefile-cloudsync-errortype-e-sys.md) | ����ͬ��ʧ�����ͣ�Ϊö�����͡�<br/><br/>- ��ǰ�׶Σ�ͬ�������У�������������ʹ���ƶ��������磬�ƶ����������WIFI��������ʱ���Ż᷵��NETWORK_UNAVAILABLE������������ʹ���ƶ��������磬����һ������������ã���������ͬ����<br/>- ͬ�������У��ǳ�糡���£���������10%����ɵ�ǰ������ͬ����ֹͣͬ�������ص͵�����<br/>- ����ͬ��ʱ���ǳ�糡���£�����������10%��������ͬ��<br/>- ����ʱ�����ƶ˿ռ䲻�㣬���ļ�����ʧ�ܣ��ƶ��޸��ļ���¼��<br/> |
| [FileState](arkts-corefile-cloudsync-filestate-e.md) | �����ļ�ͬ��״̬��Ϊö�����͡�<br/> |
| <!--DelRow-->[FileSyncState](arkts-corefile-cloudsync-filesyncstate-e-sys.md) | �����ļ�ͬ��״̬��Ϊö�����͡�<br/> |
| [NotifyType](arkts-corefile-cloudsync-notifytype-e.md) | ���ݱ��֪ͨ���͡�<br/> |
| <!--DelRow-->[OptimizeState](arkts-corefile-cloudsync-optimizestate-e-sys.md) | �Ż��ռ�״̬��Ϊö�����͡�<br/> |
| [State](arkts-corefile-cloudsync-state-e.md) | ���ļ�����״̬��Ϊö�����͡�<br/> |
| <!--DelRow-->[State](arkts-corefile-cloudsync-state-e-sys.md) | ���ļ�����״̬��Ϊö�����͡�<br/> |
| [SyncState](arkts-corefile-cloudsync-syncstate-e.md) | ����ͬ��״̬��Ϊö�����͡�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ����ͬ��״̬�������ʱ�����Ӧ��ע����ͬ�������¼���������ͨ���ص�֪ͨӦ�á�<br/> |
| <!--DelRow-->[UploadState](arkts-corefile-cloudsync-uploadstate-e-sys.md) | �ļ��ϴ�״̬��ö�١�<br/> |

