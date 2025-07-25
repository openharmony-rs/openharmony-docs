# Uploading and Downloading Application Files

This topic describes how to upload an application file to a network server and download a network resource file from a network server to a local application file directory.

## Uploading Application Files

You can use **uploadFile()** in [ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md) to upload local files. The system service agent uploads the files. In API version 12, you can set the address of the agent in **request.agent.create()**.

> **NOTE**
>
> Currently, only files in the **cacheDir** directory can be uploaded using **request.uploadFile**; user public files and files in the **cacheDir** directory can be uploaded together using **request.agent**.
>
> To use **uploadFile()** in **ohos.request**, you need to [declare permissions](../../security/AccessToken/declare-permissions.md): ohos.permission.INTERNET.

The following code demonstrates how to upload files from a cache directory of an application to a network server in two approaches:

```ts
// Approach 1: Use request.uploadFile.
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
        Button("Upload").onClick(() => {
          // Obtain the application file path.
          // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let cacheDir = context.cacheDir;

          // Create an application file locally.
          let file = fs.openSync(cacheDir + '/test.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
          fs.writeSync(file.fd, 'upload file test');
          fs.closeSync(file);

          // Configure the upload task.
          let files: Array<request.File> = [
          // "internal://cache" in uri corresponds to the cacheDir directory.
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

          // Upload the created application file to the network server.
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
// Approach 2: Use request.agent.
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
        Button("Upload").onClick(() => {
          // Obtain the application file path.
          // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          let cacheDir = context.cacheDir;

          // Create an application file locally.
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
              // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
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

## Downloading Network Resource Files to an Application Directory

You can use **downloadFile()** in [ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md) to download network resource files to a local application directory. You can use the [ohos.file.fs](../../reference/apis-core-file-kit/js-apis-file-fs.md) APIs to access the downloaded files. For details, see [Accessing Application Files](../../file-management/app-file-access.md). The system service agent downloads the files. In API version 12, you can set the address of the agent in **request.agent.create()**.

> **NOTE**
>
> Currently, network resource files can be downloaded only to the application file directory.
>
> To use **uploadFile()** in **ohos.request**, you need to [declare permissions](../../security/AccessToken/declare-permissions.md): ohos.permission.INTERNET.

The following code demonstrates how to download files from a network server to an application directory in two approaches:

```ts
// Approach 1: Use request.downloadFile.
// pages/xxx.ets
// Download the network resource file to the local application file directory, and read data from the file.
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
        Button("Download").onClick(() => {
          // Obtain the application file path.
          // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
// Approach 2: Use request.agent.
// pages/xxx.ets
// Download the network resource file to the local application file directory, and read data from the file.
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
        Button("Download").onClick(() => {
          // Obtain the application file path.
          // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
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
              // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
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

## Downloading Network Resource Files to the User File
You can use the [request.agent](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentcreate10) API of the upload and download module ([ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md)) to download network resource files to the user file.

### Downloading Documents

Call the [save()](../../reference/apis-core-file-kit/js-apis-file-picker.md#save) API of [DocumentViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#documentviewpicker) to save a document and obtain the URI of the user file. Use this URI as the value of the **saveas** field of [Config](../../reference/apis-basic-services-kit/js-apis-request.md#config10) to download the document.

```ts
import { BusinessError, request } from '@kit.BasicServicesKit';
import { picker } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("Download Document").width("50%").margin({ top: 20 }).height(40).onClick(async () => {
          // Create a documentSaveOptions instance.
          const documentSaveOptions = new picker.DocumentSaveOptions();
          // (Optional) Name of the file to save. The default value is empty.
          documentSaveOptions.newFileNames = ["xxxx.txt"];
          // (Optional) Type of the document to save. The value is in ['Description|File name extensions'] format. To save all files, use 'All files (*.*)|.*'. If there are multiple file name extensions (a maximum of 100 extensions can be filtered), the first one is used by default. If this parameter is not specified, no extension is filtered by default.
          documentSaveOptions.fileSuffixChoices = ['Document|.txt', '.pdf'];

          let uri: string = '';
          // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          const documentViewPicker = new picker.DocumentViewPicker(context);
          await documentViewPicker.save(documentSaveOptions).then((documentSaveResult: Array<string>) => {
            uri = documentSaveResult[0];
            console.info('DocumentViewPicker.save to file succeed and uri is:' + uri);
          }).catch((err: BusinessError) => {
            console.error(`Invoke documentViewPicker.save failed, code is ${err.code}, message is ${err.message}`);
          })
          if (uri != '') {
            let config: request.agent.Config = {
              action: request.agent.Action.DOWNLOAD,
              url: 'https://xxxx/xxxx.txt',
              // The saveas field specifies the URI of the file saved by DocumentViewPicker.
              saveas: uri,
              gauge: true,
              // The overwrite field must be set to true.
              overwrite: true,
              network: request.agent.Network.WIFI,
              // The mode field must be set to request.agent.Mode.FOREGROUND.
              mode: request.agent.Mode.FOREGROUND,
            };
            try {
              request.agent.create(context, config).then((task: request.agent.Task) => {
                task.start((err: BusinessError) => {
                  if (err) {
                    console.error(`Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
                    return;
                  }
                });
                task.on('progress', async (progress) => {
                  console.warn(`Request download status ${progress.state}, downloaded ${progress.processed}`);
                })
                task.on('completed', async (progress) => {
                  console.warn('Request download completed, ' + JSON.stringify(progress));
                  // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
                  request.agent.remove(task.tid);
                })
              }).catch((err: BusinessError) => {
                console.error(`Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
              });
            } catch (err) {
              console.error(`Failed to create a download task, err: ${err}`);
            }
          }
        })
      }
    }
  }
}
```

### Downloading Audios

Call the [save()](../../reference/apis-core-file-kit/js-apis-file-picker.md#save-3) API of [AudioViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#audioviewpicker) to save an audio and obtain the URI of the user file. Use this URI as the value of the **saveas** field of [Config](../../reference/apis-basic-services-kit/js-apis-request.md#config10) to download the audio.

```ts
import { BusinessError, request } from '@kit.BasicServicesKit';
import { picker } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("Download Audio").width("50%").margin({ top: 20 }).height(40).onClick(async () => {
          // Create a documentSaveOptions instance.
          const audioSaveOptions = new picker.AudioSaveOptions();
          // (Optional) Name of the file to save. The default value is empty.
          audioSaveOptions.newFileNames = ['xxxx.mp3'];

          let uri: string = '';
          // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
          let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
          const audioViewPicker = new picker.AudioViewPicker(context);
          await audioViewPicker.save(audioSaveOptions).then((audioSelectResult: Array<string>) => {
            uri = audioSelectResult[0];
            console.info('AudioViewPicker.save to file succeed and uri is:' + uri);
          }).catch((err: BusinessError) => {
            console.error(`Invoke audioViewPicker.save failed, code is ${err.code}, message is ${err.message}`);
          })
          if (uri != '') {
            let config: request.agent.Config = {
              action: request.agent.Action.DOWNLOAD,
              url: 'https://xxxx/xxxx.mp3',
              // The saveas field specifies the URI of the file saved by AudioViewPicker.
              saveas: uri,
              gauge: true,
              // The overwrite field must be set to true.
              overwrite: true,
              network: request.agent.Network.WIFI,
              // The mode field must be set to request.agent.Mode.FOREGROUND.
              mode: request.agent.Mode.FOREGROUND,
            };
            try {
              request.agent.create(context, config).then((task: request.agent.Task) => {
                task.start((err: BusinessError) => {
                  if (err) {
                    console.error(`Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
                    return;
                  }
                });
                task.on('progress', async (progress) => {
                  console.warn(`Request download status ${progress.state}, downloaded ${progress.processed}`);
                })
                task.on('completed', async (progress) => {
                  console.warn('Request download completed, ' + JSON.stringify(progress));
                  // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
                  request.agent.remove(task.tid);
                })
              }).catch((err: BusinessError) => {
                console.error(`Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
              });
            } catch (err) {
              console.error(`Failed to create a download task, err: ${err}`);
            }
          }
        })
      }
    }
  }
}
```

### Downloading Images or Videos

Call the [createAsset()](../../reference/apis-media-library-kit/js-apis-photoAccessHelper.md#createasset-2) API of [PhotoAccessHelper](../../reference/apis-media-library-kit/js-apis-photoAccessHelper.md) to create a media file and obtain the URI of the user file. Use this URI as the value of the **saveas** field of [Config](../../reference/apis-basic-services-kit/js-apis-request.md#config10) to download the media file.

Permission required: [ohos.permission.WRITE_IMAGEVIDEO](../../security/AccessToken/permissions-for-all-user.md#ohospermissionwrite_media)

[ohos.permission.WRITE_IMAGEVIDEO](../../security/AccessToken/permissions-for-all-user.md#ohospermissionwrite_media) is a [restricted permission](../../security/AccessToken/restricted-permissions.md) of the [system_basic](../../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism) level. If the normal-level application needs to request this permission, its APL level must be declared as system_basic or higher. In addition, you should [request the user_grant permission from users](../../security/AccessToken/request-user-authorization.md).

```ts
import { BusinessError, request } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

import { bundleManager } from '@kit.AbilityKit';
import { abilityAccessCtrl, Context, PermissionRequestResult, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button("Download Image").width("50%").margin({ top: 20 }).height(40).onClick(async () => {
          let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION |
          bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA;
          // Obtain accessTokenID of the application.
          let tokenID = -1;
          try {
            await bundleManager.getBundleInfoForSelf(bundleFlags).then((data) => {
              console.info(`/Request getBundleInfoForSelf successfully. Data: ${JSON.stringify(data)}`);
              tokenID = data.appInfo.accessTokenId;
            }).catch((err: BusinessError) => {
              console.error(`GetBundleInfoForSelf failed. Cause: ${err.message}`);
            });
          } catch (err) {
            let message = (err as BusinessError).message;
            console.error('GetBundleInfoForSelf failed: %{public}s', message);
          }
          let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;

          let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
          let grant = true;
          // Check whether the application has the required permission. This API uses a promise to return the result.
          await atManager.checkAccessToken(tokenID, 'ohos.permission.WRITE_IMAGEVIDEO')
            .then((data: abilityAccessCtrl.GrantStatus) => {
              console.log(`/Request checkAccessToken success, data->${JSON.stringify(data)}`);
              if (data != abilityAccessCtrl.GrantStatus.PERMISSION_GRANTED) {
                grant = false;
              }
            })
            .catch((err: BusinessError) => {
              console.error(`GheckAccessToken fail, err->${JSON.stringify(err)}`);
            });

          if (!grant) {
            // Display a dialog box for the user to grant the required permission. This API uses an asynchronous callback to return the result.
            await atManager.requestPermissionsFromUser(context, ['ohos.permission.WRITE_IMAGEVIDEO'])
              .then((data: PermissionRequestResult) => {
                console.info('/Request grant:' + JSON.stringify(data));
                console.info('/Request grant permissions:' + data.permissions);
                console.info('/Request grant authResults:' + data.authResults);
                console.info('/Request grant dialogShownResults:' + data.dialogShownResults);
              }).catch((err: BusinessError) => {
                console.error('Grant error:' + JSON.stringify(err));
              });
          }

          try {
            let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
            let extension: string = 'jpg';
            let options: photoAccessHelper.CreateOptions = {
              title: 'xxxx'
            }
            // Obtain a PhotoAccessHelper instance, which can be used for accessing and modifying media files in an album.
            let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
            // Create an image or video asset with the specified file type, file name extension, and options. This API uses a promise to return the result.
            let uri: string = await phAccessHelper.createAsset(photoType, extension, options);
            console.info('/Request createAsset uri' + uri);
            console.info('/Request createAsset successfully');

            let config: request.agent.Config = {
              action: request.agent.Action.DOWNLOAD,
              url: 'https://xxxx/xxxx.jpg',
              // The saveas field specifies the URI of the file saved by PhotoAccessHelper.
              saveas: uri,
              gauge: true,
              // The overwrite field must be set to true.
              overwrite: true,
              network: request.agent.Network.WIFI,
              // The mode field must be set to request.agent.Mode.FOREGROUND.
              mode: request.agent.Mode.FOREGROUND,
            };
            request.agent.create(context, config).then((task: request.agent.Task) => {
              task.start((err: BusinessError) => {
                if (err) {
                  console.error(`Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
                  return;
                }
              });
              task.on('progress', async (progress) => {
                console.warn(`Request download status ${progress.state}, downloaded ${progress.processed}`);
              })
              task.on('completed', async (progress) => {
                console.warn('Request download completed, ' + JSON.stringify(progress));
                // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
                request.agent.remove(task.tid);
              })
            }).catch((err: BusinessError) => {
              console.error(`Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
            });
          } catch (err) {
            console.error(`Failed to create a download task, err: ${err}`);
          }
        })
      }
    }
  }
}
```

## Adding Network Configuration

### Intercepting HTTP

You can set the configuration file to intercept HTTP. After HTTP is disabled for the upload and download module, upload and download tasks using plaintext HTTP cannot be created. The configuration file is stored in the **src/main/resources/base/profile/network_config.json** directory of the application. For details, see the parameters in the [configuration file](../../reference/apis-network-kit/js-apis-net-connection.md#connectionsetapphttpproxy11) of the network management module .

The sample configuration file is as follows:

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
