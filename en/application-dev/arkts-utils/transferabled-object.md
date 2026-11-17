---
kits: ["ArkTS / Ark Programming Language"]
description: "Introduces two transfer modes for Transferable objects (NativeBinding objects): shared mode supports cross-thread shared access, while transfer mode transfers object ownership and the original thread no longer has access permission, suitable for objects that require efficient transfer such as file descriptors and graphics resources."
keywords: [Transferable object, NativeBinding object, shared mode, transfer mode, ownership transfer, file descriptor, graphics resource]
doctype: guide
status: active
---

# Transferable Object (NativeBinding Object)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:52:12.598Z pushedAt=2026-11-12T13:37:54.277Z nl=1 -->


A Transferable object, also known as a NativeBinding object, is a JS object that is bound to a C++ object, with the primary functionality provided by C++. Its JS object wrapper is allocated in the local heap of the virtual machine. During cross-thread communication, the same C++ object is reused. Compared with the pass-by-copy mode of JS objects, this method offers higher transfer efficiency. Therefore, NativeBinding objects that can be shared or transferred are also referred to as Transferable objects. You can also customize Transferable objects. For details, see [Multithreaded Operations with Custom Native Transferable Objects](napi-coerce-to-native-binding-object.md).


## Shared Mode

If the C++ implementation can ensure thread safety, the C++ part of the NativeBinding object supports the shared mode. In this case, after the NativeBinding object is passed across threads, you only need to create a JS object wrapper again to bridge to the same C++ object, achieving the sharing of the C++ object. The following figure shows the communication process.


![nativeBinding](figures/nativeBinding.png)


Common shared mode NativeBinding objects include context objects such as the application context ([ApplicationContext](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md)). These context objects encapsulate the context information of application components and provide the capability to access system services and resources, enabling application components to interact with the system. For details about how to obtain context information, see [Obtaining Context Information](../application-models/application-context-stage.md). For an example of using a context across threads, see [Using TaskPool for Frequent Database Operations](batch-database-operations-guide.md#using-taskpool-for-frequent-database-operations).


## Transfer Mode

If the C++ implementation contains data and cannot ensure thread safe, the C++ part of the NativeBinding object should be passed by transfer. In this case, after the NativeBinding object is passed across threads, you only need to create a JS object wrapper again to bridge to the C++ object. However, the original object must remove its binding to this object. The following figure shows the communication process.

![nativeBinding_transfer](figures/nativeBinding_transfer.png)

Common transfer mode NativeBinding objects include the [PixelMap](../reference/apis-image-kit/arkts-apis-image-PixelMap.md) object, which can read or write image data and obtain image information, and is often used to display images.

Here is an example of passing a PixelMap object across threads. Obtain the image resource from the **rawfile** folder, and create a PixelMap object in the child thread and pass it to the main thread. The specific implementation is as follows:

<!-- @[example_pass_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/CommunicationObjects/entry/src/main/ets/managers/TransferabledObject.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';
import { loadPixelMap } from './pixelMapTest';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  uiContext = this.getUIContext();
  @State message: string = 'Hello World';
  @State pixelMap: PixelMap | undefined = undefined;

  private async loadImageFromThread(): Promise<void> {
    const resourceMgr = this.uiContext?.getHostContext()?.resourceManager;
    // Here 'startIcon.png' is copied from media to the resources/rawfile folder in the project. Replace it with your own file,
    // otherwise imageSource creation will fail and subsequent execution cannot proceed normally (the log will print "Failed to get RawFd").
    await resourceMgr?.getRawFd('startIcon.png').then(async rawFileDescriptor => {
      await taskpool.execute(loadPixelMap, rawFileDescriptor).then(pixelMap => {
        if (pixelMap) {
          this.pixelMap = pixelMap as PixelMap;
          this.message = 'success';
          console.info('Succeeded in creating pixelMap.');
          // The main thread releases the pixelMap. Because setTransferDetached has been called when the child thread returns the pixelMap, the pixelMap can be released immediately.
          this.pixelMap.release();
        } else {
          this.message = 'failed';
          console.error('Failed to create pixelMap.');
        }
      }).catch((e: BusinessError) => {
        this.message = 'failed';
           console.error(`taskpool execute loadPixelMap failed. Code: ${e.code}, message: ${e.message}`);
      });
    }).catch(() => {
      this.message = 'failed';
      console.error(`Failed to get RawFd`);
    });
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.loadImageFromThread();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

<!-- @[example_pass_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/CommunicationObjects/entry/src/main/ets/managers/pixelMapTest.ets) -->

``` TypeScript
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Concurrent
export async function loadPixelMap(rawFileDescriptor: resourceManager.RawFileDescriptor): Promise<PixelMap> {
  // Create an imageSource.
  const imageSource = image.createImageSource(rawFileDescriptor);
  // Create a pixelMap.
  const pixelMap = imageSource.createPixelMapSync();
  // Release the imageSource.
  imageSource.release();
  // Detach pixelMap from the original thread's reference after cross-thread transfer is complete.
  try {
       pixelMap.setTransferDetached(true);
     } catch (err) {
       hilog.error(0x0000, 'testTag', 'Failed to set transferDetached. Cause: %{public}s', JSON.stringify(err));
     }
  // Return the pixelMap to the main thread.
  return pixelMap;
}
```
