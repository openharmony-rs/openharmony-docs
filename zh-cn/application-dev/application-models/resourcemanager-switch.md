# resourceManager接口切换


  | FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应字段 | 
| -------- | -------- | -------- |
| getResourceManager(callback:&nbsp;AsyncCallback&lt;ResourceManager&gt;):&nbsp;void;<br/>getResourceManager(bundleName:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;ResourceManager&gt;):&nbsp;void;<br/>getResourceManager():&nbsp;Promise&lt;ResourceManager&gt;;<br/>getResourceManager(bundleName:&nbsp;string):&nbsp;Promise&lt;ResourceManager&gt;; | application\Context.d.ts | resourceManager:&nbsp;resmgr.ResourceManager; |
