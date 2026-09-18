# @ohos.base(Public Callback Information)

The **Base** module defines the public callback types of ArkTS APIs, including the common and error callbacks. These
 callbacks provide a unified asynchronous processing mechanism for processing asynchronous operation results and error
 messages. They can help developers simplify the asynchronous programming model and improve code readability and
 maintainability.

> **NOTE**
 >
 > - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a
 >   superscript to indicate their earliest API version.
 > - Since API version 12, the APIs of this module are supported in ArkTS widgets.



## Modules to Import

```TypeScript
import { AsyncCallback, BusinessError, Callback, ErrorCallback } from '@kit.BasicServicesKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [AsyncCallback](arkts-basicservices-base-asynccallback-i.md) | Defines a common callback that carries an error parameter and asynchronous return value. It is used to return error information or success data when an asynchronous operation is complete. |
| [BusinessError](arkts-basicservices-base-businesserror-i.md) | Defines an error parameter. This API inherits from the **Error** class and is used to pass standard error information, including the error code and optional additional information. |
| [Callback](arkts-basicservices-base-callback-i.md) | Defines a common callback used to return the processing result when an asynchronous operation is successful. You need to define the callback type. |
| [ErrorCallback](arkts-basicservices-base-errorcallback-i.md) | Defines a common callback that carries an error parameter. It is used to return error information when an asynchronous operation fails. The specific error code is defined by each API. For details, please refer to the error code description of the corresponding API. |
