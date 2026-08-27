# request接口切换


  | FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| download(config:&nbsp;DownloadConfig,&nbsp;callback:&nbsp;AsyncCallback&lt;DownloadTask&gt;):&nbsp;void;<br/>download(config:&nbsp;DownloadConfig):&nbsp;Promise&lt;DownloadTask&gt;; | \@ohos.request.d.ts | downloadFile(context:&nbsp;BaseContext,&nbsp;config:&nbsp;DownloadConfig,&nbsp;callback:&nbsp;AsyncCallback&lt;DownloadTask&gt;):&nbsp;void;<br/>downloadFile(context:&nbsp;BaseContext,&nbsp;config:&nbsp;DownloadConfig):&nbsp;Promise&lt;DownloadTask&gt;; |
| upload(config:&nbsp;UploadConfig,&nbsp;callback:&nbsp;AsyncCallback&lt;UploadTask&gt;):&nbsp;void;<br/>upload(config:&nbsp;UploadConfig):&nbsp;Promise&lt;UploadTask&gt;; | \@ohos.request.d.ts | uploadFile(context:&nbsp;BaseContext,&nbsp;config:&nbsp;UploadConfig,&nbsp;callback:&nbsp;AsyncCallback&lt;UploadTask&gt;):&nbsp;void;<br/>uploadFile(context:&nbsp;BaseContext,&nbsp;config:&nbsp;UploadConfig):&nbsp;Promise&lt;UploadTask&gt;; |
