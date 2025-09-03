# 应用文件上传下载
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->

应用可以将应用文件上传到网络服务器，也可以从网络服务器下载网络资源文件到本地应用文件目录。

## 上传应用文件

开发者可以使用上传下载模块（[ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md)）的上传接口将本地文件上传。文件上传过程使用系统服务代理完成，在api12中request.agent.create接口增加了设置代理地址参数，支持用户设置自定义代理地址。

> **说明：**
>
> 当前上传应用文件功能。request.uploadFile方式仅支持上传应用缓存文件路径（cacheDir）下的文件，request.agent方式支持上传用户公共文件和应用缓存文件路径下的文件。
>
> 使用上传下载模块，需[声明权限](../../security/AccessToken/declare-permissions.md)：ohos.permission.INTERNET。
>
> 上传下载模块不支持Charles、Fiddler等代理抓包工具。

以下示例代码演示两种将缓存文件上传至服务器的方法：

```ts
// 方式一:request.uploadFile
// pages/xxx.ets
import { common } from '@kit.AbilityKit';
import fs from '@ohos.file.fs';
import { BusinessError, request } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("上传").onClick(() => {
          // 获取应用文件路径
          // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let cacheDir = context.cacheDir;

          // 新建一个本地应用文件
          try {
            let file = fs.openSync(cacheDir + '/test.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
            fs.writeSync(file.fd, 'upload file test');
            fs.closeSync(file);
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Invoke uploadFile failed, code is ${err.code}, message is ${err.message}`);
          }

          // 上传任务配置项
          let files: Array<request.File> = [
          //uri前缀internal://cache 对应cacheDir目录
            { filename: 'test.txt', name: 'test', uri: 'internal://cache/test.txt', type: 'txt' }
          ]
          let data: Array<request.RequestData> = [{ name: 'name', value: 'value' }];
          let uploadConfig: request.UploadConfig = {
            url: 'https://xxx',
            header: {
              'key1':'value1',
              'key2':'value2'
            },
            method: 'POST',
            files: files,
            data: data
          }

          // 将本地应用文件上传至网络服务器
          try {
            request.uploadFile(context, uploadConfig)
              .then((uploadTask: request.UploadTask) => {
                uploadTask.on('complete', (taskStates: Array<request.TaskState>) => {
                  for (let i = 0; i < taskStates.length; i++) {
                    console.info(`upload complete taskState: ${JSON.stringify(taskStates[i])}`);
                  }
                });
              })
              .catch((err: BusinessError) => {
                console.error(`Invoke uploadFile failed, code is ${err.code}, message is ${err.message}`);
              })
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Invoke uploadFile failed, code is ${err.code}, message is ${err.message}`);
          }
        })
      }
    }
  }
}
```

```ts
// 方式二:request.agent
// pages/xxx.ets
import { common } from '@kit.AbilityKit';
import fs from '@ohos.file.fs';
import { BusinessError, request } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("上传").onClick(() => {
          // 获取应用文件路径
          // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let cacheDir = context.cacheDir;

          // 新建一个本地应用文件
          let file = fs.openSync(cacheDir + '/test.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
          fs.writeSync(file.fd, 'upload file test');
          fs.closeSync(file);
          let attachments: Array<request.agent.FormItem> = [{
            name: "test",
            value: [
              {
                filename: "test.txt",
                path: "./test.txt",
              },
            ]
          }];
          let config: request.agent.Config = {
            action: request.agent.Action.UPLOAD,
            url: 'http://xxx',
            mode: request.agent.Mode.FOREGROUND,
            overwrite: true,
            method: "POST",
            headers: {
              'key1':'value1',
              'key2':'value2'
            },
            data: attachments,
            saveas: "./"
          };
          request.agent.create(context, config).then((task: request.agent.Task) => {
            task.start((err: BusinessError) => {
              if (err) {
                console.error(`Failed to start the upload task, Code: ${err.code}  message: ${err.message}`);
                return;
              }
            });
            task.on('progress', async(progress) => {
              console.warn(`/Request upload status ${progress.state}, uploaded ${progress.processed}`);
            })
            task.on('completed', async() => {
              console.warn(`/Request upload completed`);
              //该方法需用户管理任务生命周期，任务结束后调用remove释放task对象
              request.agent.remove(task.tid);
            })
          }).catch((err: BusinessError) => {
            console.error(`Failed to create a upload task, Code: ${err.code}, message: ${err.message}`);
          });
        })
      }
    }
  }
}

```

## 下载网络资源文件至应用文件目录

开发者可以使用上传下载模块（[ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md)）的下载接口将网络资源文件下载到应用文件目录。对已下载的网络资源文件，开发者可以使用基础文件IO接口（[ohos.file.fs](../../reference/apis-core-file-kit/js-apis-file-fs.md)）对其进行访问，使用方式与[应用文件访问](../../file-management/app-file-access.md)一致。文件下载过程使用系统服务代理完成，在api12中request.agent.create接口增加了设置代理地址参数，支持用户设置自定义代理地址。

> **说明：**
>
> 当前网络资源文件仅支持下载至应用文件目录。
>
> 使用上传下载模块，需[声明权限](../../security/AccessToken/declare-permissions.md)：ohos.permission.INTERNET。

以下示例代码演示两种下载网络资源文件到应用文件目录的方式：

```ts
// 方式一:request.downloadFile
// pages/xxx.ets
// 将网络资源文件下载到应用文件目录并读取一段内容
import { common } from '@kit.AbilityKit';
import fs from '@ohos.file.fs';
import { BusinessError, request } from '@kit.BasicServicesKit';
import { buffer } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("下载").onClick(() => {
          // 获取应用文件路径
          // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let filesDir = context.filesDir;

          try {
            request.downloadFile(context, {
              url: 'https://xxxx/xxxx.txt',
              filePath: filesDir + '/xxxx.txt'
            }).then((downloadTask: request.DownloadTask) => {
              downloadTask.on('complete', () => {
                console.info('download complete');
                let file = fs.openSync(filesDir + '/xxxx.txt', fs.OpenMode.READ_WRITE);
                let arrayBuffer = new ArrayBuffer(1024);
                let readLen = fs.readSync(file.fd, arrayBuffer);
                let buf = buffer.from(arrayBuffer, 0, readLen);
                console.info(`The content of file: ${buf.toString()}`);
                fs.closeSync(file);
              })
            }).catch((err: BusinessError) => {
              console.error(`Invoke downloadTask failed, code is ${err.code}, message is ${err.message}`);
            });
          } catch (error) {
            let err: BusinessError = error as BusinessError;
            console.error(`Invoke downloadFile failed, code is ${err.code}, message is ${err.message}`);
          }
        })
      }
    }
  }
}
```
```ts
// 方式二:request.agent
// pages/xxx.ets
// 将网络资源文件下载到应用文件目录并读取一段内容
import { common } from '@kit.AbilityKit';
import fs from '@ohos.file.fs';
import { BusinessError, request } from '@kit.BasicServicesKit';
import { buffer } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("下载").onClick(() => {
          // 获取应用文件路径
          // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let filesDir = context.filesDir;

          let config: request.agent.Config = {
            action: request.agent.Action.DOWNLOAD,
            url: 'https://xxxx/test.txt',
            saveas: 'xxxx.txt',
            gauge: true,
            overwrite: true,
            network: request.agent.Network.WIFI,
          };
          request.agent.create(context, config).then((task: request.agent.Task) => {
            task.start((err: BusinessError) => {
              if (err) {
                console.error(`Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
                return;
              }
            });
            task.on('progress', async (progress) => {
              console.warn(`/Request download status ${progress.state}, downloaded ${progress.processed}`);
            })
            task.on('completed', async () => {
              console.warn(`/Request download completed`);
              let file = fs.openSync(filesDir + '/xxxx.txt', fs.OpenMode.READ_WRITE);
              let arrayBuffer = new ArrayBuffer(1024);
              let readLen = fs.readSync(file.fd, arrayBuffer);
              let buf = buffer.from(arrayBuffer, 0, readLen);
              console.info(`The content of file: ${buf.toString()}`);
              fs.closeSync(file);
              //该方法需用户管理任务生命周期，任务结束后调用remove释放task对象
              request.agent.remove(task.tid);
            })
          }).catch((err: BusinessError) => {
            console.error(`Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
          });
        })
      }
    }
  }
}

```

## 添加网络配置

### HTTP拦截

开发者可以通过设置配置文件实现HTTP拦截功能，上传下载模块在应用配置文件中禁用HTTP后，无法创建明文HTTP传输的上传下载任务。配置文件在APP中的路径是：`src/main/resources/base/profile/network_config.json`。请参考网络管理模块[配置文件](../../reference/apis-network-kit/js-apis-net-connection.md#connectionsetapphttpproxy11)配置参数

参考配置文件如下：

```ts
{
  "network-security-config": {
    "base-config": {
      "cleartextTrafficPermitted": true, 
      "trust-anchors": [
        {
          "certificates": "/etc/security/certificates"
        }
      ]
    },
    "domain-config": [
      {
        "cleartextTrafficPermitted": true,
        "domains": [
          {
            "include-subdomains": true,
            "name": "*.example.com"
          }
        ],
      }
    ]
  }
}
```

