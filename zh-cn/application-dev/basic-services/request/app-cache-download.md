# 应用文件缓存下载
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @fang-jinxu-->

开发者可以使用缓存下载模块（[cacheDownload](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md)）将网络资源文件下载并缓存到文件系统中。缓存下载功能支持配置重试策略和超时控制，从API version 26.0.0开始，开发者可以为单个任务配置重试和超时参数，也可以设置全局默认配置。

> **说明：**
>
> · 使用缓存下载模块，需[声明权限](../../security/AccessToken/declare-permissions.md)：ohos.permission.INTERNET。
>
> · 如需获取下载信息或检查网络可用性，还需声明权限：ohos.permission.GET_NETWORK_INFO。
>
> · 缓存下载的资源会被存储在文件缓存中，单次下载资源解压后最大支持20MB。
>
> · 缓存下载回调监听（onDownloadSuccess/onDownloadError）是进程级别的，需要在页面生命周期内正确管理注册与注销。

## 配置任务级重试策略

从API version 26.0.0开始，开发者可以在创建缓存下载任务时通过[RetryOptions](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#retryoptions)配置任务的重试策略。当下载失败时，系统会根据配置自动进行重试。

以下示例展示了如何为单个缓存下载任务配置重试参数：

<!-- @[cache_download_with_retry](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/CacheDownloadRetry.ets)--> 

``` TypeScript
startCacheDownloadWithRetry(): void {
  this.downloadStatus = 'Downloading';
  this.errorMessage = '';
  logger.info(TAG, `Starting cache download with retry, url: ${this.downloadUrl}, maxRetryCount: ${this.maxRetryCount}`);

  // 如果URL发生变化，需要重新注册回调
  this.unregisterCallbacks();
  this.registerCallbacks();

  try {
    // 配置 RetryOptions - API 26 新增参数
    let retryOptions: cacheDownload.RetryOptions = {
      maxRetryCount: this.maxRetryCount  // 最大重试次数，范围0-10，默认值1
    };

    // 配置 CacheDownloadOptions，包含 retry 参数
    let options: cacheDownload.CacheDownloadOptions = {
      retry: retryOptions
    };

    // 启动缓存下载任务
    cacheDownload.download(this.downloadUrl, options);
    logger.info(TAG, 'Cache download task started');
  } catch (err) {
    let error = err as BusinessError;
    logger.error(TAG, `Failed to start cache download, code: ${error.code}, message: ${error.message}`);
    this.downloadStatus = 'Failed';
    this.errorMessage = `BusinessError: ${error.code}, ${error.message}`;
  }
}
```

## 配置任务级超时策略

从API version 26.0.0开始，开发者可以在创建缓存下载任务时通过[TimeoutOptions](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#timeoutoptions)配置任务的超时策略。

以下示例展示了如何为单个缓存下载任务配置超时参数：

<!-- @[cache_download_with_timeout](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/CacheDownloadTimeout.ets)--> 

``` TypeScript
startCacheDownloadWithTimeout(): void {
  this.downloadStatus = 'Downloading';
  this.errorMessage = '';
  logger.info(TAG, `Starting cache download with timeout, url: ${this.downloadUrl}`);
  logger.info(TAG, `networkCheckTimeout: ${this.networkCheckTimeout}s, httpTotalTimeout: ${this.httpTotalTimeout}s`);

  // 如果URL发生变化，需要重新注册回调
  this.unregisterCallbacks();
  this.registerCallbacks();

  try {
    let timeoutOptions: cacheDownload.TimeoutOptions = {
      networkCheckTimeout: this.networkCheckTimeout,
      httpTotalTimeout: this.httpTotalTimeout
    };

    let options: cacheDownload.CacheDownloadOptions = {
      timeout: timeoutOptions
    };

    cacheDownload.download(this.downloadUrl, options);
    logger.info(TAG, 'Cache download task started');
  } catch (err) {
    let error = err as BusinessError;
    logger.error(TAG, `Failed to start cache download, code: ${error.code}, message: ${error.message}`);
    this.downloadStatus = 'Failed';
    this.errorMessage = `BusinessError: ${error.code}, ${error.message}`;
  }
}
```

## 设置全局重试配置

从API version 26.0.0开始，开发者可以通过[setGlobalRetryOptions](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadsetglobalretryoptions)接口设置全局默认的重试配置。该配置适用于所有未指定任务级retry参数的缓存下载任务。

以下示例展示了如何设置全局重试配置：

<!-- @[set_global_retry_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/GlobalRetryOptions.ets)--> 

``` TypeScript
setGlobalRetryOptions(): void {
  logger.info(TAG, `Setting global retry options, maxRetryCount: ${this.globalMaxRetryCount}`);

  try {
    let globalRetryOptions: cacheDownload.RetryOptions = {
      maxRetryCount: this.globalMaxRetryCount
    };

    // 调用 setGlobalRetryOptions 设置全局重试配置
    // 该配置适用于所有未指定任务级 retry 的缓存下载任务
    cacheDownload.setGlobalRetryOptions(globalRetryOptions);
      
    this.globalConfigStatus = `maxRetryCount = ${this.globalMaxRetryCount}`;
    logger.info(TAG, 'Global retry options set successfully');
    this.showToast($r('app.string.global_config_success'));
  } catch (err) {
    let error = err as BusinessError;
    logger.error(TAG, `Failed to set global retry options, code: ${error.code}, message: ${error.message}`);
    this.globalConfigStatus = 'Failed';
    this.showToast($r('app.string.global_config_failed'));
  }
}
```

## 设置全局超时配置

从API version 26.0.0开始，开发者可以通过[setGlobalTimeoutOptions](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadsetglobaltimeoutoptions)接口设置全局默认的超时配置。该配置适用于所有未指定任务级timeout参数的缓存下载任务。

以下示例展示了如何设置全局超时配置：

<!-- @[set_global_timeout_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/GlobalTimeoutOptions.ets)--> 

``` TypeScript
setGlobalTimeoutOptions(): void {
  logger.info(TAG, `Setting global timeout options`);
  logger.info(TAG, `networkCheckTimeout: ${this.globalNetworkCheckTimeout}s, httpTotalTimeout: ${this.globalHttpTotalTimeout}s`);

  try {
    let globalTimeoutOptions: cacheDownload.TimeoutOptions = {
      networkCheckTimeout: this.globalNetworkCheckTimeout,
      httpTotalTimeout: this.globalHttpTotalTimeout
    };

    // 调用 setGlobalTimeoutOptions 设置全局超时配置
    // 该配置适用于所有未指定任务级 timeout 的缓存下载任务
    cacheDownload.setGlobalTimeoutOptions(globalTimeoutOptions);
      
    this.globalConfigStatus = `networkCheckTimeout=${this.globalNetworkCheckTimeout}s, httpTotalTimeout=${this.globalHttpTotalTimeout}s`;
    logger.info(TAG, 'Global timeout options set successfully');
    this.showToast($r('app.string.global_config_success'));
  } catch (err) {
    let error = err as BusinessError;
    logger.error(TAG, `Failed to set global timeout options, code: ${error.code}, message: ${error.message}`);
    this.globalConfigStatus = 'Failed';
    this.showToast($r('app.string.global_config_failed'));
  }
}
```

## 注册下载回调监听

从API version 23开始，开发者可以通过[onDownloadSuccess](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadondownloadsuccess23)和[onDownloadError](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadondownloaderror23)接口注册回调函数，监听下载成功和失败事件。

> **说明：**
>
> · 回调监听是进程级别的，对整个应用进程生效。
>
> · 同一URL多次调用注册接口会注册多个回调，下载完成时所有回调都会被触发。
>
> · 需要在页面退出时调用[offDownloadSuccess](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadoffdownloadsuccess23)和[offDownloadError](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadoffdownloaderror23)注销回调，避免内存泄漏。

注册和注销回调的基本用法如下：

<!-- @[cache_download_register_callbacks](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/CacheDownloadRetry.ets)--> 

``` TypeScript
// 注册回调监听（页面生命周期内只注册一次）
private registerCallbacks(): void {
  this.successCallback = () => {
    logger.info(TAG, 'Cache download succeeded');
    this.downloadStatus = 'Success';
    this.showToast($r('app.string.download_success'));
  };

  this.errorCallback = (error: cacheDownload.DownloadError) => {
    logger.error(TAG, `Cache download failed, errorCode: ${error.errorCode}, message: ${error.message}`);
    this.downloadStatus = 'Failed';
    this.errorMessage = `Error: ${error.errorCode}, ${error.message}`;
    this.showToast($r('app.string.download_failed'));
  };

  // 使用当前URL注册回调（初始URL）
  cacheDownload.onDownloadSuccess(this.downloadUrl, this.successCallback);
  cacheDownload.onDownloadError(this.downloadUrl, this.errorCallback);
}
```

<!-- --> 

<!-- @[cache_download_unregister_callbacks](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/CacheDownloadRetry.ets)--> 

``` TypeScript
// 注销回调监听
private unregisterCallbacks(): void {
  cacheDownload.offDownloadSuccess(this.downloadUrl, this.successCallback);
  cacheDownload.offDownloadError(this.downloadUrl, this.errorCallback);
}
```

## 取消缓存下载任务

开发者可以通过[cancel](../../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md#cachedownloadcancel)接口取消正在进行的缓存下载任务。

<!-- @[cache_download_cancel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Basic-Services-Kit/request/CacheDownload/entry/src/main/ets/pages/CacheDownloadRetry.ets)-->

``` TypeScript
cancelCacheDownload(): void {
  try {
    cacheDownload.cancel(this.downloadUrl);
    logger.info(TAG, 'Cache download task cancelled');
    this.downloadStatus = 'Cancelled';
    this.showToast($r('app.string.download_cancelled'));
  } catch (err) {
    let error = err as BusinessError;
    logger.error(TAG, `Failed to cancel, code: ${error.code}, message: ${error.message}`);
  }
}
```

## 相关权限

使用缓存下载功能需要声明以下权限：

| 权限 | 说明 |
|---|---|
| [ohos.permission.INTERNET](../../security/AccessToken/permissions-for-all.md#ohospermissioninternet) | 允许应用访问网络，必选权限。 |
| [ohos.permission.GET_NETWORK_INFO](../../security/AccessToken/permissions-for-all.md#ohospermissionget_network_info) | 允许应用获取网络信息，使用getDownloadInfo接口获取下载信息或等待检查网络可用则需要此权限。 |
