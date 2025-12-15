# Uploading and Downloading Application Files
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

This topic describes how to upload an application file to a network server and download a network resource file from a network server to a local application file directory.

## Uploading Application Files

You can use **uploadFile()** in [ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md) to upload local files. The system service proxy implements the upload. In API version 12, the parameter for setting the custom proxy address is added to the **request.agent.create** API.

> **NOTE**
>
> · Currently, the **request.uploadFile** API can upload only files in the **cacheDir** directory, while the **request.agent** API can upload the user public files and files in the **cacheDir** directory.
>
> · The ohos.permission.INTERNET permission is required for using **ohos.request**. For details about how to request the permission, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).
>
> · The **ohos.request** module does not support proxy packet capture tools such as Charles and Fiddler.
>
> · Currently, APIs of the **ohos.request** module cannot be called in sub-threads, such as [TaskPool](../../arkts-utils/taskpool-introduction.md).

The following sample code shows how to upload cache files to the server in two ways:

<!-- @[request_upload_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/upload/RequestUpload.ets)-->

``` TypeScript
  async requestUploadFile(fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Obtain the application file path.
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let url = await urlUtils.getUrl(context);
    let cacheDir = context.cacheDir;

    // Create an application file locally.
    try {
      let file = fs.openSync(cacheDir + '/test.txt', fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
      fs.writeSync(file.fd, 'upload file test');
      fs.closeSync(file);
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      logger.error(TAG, `Invoke uploadFile failed, code=${err.code}, message=${err.message}`);
    }

    // Configure the upload task.
    let files: request.File[] = [
    // "internal://cache" in uri corresponds to the cacheDir directory.
      {
        filename: fileName,
        name: 'test',
        uri: 'internal://cache/' + fileName,
        type: 'txt'
      }
    ]
    let data: request.RequestData[] = [{ name: 'name', value: 'value' }];
    let uploadConfig: request.UploadConfig = {
      url: url,
      header: {
        'key1': 'value1',
        'key2': 'value2'
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
              logger.info(TAG, `upload complete taskState: ${JSON.stringify(taskStates[i])}`);
            }
            callback(100, true);
          });
        })
        .catch((err: BusinessError) => {
          logger.error(TAG, `Invoke uploadFile failed, code=${err.code}, message=${err.message}`);
        })
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      logger.error(TAG, `Invoke uploadFile failed, code=${err.code}, message=${err.message}`);
    }
  }

```


<!-- @[upload_agent_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/upload/RequestUpload.ets)-->

``` TypeScript
  async requestAgentUpload(fileName: string, callback: (progress: number, isSucceed: boolean) => void,
    context: common.UIAbilityContext) {
    // Obtain the application file path.
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let url = await urlUtils.getUrl(context);
    let cacheDir = context.cacheDir;

    let attachments: request.agent.FormItem[] = [{
      name: 'test',
      value: [
        {
          filename: fileName,
          path: cacheDir + '/' + fileName,
        },
      ]
    }];
    let config: request.agent.Config = {
      action: request.agent.Action.UPLOAD,
      url: url,
      mode: request.agent.Mode.FOREGROUND,
      overwrite: true,
      method: 'POST',
      headers: {
        'key1': 'value1',
        'key2': 'value2'
      },
      data: attachments
    };
    request.agent.create(context, config).then((task: request.agent.Task) => {
      task.start((err: BusinessError) => {
        if (err) {
          logger.error(TAG, `Failed to start the upload task, code=${err.code}, message=${err.message}`);
          return;
        }
      });
      task.on('progress', async (progress) => {
        logger.info(TAG, `Request upload status ${progress.state}, uploaded ${progress.processed}`);
      })
      task.on('completed', async () => {
        logger.info(TAG, `Request upload completed`);
        callback(100, true);
        // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
        request.agent.remove(task.tid);
      })
    }).catch((err: BusinessError) => {
      logger.error(TAG, `Failed to start the upload task, code=${err.code}, message=${err.message}`);
    });
  }

```


## Downloading Network Resource Files to an Application Directory

