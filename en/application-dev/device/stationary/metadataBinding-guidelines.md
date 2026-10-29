# Metadata Binding Development
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @codexu62-->
<!--Designer: @yuxiaoyang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2fe43cf7ea77cdd21cfa7d17dc93a663c83e8548 translatedAt=2026-10-13T12:46:25.078Z pushedAt=2026-10-15T10:19:06.327Z -->

## Overview

Metadata binding allows the system to map the content browsed by the current user to the [App Linking link](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/applinking-introduction) provided by a third-party application and save the association.

For detailed API introduction, refer to [@ohos.multimodalAwareness.metadataBinding (Metadata Binding)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-metadataBinding.md).

## Overview

A third-party application can use metadata binding to map an App Linking link to the system application or service that calls the API. For example, when a user browses a product in an e-commerce application and saves a screenshot of the product image, the system records the mapping between the image and the App Linking link provided by the e-commerce application. When the user browses the image again and actively triggers the Celia screen recognition capability, the system reminds the user whether to return to the e-commerce application to view the product details. The reminder style is configured by Celia.

## Demonstration Example

![Metadata binding](figures/metadatabinding.gif)

## Available APIs

  - The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
  - This module supports metadata binding.

| Name                                                       | Description                                   |
| ------------------------------------------------------------ | -------------------------------------- |
| [submitMetadata](../../reference/apis-multimodalawareness-kit/js-apis-awareness-metadataBinding.md#metadatabindingsubmitmetadata)(metadata: string): void; | Passes the HarmonyOS App Linking link to be encoded from a third-party app to the multimodal awareness service, which determines the appropriate time to deliver the content to the system app that calls the encoding API. |
| [on](../../reference/apis-multimodalawareness-kit/js-apis-awareness-metadataBinding.md#metadatabindingonoperationsubmitmetadata)(type: 'operationSubmitMetadata', bundleName: string, callback: Callback&lt;number&gt;): void; | Subscribes to system events to obtain encoded content. The app registers a callback, and the encoded content is returned when the event occurs. |
| [off](../../reference/apis-multimodalawareness-kit/js-apis-awareness-metadataBinding.md#metadatabindingoffoperationsubmitmetadata)(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback&lt;number&gt;): void; | Unsubscribes from system events for obtaining encoded content. This API cancels the registered callback. |
  
## Constraints

  - Encoding fails if a HarmonyOS App Linking URL exceeds 128 bytes, and a screenshot is taken to save the original image.

## How to Develop

1. Import the related modules.

   <!-- @[import_the_metadata_binding_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/MetadataBinding/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { metadataBinding } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { Callback } from '@kit.BasicServicesKit';
   ```

2. Define the metadata binding service callback and the bundle name. The function receives the encoded content returned.   

   <!-- @[metadata_binding_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/MetadataBinding/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let callback : Callback<number> = (event: number) => {};
   let bundleName: string = 'com.example.app';
   ```

3. Subscribe to the metadata binding service.

   <!-- @[metadata_binding_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/MetadataBinding/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   try {
     metadataBinding.on('operationSubmitMetadata', bundleName, callback);
     console.info('on succeeded');
     // ...
   } catch (err) {
     let error = err as BusinessError;
     console.error('Register event error and err code is ' + error.code);
     // ...
   }
   ```

4. Provide the App Linking link.

   <!-- @[metadata_binding_submit](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/MetadataBinding/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   let metadata: string = 'sample metadata';
   try {
     metadataBinding.submitMetadata(metadata);
     // ...
   } catch (err) {
     let error = err as BusinessError;
     console.error('Submit metadata error and err code is ' + error.code);
     // ...
   }
   ```

5. Unsubscribe from the metadata binding service.

   <!-- @[metadata_binding_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/MetadataBinding/entry/src/main/ets/pages/Index.ets) --> 
   
   ``` TypeScript
   try {
     metadataBinding.off('operationSubmitMetadata', bundleName, callback);
     console.info('off succeeded');
     // ...
   } catch (err) {
     let error = err as BusinessError;
     console.error('Unregister event error and err code is ' + error.code);
     // ...
   }
   ```