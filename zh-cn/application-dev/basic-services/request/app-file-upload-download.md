# 应用文件上传下载
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

应用支持将文件上传到网络服务器，也支持从网络服务器下载资源文件到本地目录。

## 上传应用文件

开发者可以使用上传下载模块（[ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md)）的上传接口将本地文件上传。文件上传过程通过系统服务代理完成。在api12中，`request.agent.create`接口增加了设置代理地址的参数，支持设置自定义代理地址。

> **说明：**
>
> · 当前上传应用文件功能。request.uploadFile方式仅支持上传应用缓存文件路径（cacheDir）下的文件，request.agent方式支持上传用户公共文件和应用缓存文件路径下的文件。
>
> · 使用上传下载模块，需[声明权限](../../security/AccessToken/declare-permissions.md)：ohos.permission.INTERNET。
>
> · 上传下载模块不支持Charles、Fiddler等代理抓包工具。
>
> · 上传下载模块接口目前暂不支持子线程调用场景，如[TaskPool](../../arkts-utils/taskpool-introduction.md)等。

以下示例代码展示了两种将缓存文件上传至服务器的方法：

<!-- @[request_upload_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/upload/RequestUpload.ets)-->

<!-- @[upload_agent_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/upload/RequestUpload.ets)-->

## 下载网络资源文件至应用文件目录

开发者可以使用上传下载模块（[ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md)）的下载接口将网络资源文件下载到应用文件目录。对已下载的网络资源应用文件，开发者可以使用基础文件IO接口（[ohos.file.fs](../../reference/apis-core-file-kit/js-apis-file-fs.md)）对其进行访问，使用方式与[应用文件访问](../../file-management/app-file-access.md)一致。文件下载过程使用系统服务代理完成，在api12中request.agent.create接口增加了设置代理地址参数，支持用户设置自定义代理地址。

> **说明：**
>
> 当前网络资源文件仅支持下载至应用文件目录。
>
> 使用上传下载模块，需[声明权限](../../security/AccessToken/declare-permissions.md)：ohos.permission.INTERNET。

以下示例代码展示了将网络资源文件下载到应用内部文件目录的两种方法：

<!-- @[request_download_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/RequestDownload.ets)-->

<!-- @[download_agent_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/RequestDownload.ets)-->

## 下载网络资源文件至用户文件
开发者可以使用[ohos.request](../../reference/apis-basic-services-kit/js-apis-request.md)的[request.agent](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentcreate10)接口下载网络资源文件到指定的用户文件目录。

> **说明：**
>
> 从API version 20开始支持下载网络资源文件至用户文件。

### 下载文档类文件

开发者可以通过调用[DocumentViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#documentviewpicker)的[save()](../../reference/apis-core-file-kit/js-apis-file-picker.md#save)接口保存文件并获得用户文件的uri，将此uri作为[Config](../../reference/apis-basic-services-kit/js-apis-request.md#config10)的saveas字段值进行下载。

<!-- @[doc_user_file_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/userFile/DocumentDownload.ets)-->

### 下载音频类文件

开发者可以通过调用[AudioViewPicker](../../reference/apis-core-file-kit/js-apis-file-picker.md#audioviewpicker)的[save()](../../reference/apis-core-file-kit/js-apis-file-picker.md#save-3)接口保存文件并获得用户文件的uri，将此uri作为[Config](../../reference/apis-basic-services-kit/js-apis-request.md#config10)的saveas字段值进行下载。

<!-- @[audio_user_file_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/userFile/AudioDownload.ets)-->

### 下载图片或视频类文件

开发者可以通过调用[PhotoAccessHelper](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper.md)的[createAsset()](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#createasset-2)接口创建媒体文件并获取用户文件的URI，将其作为[Config](../../reference/apis-basic-services-kit/js-apis-request.md#config10)的saveas字段值进行下载。

需要权限：[ohos.permission.WRITE_IMAGEVIDEO](../../security/AccessToken/permissions-for-all-user.md#ohospermissionwrite_media)

权限[ohos.permission.WRITE_IMAGEVIDEO](../../security/AccessToken/permissions-for-all-user.md#ohospermissionwrite_media)是[system_basic](../../security/AccessToken/app-permission-mgmt-overview.md#权限机制中的基本概念)级别的[受限开放权限](../../security/AccessToken/restricted-permissions.md)，normal等级的应用需要将自身的APL等级声明为system_basic及以上。授权方式为user_grant，需要[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。

<!-- @[media_user_file_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/userFile/MediaDownload.ets)-->

## 添加任务速度限制与超时限制

开发者可以使用[ohos.request (上传下载)](../../reference/apis-basic-services-kit/js-apis-request.md)模块中的接口上传本地文件或下载网络资源文件。为方便对任务速度及时长进行限制，分别在API version 18中增加了[setMaxSpeed](../../reference/apis-basic-services-kit/js-apis-request.md#setmaxspeed18)接口，支持用户设置任务的最高速度限制；在API version 20的[request.agent.create](../../reference/apis-basic-services-kit/js-apis-request.md#requestagentcreate10-1)接口中增加了最低限速及超时参数，支持用户自定义最低速度限制以及超时时间。

以下是对下载任务进行速度限制与超时限制的方式的示例代码演示：

<!-- @[speed_limit_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/SpeedLimitDownload.ets)-->

## 添加网络配置

### HTTP拦截

开发者可以通过设置配置文件实现HTTP拦截功能。上传下载模块在应用配置文件中禁用HTTP后，无法创建明文HTTP传输的上传下载任务。配置文件在APP中的路径是：`src/main/resources/base/profile/network_config.json`。请参考网络管理模块[配置文件](../../reference/apis-network-kit/js-apis-net-connection.md#connectionsetapphttpproxy11)，了解需要配置的具体参数。

参考配置文件如下所示：

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

## 使用WantAgent实现通知栏跳转功能

从API version 22开始，开发者可以使用[wantAgent](../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md)接口与上传下载模块结合，实现点击任务通知后跳转至应用指定页面的功能。

### 功能介绍

通过在下载任务的配置中设置[wantAgent参数](../../reference/apis-basic-services-kit/js-apis-request.md#notification15)，开发者可以指定用户点击通知后要跳转的应用页面及相关参数。当用户点击正在进行或已完成的下载任务通知时，系统会根据wantAgent参数启动指定的应用能力。

### 示例代码

以下示例代码展示了如何创建一个带有wantAgent功能的下载任务：

<!-- @[want_agent_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UploadAndDownload/UploadDownloadGuide/features/uploadanddownload/src/main/ets/download/WantAgentDownload.ets)-->

### 配置说明

在上面的示例代码中，我们主要通过以下几个步骤实现了通知栏跳转功能：

1. **创建WantAgentInfo对象**：定义点击通知后要执行的操作，包括目标应用的包名、ability名称和需要传递的具体参数。

2. **获取WantAgent实例**：通过`wantAgent.getWantAgent()`方法获取WantAgent实例。

3. **配置下载任务**：在`request.agent.Config`中设置`notification`属性，并将`wantAgent`参数设置为前面获取的WantAgent实例。

4. **设置通知可见性**：通过`visibility`参数可以控制通知显示的内容，例如进度、完成状态等。

### 注意事项

- 此功能仅支持API version 22及以上版本。
- 确保在配置`wantAgentInfo`时，填写正确的应用包名和ability名称。
- `wantAgent`参数需要与`notification`参数配合使用，才能在通知中显示跳转功能。
- 在实际应用中，建议根据业务需求调整通知的标题、描述、可见性以及其他相关参数。