You can use **downloadFile()** in [ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md) to download network resource files to a local application directory. You can use the [ohos.file.fs](../../reference/apis-core-file-kit/js-apis-file-fs.md) APIs to access the downloaded files. For details, see [Accessing Application Files](../../file-management/app-file-access.md). The system service agent downloads the files. In API version 12, you can set the address of the agent in **request.agent.create()**.

> **NOTE**
>
> Currently, network resource files can be downloaded only to the application file directory.
>
> To use **uploadFile()** in **ohos.request**, you need to [declare permissions](../../security/AccessToken/declare-permissions.md): ohos.permission.INTERNET.

The following sample code shows how to download network resource files to the application file directory in two ways:

<!-- @[request_download_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/RequestDownload.ets)-->

``` TypeScript
  async requestDownloadFile(url: string, fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Obtain the application file path.
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let filesDir = context.cacheDir;
    let filePath = filesDir + '/' + fileName;
    this.clearExistFile(filePath);
    try {
      await request.downloadFile(context, {
        url: url,
        filePath: filePath,
      }).then((downloadTask: request.DownloadTask) => {
        downloadTask.on('complete', () => {
          // Obtain the file status information, including the file size.
          let fileStat = fileIo.statSync(filePath);
          let fileSize = fileStat.size;
          logger.info(TAG, `download complete, file= ${url}, size=${fileSize}, progress = 100%`);
          callback(100, true);
        })
      }).catch((err: BusinessError) => {
        logger.error(TAG, `downloadFile error, code=${err.code}, message=${err.message}`);
      });
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      logger.error(TAG, `downloadFile catch error, code=${err.code}, message=${err.message}`);
    }
  }

```


<!-- @[download_agent_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/RequestDownload.ets)-->

``` TypeScript
  async requestAgentDownload(url: string, fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Obtain the application file path.
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let filesDir = context.cacheDir;

    let config: request.agent.Config = {
      action: request.agent.Action.DOWNLOAD,
      url: url,
      saveas: fileName,
      gauge: true,
      overwrite: true,
      network: request.agent.Network.WIFI,
    };
    await request.agent.create(context, config).then((task: request.agent.Task) => {
      task.start((error: BusinessError) => {
        if (error) {
          logger.error(TAG, `start agent download task error, code=${error.code}, message=${error.message}`);
          return;
        }
      });
      task.on('progress', async (progress) => {
        logger.info(TAG, `Request download status ${progress.state}, downloaded ${progress.processed}`);
      })
      task.on('completed', async () => {
        logger.info(TAG, `Request download completed`);
        let filePath = filesDir + '/' + fileName;
        // Obtain the file status information, including the file size.
        let fileStat = fileIo.statSync(filePath);
        let fileSize = fileStat.size;
        logger.info(TAG, `download complete, file= ${url}, size=${fileSize}, progress = 100%`);
        callback(100, true);
        request.agent.remove(task.tid);
      })
    }).catch((err: BusinessError) => {
      logger.error(TAG, `download agent task catch error, code=${err.code}, message=${err.message}`);
    });
  }

```


## Downloading Network Resource Files to the User File
You can use the [request.agent](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentcreate10) API of [ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md) to download network resource files to the specified user file directory.

> **NOTE**
>
> Since API version 20, network resource files can be downloaded to the user file directory.

### Downloading Documents

