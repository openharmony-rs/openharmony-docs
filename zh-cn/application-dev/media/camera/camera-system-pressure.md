# 压力管控(ArkTS)

相机框架提供对系统压力等级的监听。

在长时间使用相机的场景（如直播业务）中，相机应用可以通过监听系统压力等级变化，动态调整画质（如帧率、分辨率等），平衡功耗、发热和系统负载，保证服务长时间可用。

## 状态监听

可以通过注册systemPressureLevelChange的回调函数获取系统压力的监听结果，当系统压力发生变化时，callback返回SystemPressureLevel参数。参数的具体内容可参考相机管理器回调接口实例[SystemPressureLevel](../../reference/apis-camera-kit/arkts-apis-camera-e.md#systempressurelevel20)。

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, systemPressureLevel: camera.SystemPressureLevel): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`systemPressureLevel: ${systemPressureLevel}`);
}

function registerSystemPressureLevelChangeCallback(photoSession: camera.PhotoSession): void {
    photoSession.on('systemPressureLevelChange', callback);
}
```