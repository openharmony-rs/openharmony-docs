| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API废弃版本变更|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_TYPE = 'image/*'<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：VIDEO_TYPE = 'video/*'<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：NA|类名：PhotoViewMIMETypes；<br>API声明：IMAGE_VIDEO_TYPE = '*/*'<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：NA|类名：PhotoSelectOptions；<br>API声明：MIMEType?: PhotoViewMIMETypes;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：NA|类名：PhotoSelectOptions；<br>API声明：maxSelectNumber?: number;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：NA|类名：PhotoSelectResult；<br>API声明：photoUris: Array\<string>;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：NA|类名：PhotoSelectResult；<br>API声明：isOriginalPhoto: boolean;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|API废弃版本变更|类名：PhotoSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：NA|类名：PhotoSaveOptions；<br>API声明：newFileNames?: Array\<string>;<br>差异内容：18|api/@ohos.file.picker.d.ts|
|删除错误码|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：201|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：NA|api/@ohos.fileshare.d.ts|
|权限变更|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：ohos.permission.FILE_ACCESS_PERSIST|类名：fileShare；<br>API声明：function checkPersistentPermission(policies: Array\<PolicyInfo>): Promise\<Array\<boolean>>;<br>差异内容：NA|api/@ohos.fileshare.d.ts|
|起始版本有变化|类名：storageStatistics；<br>API声明：function getTotalSize(callback: AsyncCallback\<number>): void;<br>差异内容：9|类名：storageStatistics；<br>API声明：function getTotalSize(callback: AsyncCallback\<number>): void;<br>差异内容：15|api/@ohos.file.storageStatistics.d.ts|
|起始版本有变化|类名：storageStatistics；<br>API声明：function getTotalSize(): Promise\<number>;<br>差异内容：9|类名：storageStatistics；<br>API声明：function getTotalSize(): Promise\<number>;<br>差异内容：15|api/@ohos.file.storageStatistics.d.ts|
|起始版本有变化|类名：storageStatistics；<br>API声明：function getTotalSizeSync(): number;<br>差异内容：10|类名：storageStatistics；<br>API声明：function getTotalSizeSync(): number;<br>差异内容：15|api/@ohos.file.storageStatistics.d.ts|
|起始版本有变化|类名：storageStatistics；<br>API声明：function getFreeSize(callback: AsyncCallback\<number>): void;<br>差异内容：9|类名：storageStatistics；<br>API声明：function getFreeSize(callback: AsyncCallback\<number>): void;<br>差异内容：15|api/@ohos.file.storageStatistics.d.ts|
|起始版本有变化|类名：storageStatistics；<br>API声明：function getFreeSize(): Promise\<number>;<br>差异内容：9|类名：storageStatistics；<br>API声明：function getFreeSize(): Promise\<number>;<br>差异内容：15|api/@ohos.file.storageStatistics.d.ts|
|起始版本有变化|类名：storageStatistics；<br>API声明：function getFreeSizeSync(): number;<br>差异内容：10|类名：storageStatistics；<br>API声明：function getFreeSizeSync(): number;<br>差异内容：15|api/@ohos.file.storageStatistics.d.ts|