Call the [save()](../../reference/apis-core-file-kit/js-apis-file-picker.md#save) API of [DocumentViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#documentviewpicker) to save a document and obtain the URI of the user file. Use this URI as the value of the **saveas** field of [Config](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentconfig10) to download the document.

<!-- @[doc_user_file_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/userFile/DocumentDownload.ets)-->

``` TypeScript
  async docFileAgentTask(url: string, fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Create a documentSaveOptions instance.
    try {
      const documentSaveOptions = new picker.DocumentSaveOptions();
      // (Optional) Name of the file to save. The default value is empty.
      documentSaveOptions.newFileNames = [fileName];
      // (Optional) Type of the document to save. The value is in ['Description|File name extensions'] format. To save all files, use 'All files (*.*)|.*'. If there are multiple file name extensions (a maximum of 100 extensions can be filtered), the first one is used by default. If this parameter is not specified, no extension is filtered by default.
      documentSaveOptions.fileSuffixChoices = ['Document|.txt', '.pdf'];
      let uri: string = '';
      // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
      const documentViewPicker = new picker.DocumentViewPicker(context);
      await documentViewPicker.save(documentSaveOptions).then((documentSaveResult: Array<string>) => {
        uri = documentSaveResult[0];
        logger.info(TAG, `DocumentViewPicker.save to file succeed and uri is ${uri}`);
      }).catch((err: BusinessError) => {
        logger.error(TAG, `documentViewPicker.save error, code=${err.code}, message=${err.message}`);
      })
      if (uri != '') {
        let config: request.agent.Config = {
          action: request.agent.Action.DOWNLOAD,
          url: url,
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
          await request.agent.create(context, config).then((task: request.agent.Task) => {
            task.start((err: BusinessError) => {
              if (err) {
                logger.error(TAG, `start download task error, code=${err.code}, message=${err.message}`);
                return;
              }
            });
            task.on('progress', async (progress) => {
              logger.info(TAG, `download status ${progress.state}, downloaded ${progress.processed}`);
            })
            task.on('completed', async (progress) => {
              logger.info(TAG, `download completed ${JSON.stringify(progress)}`);
              callback(100, true);
              // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
              request.agent.remove(task.tid);
            })
          }).catch((err: BusinessError) => {
            logger.error(TAG, `Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
          });
        } catch (error) {
          let err: BusinessError = error as BusinessError;
          logger.error(TAG, `Failed to create a download task, code=${err.code}, message=${err.message}`);
        }
      }
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      logger.error(TAG, `Failed to create a documentSaveOptions, code=${err.code}, message=${err.message}`);
      return;
    }
  }

```


### Downloading Audios

Call the [save()](../../reference/apis-core-file-kit/js-apis-file-picker.md#save-3) API of [AudioViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#audioviewpicker) to save an audio and obtain the URI of the user file. Use this URI as the value of the **saveas** field of [Config](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentconfig10) to download the audio.

<!-- @[audio_user_file_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/userFile/AudioDownload.ets)-->

``` TypeScript
  async audioFileAgentTask(url: string, fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Create a documentSaveOptions instance.
    const audioSaveOptions = new picker.AudioSaveOptions();
    // (Optional) Name of the file to save. The default value is empty.
    audioSaveOptions.newFileNames = [fileName];

    let uri: string = '';
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    const audioViewPicker = new picker.AudioViewPicker(context);
    await audioViewPicker.save(audioSaveOptions).then((audioSelectResult: Array<string>) => {
      uri = audioSelectResult[0];
      logger.info(TAG, `AudioViewPicker.save to file succeed and uri is ${uri}`);
    }).catch((err: BusinessError) => {
      logger.error(TAG, `Invoke audioViewPicker.save failed, code is ${err.code}, message is ${err.message}`);
    })
    if (uri != '') {
      let config: request.agent.Config = {
        action: request.agent.Action.DOWNLOAD,
        url: url,
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
              logger.error(TAG, `Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
              return;
            }
          });
          task.on('progress', async (progress) => {
            logger.info(TAG, `Request download status ${progress.state}, downloaded ${progress.processed}`);
          })
          task.on('completed', async (progress) => {
            logger.info(TAG, `Request download completed, ${JSON.stringify(progress)}`);
            callback(100, true);
            // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
            request.agent.remove(task.tid);
          })
        }).catch((err: BusinessError) => {
          logger.error(TAG, `Failed to create a download task, code=${err.code}, message=${err.message}`);
        });
      } catch (error) {
        let err: BusinessError = error as BusinessError;
        logger.error(TAG, `Failed to create a audio download task, code=${err.code}, message=${err.message}`);
      }
    }
  }

```


### Downloading Images or Videos

Call the [createAsset()](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#createasset-2) API of [PhotoAccessHelper](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper.md) to create a media file and obtain the URI of the user file. Use this URI as the value of the **saveas** field of [Config](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentconfig10) to download the media file.

Permission required: [ohos.permission.WRITE_IMAGEVIDEO](../../security/AccessToken/restricted-permissions.md#ohospermissionwrite_imagevideo)

[ohos.permission.WRITE_IMAGEVIDEO](../../security/AccessToken/restricted-permissions.md#ohospermissionwrite_imagevideo) is a [restricted permission](../../security/AccessToken/restricted-permissions.md) of the [system_basic](../../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism) level. If the normal-level application needs to request this permission, its APL level must be declared as system_basic or higher. In addition, you should [request the user_grant permission from users](../../security/AccessToken/request-user-authorization.md).

<!-- @[media_user_file_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/userFile/MediaDownload.ets)-->

``` TypeScript
  async mediaFileAgentTask(url: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION |
    bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA;
    // Obtain accessTokenID of the application.
    let tokenID = -1;
    try {
      await bundleManager.getBundleInfoForSelf(bundleFlags).then((data) => {
        logger.info(TAG, `Request getBundleInfoForSelf successfully. Data: ${JSON.stringify(data)}`);
        tokenID = data.appInfo.accessTokenId;
      }).catch((err: BusinessError) => {
        logger.error(TAG, `GetBundleInfoForSelf failed, code=${err.code}, message=${err.message}`);
      });
    } catch (err) {
      let message = (err as BusinessError).message;
      logger.error(`GetBundleInfoForSelf failed: ${message}`);
    }

    let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
    let grant = true;
    // Check whether the application has the required permission. This API uses a promise to return the result.
    await atManager.checkAccessToken(tokenID, 'ohos.permission.WRITE_IMAGEVIDEO')
      .then((data: abilityAccessCtrl.GrantStatus) => {
        logger.info(TAG, `Request checkAccessToken success, data->${JSON.stringify(data)}`);
        if (data != abilityAccessCtrl.GrantStatus.PERMISSION_GRANTED) {
          grant = false;
        }
      })
      .catch((err: BusinessError) => {
        logger.error(TAG, `CheckAccessToken fail, code=${err.code}, message=${err.message}`);
      });

    if (!grant) {
      // Display a dialog box for the user to grant the required permission. This API uses an asynchronous callback to return the result.
      await atManager.requestPermissionsFromUser(context, ['ohos.permission.WRITE_IMAGEVIDEO'])
        .then((data: PermissionRequestResult) => {
          logger.info(TAG, `Request grant: ${JSON.stringify(data)}`);
          logger.info(TAG, `Request grant permissions: ${data.permissions}`);
          logger.info(TAG, `Request grant authResults: ${data.authResults}`);
          logger.info(TAG, `Request grant dialogShownResults: ${data.dialogShownResults}`);
        }).catch((err: BusinessError) => {
          logger.error(TAG, `Grant error, code=${err.code}, message=${err.message}`);
        });
    }

    try {
      let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
      let extension: string = 'jpg';
      let options: photoAccessHelper.CreateOptions = {
        title: 'media'
      }
      // Obtain a PhotoAccessHelper instance, which can be used for accessing and modifying media files in an album.
      let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
      // Create an image or video asset with the specified file type, file name extension, and options. This API uses a promise to return the result.
      let uri: string = await phAccessHelper.createAsset(photoType, extension, options);
      logger.info(TAG, `Request createAsset uri ${uri}`);

      let config: request.agent.Config = {
        action: request.agent.Action.DOWNLOAD,
        url: url,
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
            logger.error(TAG, `Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
            return;
          }
        });
        task.on('progress', async (progress) => {
          logger.info(TAG, `Request download status ${progress.state}, downloaded ${progress.processed}`);
        })
        task.on('completed', async (progress) => {
          logger.info(TAG, `Request download completed, ${JSON.stringify(progress)}`);
          callback(100, true);
          // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
          request.agent.remove(task.tid);
        })
      }).catch((err: BusinessError) => {
        logger.error(TAG, `Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
      });
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      logger.error(TAG, `Failed to create a media download task, code=${err.code}, message=${err.message}`);
    }
  }

```


## Configuring Task Speed Limit and Timeout

You can use the APIs of the [ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md) module to upload local files or download network resource files. To set the task speed limit and duration, the [setMaxSpeed](../../reference/apis-basic-services-kit/js-apis-request.md#setmaxspeed18) API is available since API version 18 and the minimum speed and timeout parameters are available in the [request.agent.create](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentcreate10-1) API since API version 20.

The following sample code shows how to configure the speed and timeout of a download task:

<!-- @[speed_limit_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/SpeedLimitDownload.ets)-->

``` TypeScript
  async speedLimitDownload(url: string, fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Obtain the application file path.
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
    let filesDir = context.cacheDir;

    let config: request.agent.Config = {
      action: request.agent.Action.DOWNLOAD,
      url: url,
      saveas: fileName,
      gauge: true,
      overwrite: true,
      network: request.agent.Network.WIFI,
      // Rules for setting the minimum speed limit:
      // 1. If the task speed is lower than the specified value (for example, 16 × 1024 B/s) for a specified period (for example, 10s), the task fails.
      // 2. Conditions for resetting the timer:
      //    - The speed at any given second is below the minimum speed limit.
      //    - The task is resumed after being paused.
      //    - The task is restarted after being stopped.
      minSpeed: {
        speed: 16 * 1024,
        duration: 10
      },
      // Rules for setting timeout:
      // 1. connectionTimeout:
      //    - If the time required for establishing a single connection exceeds the specified duration (for example, 60s), the task fails.
      //    - The timer is started independently for each connection (not accumulated).
      // 2. totalTimeout:
      //    - If the total task duration (including connection and transmission time) exceeds the specified duration (for example, 120s), the task fails.
      //    - The duration is not counted if the task is paused and is accumulated after the task is resumed.
      // 3. Conditions for resetting the timer: The timer is reset when the task fails or stops.
      timeout: {
        connectionTimeout: 60,
        totalTimeout: 120,
      }
    };
    request.agent.create(context, config).then((task: request.agent.Task) => {
      // Set the maximum task speed.
      task.setMaxSpeed(10 * 1024 * 1024).then(() => {
        logger.info(TAG, `Succeeded in setting the max speed of the task. result: ${task.tid}`);
      }).catch((err: BusinessError) => {
        logger.error(TAG, `Failed to set the max speed of the task, code=${err.code}, message=${err.message}`);
      });
      task.start((err: BusinessError) => {
        if (err) {
          logger.error(TAG, `Failed to start the download task, code=${err.code}, message=${err.message}`);
          return;
        }
      });
      task.on('progress', async (progress) => {
        logger.info(TAG, `Request download status ${progress.state}, downloaded ${progress.processed}`);
      })
      task.on('completed', async () => {
        logger.info(TAG, `Request download completed`);
        // Obtain the file status information, including the file size.
        let filePath = filesDir + '/' + fileName;
        // Obtain the file status information, including the file size.
        let fileStat = fileIo.statSync(filePath);
        let fileSize = fileStat.size;
        logger.info(TAG, `download complete, file= ${url}, size=${fileSize}, progress = 100%`);
        callback(100, true);
        request.agent.remove(task.tid);
      })
    }).catch((err: BusinessError) => {
      logger.error(TAG, `Failed to create a download task, Code: ${err.code}, message: ${err.message}`);
    });
  }

```


## Adding Network Configuration

### Intercepting HTTP

You can set the configuration file to intercept HTTP. After HTTP is disabled for the **ohos.request** module, upload and download tasks using plaintext HTTP cannot be created. The configuration file is stored in the **src/main/resources/base/profile/network_config.json** directory of the application. For details about the parameters to be configured, see [Network Connection Security Configuration](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-network-ca-security#section5454123841911).

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

## Using WantAgent to Implement Redirection from the Notification Bar

Since API version 22, you can use the [wantAgent](../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md) API and the upload and download module to redirect users to a specified page in an application after they tap a task notification.

### Feature Description

The [wantAgent](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentnotification15) parameter set in the download task configuration specifies the application page to be redirected to. When a user taps a notification of an ongoing or completed download task, the system starts the specified application capability based on the **wantAgent** parameter.

### Sample Code

The following sample code shows how to create a download task with the **wantAgent** parameter.

<!-- @[want_agent_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/WantAgentDownload.ets)-->

``` TypeScript
  async wantAgentDownload(url: string, fileName: string, callback: (progress: number, isSuccess: boolean) => void,
    context: common.UIAbilityContext) {
    // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.

    // Create a wantAgentInfo object to define the operation to be performed after the notification is tapped.
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      wants: [
        {
          deviceId: '',
          bundleName: 'com.samples.uploaddownloadguide', // Use the actual bundle name.
          abilityName: 'EntryAbility', // Use the actual ability name.
          action: '',
          entities: [],
          uri: '',
          parameters: {} // Pass in custom parameters.
        }
      ],
      actionType: wantAgent.OperationType.START_ABILITY,
      requestCode: 0,
      wantAgentFlags: [wantAgent.WantAgentFlags.CONSTANT_FLAG]
    };

    // Obtain the WantAgent instance.
    let wantAgentInstance: WantAgent;
    try {
      wantAgentInstance = await wantAgent.getWantAgent(wantAgentInfo);
    } catch (error) {
      logger.error(TAG, `Failed to get WantAgent, Code: ${error.code}  message: ${error.message}`);
      return;
    }

    let filesDir = context.cacheDir;
    // Create a download task configuration, including the wantAgent parameter.
    let config: request.agent.Config = {
      action: request.agent.Action.DOWNLOAD,
      url: url, // Use the actual download address.
      title: 'Download task notification title',
      description: 'Download task notification description',
      mode: request.agent.Mode.BACKGROUND,
      overwrite: true,
      method: 'GET',
      saveas: fileName,
      network: request.agent.Network.ANY,
      gauge: true,
      notification: {
        visibility: request.agent.VISIBILITY_COMPLETION | request.agent.VISIBILITY_PROGRESS,
        wantAgent: wantAgentInstance,
      }
    };

    // Create and start a download task.
    try {
      request.agent.create(context, config).then((task: request.agent.Task) => {
        task.start((err: BusinessError) => {
          if (err) {
            logger.error(TAG, `Failed to start the download task, Code: ${err.code}  message: ${err.message}`);
            return;
          }
        });
        task.on('progress', async (progress) => {
          logger.error(TAG, `Request download status ${progress.state}, downloaded ${progress.processed}`);
        })
        task.on('completed', async (progress) => {
          console.warn('Request download completed, ' + JSON.stringify(progress));
          logger.error(TAG, `Request download completed, ${JSON.stringify(progress)}`);
          // Obtain the file status information, including the file size.
          let filePath = filesDir + '/' + fileName;
          // Obtain the file status information, including the file size.
          let fileStat = fileIo.statSync(filePath);
          let fileSize = fileStat.size;
          logger.info(TAG, `download complete, file= ${url}, size=${fileSize}, progress = 100%`);
          callback(100, true);
          // This method requires the user to manage the task lifecycle. After the task is complete, call the remove method to release the task object.
          request.agent.remove(task.tid);
        })
      }).catch((err: BusinessError) => {
        logger.error(TAG, `Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
      });
    } catch (error) {
      let err: BusinessError = error as BusinessError;
      logger.error(TAG, `Failed to operate a download task, Code: ${err.code}, message: ${err.message}`);
    }
  }

```


### Configuration

In the preceding sample code, we implement redirection from the notification bar through the following steps:

1. Create a **WantAgentInfo** object: Define the operations to be performed after a notification is tapped, including the bundle name of the target application, ability name, and parameters to be passed.

2. Obtain the **WantAgent** instance: Obtain the **WantAgent** instance by calling the **wantAgent.getWantAgent()** method.

3. Configure the download task: Set the **notification** property in **request.agent.Config** and set the **wantAgent** parameter to the obtained **WantAgent** instance.

4. Set the notification visibility: Use the **visibility** parameter to display specified content in a notification, such as the progress and completion status.

### Precautions

- This feature is supported only in API version 22 or later.
- Ensure that the correct bundle name and ability name are used when configuring **wantAgentInfo**.
- **wantAgent** must be used together with **notification** to implement the redirection feature in a notification.
- In actual applications, you are advised to adjust the title, description, visibility, and other related parameters of a notification based on service requirements.
