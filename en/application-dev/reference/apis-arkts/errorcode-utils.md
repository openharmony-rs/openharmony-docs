# Utils Error Codes
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @yuanyao14-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 10200001 Value Out of Range

**Error Message**

The value of ${param} is out of range.

**Description**

The value of a parameter passed in the API exceeds the valid range.

**Possible Causes**

The parameter value exceeds the value range.

**Solution**

Use a valid parameter value.

## 10200002 Parameter Parsing Error

**Error Message**

Invalid ${param} string.

**Description**

Failed to parse a string.

**Possible Causes**

A parameter of the string type passed in the API is a non-standard string. As a result, the string fails to be parsed.

**Solution**

Check the format of the string.

## 10200003 Failed to Initialize the Worker Instance

**Error Message**

Worker initialization failed.

**Description**

The **Worker** instance fails to be initialized when the API is called.

**Possible Causes**

1. The number of **Worker** instances to be created exceeds the upper limit.
2. The options for setting the **Worker** instance are incorrect.

**Solution**

1. Check whether the number of **Worker** instances exceeds 8. If yes, destroy idle **Worker** instances.
2. If **WorkerOptions** is set, check the parameter type and validity.

## 10200004 Worker Instance Is Not Running

**Error Message**

The Worker instance is not running.

**Description**

The **Worker** instance is not running when the API is called.

**Possible Causes**

When the API is called, the **Worker** instance has been destroyed or is being destroyed.

**Solution**

Ensure that the **Worker** instance is running properly.

## 10200005 API Not Supported in the Worker Thread

**Error Message**

The called API is not supported in the worker thread.

**Description**

An API that is not supported by the worker thread is called.

**Possible Causes**

The worker thread does not support the API.

**Solution**

Use a supported API.

## 10200006 Worker Data Serialization Exception

**Error Message**

An exception occurred during serialization.

**Description**

An error occurs during serialization.

**Possible Causes**

The type of data to transfer does not support serialization or is imported externally.

**Solution**

Ensure that the data to transfer is a valid serialized object supported by Worker. For details, see [ArkTS Inter-Thread Communication Overview](../../arkts-utils/interthread-communication-overview.md
).

## 10200007 Abnormal Worker File Path

**Error Message**

The worker file path is invalid.

**Description**

The file path is invalid, and the **Worker** instance cannot be loaded.

**Possible Causes**

The worker file path is invalid. As a result, a valid **worker.abc** file cannot be generated during the build.

**Solution**

Ensure that the worker file path complies with the specifications for creating **Worker** instances. For details, see the example under [constructor<sup>9+</sup>](js-apis-worker.md#constructor9).

## 10200009 Buffer Size Error

**Error Message**

The buffer size must be a multiple of ${size}.

**Description**

The buffer size does not meet the requirement.

**Possible Causes**

The buffer size is not an integer multiple of **size**, which can be 16-bit, 32-bit, or 64-bit.

**Solution**

Use a buffer the size of which meets the requirements.
  

## 10200010 Empty Container

**Error Message**

Container is empty.

**Description**

The container to be operated is empty.

**Possible Causes**

No element is added to the container.

**Solution**

Add elements to the container first.

## 10200011 Passed this.object Is Not an Instance of the containers Class

**Error Message**

The {methodName} method cannot be bound.

**Description**

**this.object** passed in the API is not an instance of the **containers** class.

**Possible Causes**

The APIs of the **containers** class do not support **bind()**.

**Solution**

1. Check whether **bind()** is used to call the API.
2. Check whether an object that is not a container instance is assigned to the API.

## 10200012 Constructor Calling Failure

**Error Message**

The {className}'s constructor cannot be directly invoked.

**Description**

A constructor of the **containers** class is called directly to create an instance.

**Possible Causes**

The constructors of the **containers** class cannot be directly called. The keyword **new** must be used.

**Solution**

Use the keyword **new** to create an instance.

## 10200013 Read-Only Property

**Error Message**

${propertyName} cannot be set for the buffer that has only a getter.

**Description**

The buffer ${propertyName} is read-only and cannot be set.

**Possible Causes**

The buffer is read-only.

**Solution**

Do not set the read-only attribute for the buffer.

## 10200014 Non-Concurrent Function Error

**Error Message**

The function is not marked as concurrent.

**Description**

The function is not marked as **concurrent**.

**Possible Causes**

**@Concurrent** is not added to the function required by the task to be executed in the task pool.

**Solution**

Check the functions required by the tasks executed by the task pool and add the **@Concurrent** decorator.

## 10200015 Failed to Cancel a Task That Does Not Exist

**Error Message**

The task to cancel does not exist.

**Description**

This error code is reported when you attempt to cancel a task that does not exist.

**Possible Causes**

The task to cancel does not exist in the task pool.

**Solution**

Before canceling a task, ensure that the task has been placed in the task pool by calling [taskpool.execute](js-apis-taskpool.md#taskpoolexecute-1) and is not finishing. If you are not sure, capture exceptions.

## 10200016 Failed to Cancel a Task Being Executed

**Error Message**

The task to cancel is being executed.

**Description**

This error code is reported when you attempt to cancel a task that is being executed.

**Possible Causes**

The task to cancel is being executed.

**Solution**

Before canceling a task, ensure that the task has been placed in the task pool by calling [taskpool.execute](js-apis-taskpool.md#taskpoolexecute-1) and has not started execution. If you are not sure, capture exceptions.

## 10200017 Failed to Delete an Element That Does Not Exist

**Error Message**

The element does not exist in this container.

**Description**

This error code is reported when you attempt to delete an element that does not exist in the container.

**Possible Causes**

The element to delete does not exist in the container.

**Solution**

Before deleting an element, ensure that the element exists in this container.

## 10200018 Failed to Cancel a Task Group That Does Not Exist

**Error Message**

The task group to cancel does not exist.

**Description**

This error code is reported when you attempt to cancel a task group that does not exist.

**Possible Causes**

The task group to cancel does not exist in the task pool.

**Solution**

Before canceling a task group, ensure that the task group placed in the task pool by calling [taskpool.execute](js-apis-taskpool.md#taskpoolexecute10) and is not finishing. If you are not sure, capture exceptions.

## 10200019 Failed to Call an API of an Unregistered Object

**Error Message**

The globalCallObject is not registered.

**Description**

This error code is reported when you attempt to call an API of an object that is not registered.

**Possible Causes**

The object with the specified name is not registered or has been destroyed on the **Worker** instance of the host thread.

**Solution**

Do not call the API on the object that is not registered or has been destroyed. If the registration or destruction status cannot be determined, use the try-catch mechanism to call the API.

## 10200020 Failed to Call an API of a Registered Object

**Error Message**

The method to be called is not callable or is an async method or a generator.

**Description**

This error code is reported when you attempt to call an API of an incorrect type on a registered object.

**Possible Causes**

The attribute contained in the object is not callable, the method contained in the object is asynchronous, or the object is returned by the generator function.

**Solution**

Ensure that the attribute contained in the method is callable and that the method itself or its underlying layer is not asynchronous.

## 10200021 Waiting for a Global Call Times Out

**Error Message**

Waiting for a global call timed out.

**Description**

This error code is reported when a global call does not return any value within the specified duration.

**Possible Causes**

The global call does not return any value within the specified duration, which is 5000 ms by default.

**Solution**

Do not call APIs that take a long time to process data, such as complex computing and file read/write. Otherwise, worker threads will be blocked for a long time, resulting in poor running performance.

## 10200022 Functions Not Called in TaskPool

**Error Message**

The function is not called in the TaskPool thread.

**Description**

This error code is reported when the function is not called in a **TaskPool** thread.

**Possible Causes**

The function is called in the UI main thread or in a thread that is not in **TaskPool**.

**Solution**

Ensure that concurrent functions are executed in a **TaskPool** thread. If you are not sure, capture exceptions.

## 10200023 Functions Not Called in Concurrent Functions

**Error Message**

The function is not called in the concurrent function.

**Description**

This error code is reported when the function is not called in a concurrent function.

**Possible Causes**

The function is called in a callback function.

**Solution**

Ensure that the function is called in a concurrent function. If you are not sure, capture exceptions.

## 10200024 Functions Not Registered in the Host Thread

**Error Message**

The callback is not registered on the host side.

**Description**

This error code is reported when this function is called without registering a callback in the host thread.

**Possible Causes**

This function is called without registering a callback in the host thread.

**Solution**

Ensure that the callback has been registered in the host thread before this function is called. If you are not sure, capture exceptions.

## 10200025 Failed to Add a Task with Dependent Tasks to the Queue

**Error Message**

dependent task not allowed.

**Description**

A task that has dependent tasks cannot be added to the queue.

**Possible Causes**

The task to be added to the queue has dependent tasks.

**Solution**

Call [removeDependency()](js-apis-taskpool.md#removedependency11) to remove the dependent tasks first.

## 10200026 Task with a Cyclic Dependency

**Error Message**

There is a circular dependency.

**Description**

The current task has a cyclic dependency.

**Possible Causes**

The current task has a cyclic dependency.

**Solution**

Call [removeDependency()](js-apis-taskpool.md#removedependency11) to remove unnecessary dependencies.

## 10200027 Dependency Does Not Exist

**Error Message**

The dependency does not exist.

**Description**

[removeDependency()](js-apis-taskpool.md#removedependency11) is called to remove a dependent task, but the task does not exist.

**Possible Causes**

The dependent task to remove does not exist.

**Solution**

Ensure that the dependent task to remove has been added by using [addDependency()](js-apis-taskpool.md#adddependency11). If you are not sure, capture exceptions.

## 10200028 Delay Less Than Zero

**Error Message**

The delayTime is less than zero.

**Description**

This error code is reported when the value of [delayTime](js-apis-taskpool.md#taskpoolexecutedelayed11) is less than 0.

**Possible Causes**

The value of [delayTime](js-apis-taskpool.md#taskpoolexecutedelayed11) is less than 0.

**Solution**

Ensure that [delayTime](js-apis-taskpool.md#taskpoolexecutedelayed11) is set to a value greater than 0. If you are not sure, capture exceptions.

## 10200029 ArrayBuffer Cannot Be Set as Both TransferList and CloneList

**Error Message**

An ArrayBuffer cannot be set as both a transfer list and a clone list.

**Description**

An ArrayBuffer cannot be set as both a transfer list and a clone list.

**Possible Causes**

During the transmission of a shared list, an ArrayBuffer is a parameter of both [setTransferList](js-apis-taskpool.md#settransferlist10) and [setCloneList](js-apis-taskpool.md#setclonelist11).

**Solution**

Ensure that an ArrayBuffer is set as either a transfer list or clone list. If you are not sure, capture exceptions.

## 10200030 Lock Does Not Exist

**Error Message**

The lock does not exist.

**Description**

The requested lock does not exist.

**Possible Causes**

An asynchronous lock function uses an incorrect lock name.

**Solution**

Ensure that the correct lock name is used when the API is called.

## 10200031 Calling lockAsync Timed Out

**Error Message**

Timeout exceeded.

**Description**

The [lockAsync](arkts-apis-arkts-utils-locks.md#lockasync) API fails to acquire a lock within the specified period.

**Possible Causes**

A deadlock occurs somewhere.

**Solution**

Check whether a circular dependency exists between locks. Add the **catch** statement to the [lockAsync](arkts-apis-arkts-utils-locks.md#lockasync) call to catch error information, which contains information about existing asynchronous lock instances and possible deadlock warnings.

## 10200201 Concurrent Modification Error

**Error Message**

Concurrent modification error.

**Description**

An error occurs during concurrent modification.

**Possible Causes**

A non-concurrent-safe container provided by **collections** is used, and the result generated when multiple concurrent instances simultaneously modify the container is undefined.

**Solution**

Use asynchronous locks in non-concurrent-safe containers provided by **collections**.

## 10200034 No Callback Function Is Registered for a Listening Task

**Error Message**

The executed task does not support the registration of listeners.

**Description**

The task does not support listener registration.

**Possible Causes**

The callback function is not registered or is registered after the task is executed.

**Solution**

Ensure that the callback function is registered before the task is executed.

## 10200035 doWrite Is Not Implemented

**Error Message**

The doWrite method has not been implemented.

**Description**

The **doWrite** API is not implemented.

**Possible Causes**

The code inherits from the **Writable** class, but does not implement the [doWrite](js-apis-stream.md#dowrite) API.

**Solution**

Implement the **doWrite** API in the inherited class.

## 10200036 Write Operation Is Still Performed After the Stream Ends

**Error Message**

The stream has been ended.

**Description**

The write operation is still performed after the stream ends.

**Possible Causes**

Data is written after the [end](js-apis-stream.md#end) API is called.

**Solution**

Adjust the sequence in which the APIs are called to ensure that no write operation is performed after [end](js-apis-stream.md#end).

## 10200037 Callback Is Invoked Multiple Times

**Error Message**

The callback is invoked multiple times consecutively.

**Description**

The callback is invoked multiple times.

**Possible Causes**

In the [doWrite](js-apis-stream.md#dowrite) implementation code, the callback is invoked multiple times for one write operation.

**Solution**

Check the implementation of [doWrite](js-apis-stream.md#dowrite) and exclude the situation where the callback is invoked multiple times for one write operation.

## 10200038 doRead Is Not Implemented

**Error Message**

The doRead method has not been implemented.

**Description**

The **doRead** API is not implemented.

**Possible Causes**

The code inherits from the **Readable** class, but does not implement the [doRead](js-apis-stream.md#doread) API.

**Solution**

Implement the **doRead** API in the inherited class.

## 10200039 doTransform Is Not Implemented

**Error Message**

The doTransform method has not been implemented for a class that inherits from Transform.

**Description**

The **doTransform** API is not implemented.

**Possible Causes**

The code inherits from the **Transform** class, but does not implement the [doTransform](js-apis-stream.md#dotransform) API.

**Solution**

Implement the **doTransform** API in the inherited class.

## 10200050 Concurrent Task That Has Been Executed Cannot Be Executed Periodically

**Error Message**

The concurrent task has been executed and cannot be executed periodically.

**Description**

The concurrent task that has been executed cannot be executed periodically.

**Possible Causes**

The task has been executed before [executePeriodically](../apis-arkts/js-apis-taskpool.md#taskpoolexecuteperiodically12) is called.

**Solution**

Before calling the API, ensure that the task is not executed. If you are not sure, capture exceptions.

## 10200051 Periodic Task Cannot Be Executed Again

**Error Message**

The periodic task cannot be executed again.

**Description**

A periodic task cannot be executed again.

**Possible Causes**

[execute](../apis-arkts/js-apis-taskpool.md#execute11), [executeDelayed](../apis-arkts/js-apis-taskpool.md#taskpoolexecutedelayed11), [addTask](../apis-arkts/js-apis-taskpool.md#addtask10-1), or [execute](../apis-arkts/js-apis-taskpool.md#taskpoolexecute-1) is called again to execute a periodic call.

**Solution**

Before calling these APIs, ensure that the task is not a periodic task. If you are not sure, capture exceptions.

## 10200052 Periodic Task Cannot Have Dependencies

**Error Message**

The periodic task cannot have a dependency.

**Description**

A periodic task cannot have dependencies.

**Possible Causes**

[removeDependency](../apis-arkts/js-apis-taskpool.md#removedependency11) or [addDependency](js-apis-taskpool.md#adddependency11) is called to remove or add dependencies for a periodic task.

**Solution**

Before calling these APIs, ensure that the task is not a periodic task. If you are not sure, capture exceptions.

## 10200054 Asynchronous Queue Task Discarded

**Error Message**

The asyncRunner task discarded.

**Description**

A task within the waiting list of the asynchronous queue is discarded.

**Possible Causes**

When the number of tasks executed by calling [asyncRunner.execute](../apis-arkts/js-apis-taskpool.md#execute18) exceeds the capacity of the waiting list, the earliest task in the list is discarded.

**Solution**

1. Increase the capacity of the waiting list.
2. Locate the cause of slow task execution and check the task execution logic.

## 10200055 Asynchronous Queue Task Canceled

**Error Message**

The asyncRunner task has been canceled.

**Description**

The task in the asynchronous queue is canceled.

**Possible Causes**

The task is canceled when it is pending in the task pool for processing or when it is in the waiting list.

**Solution**

Before canceling a task, ensure that the task has been distributed to the task pool and started for execution. If you are not sure, capture exceptions.

## 10200056 Asynchronous Queue Task Cannot Have Dependencies

**Error Message**

The task has been executed by AsyncRunner.

**Description**

An asynchronous queue task cannot have dependencies.

**Possible Causes**

[removeDependency](../apis-arkts/js-apis-taskpool.md#removedependency11) or [addDependency](js-apis-taskpool.md#adddependency11) is called to remove or add dependencies for an asynchronous queue task.

**Solution**

Before calling these APIs, ensure that the task is not an asynchronous queue task. If you are not sure, capture exceptions.

## 10200057 Task Cannot Be Executed by Two APIs

**Error Message**

The task cannot be executed by two APIs.

**Description**

Asynchronous queue tasks can be executed only by [asyncRunner.execute](../apis-arkts/js-apis-taskpool.md#execute18), whereas non-asynchronous tasks cannot be executed by [asyncRunner.execute](../apis-arkts/js-apis-taskpool.md#execute18).

**Possible Causes**

1. [sequenceRunner.execute](../apis-arkts/js-apis-taskpool.md#execute11), [executeDelayed](../apis-arkts/js-apis-taskpool.md#taskpoolexecutedelayed11), [addTask](../apis-arkts/js-apis-taskpool.md#addtask10-1), [taskpool.execute](../apis-arkts/js-apis-taskpool.md#taskpoolexecute-1), [asyncRunner.execute](../apis-arkts/js-apis-taskpool.md#execute18), [executePeriodically](../apis-arkts/js-apis-taskpool.md#taskpoolexecuteperiodically12), or [addDependency](js-apis-taskpool.md#adddependency11) is called to execute an asynchronous queue task.
2. [execute](../apis-arkts/js-apis-taskpool.md#execute18) of the asynchronous queue is called again to execute a task that has been executed.

**Solution**

1. When calling these APIs, ensure that the asynchronous queue task will not be executed. If you are not sure, capture exceptions.
2. When calling [execute](../apis-arkts/js-apis-taskpool.md#execute18) of the asynchronous queue, ensure that the task has not been executed. If you are not sure, capture exceptions.

## 10200060 Precision Limit Is Exceeded

**Error Message**

Precision limit exceeded.

**Description**

A **Decimal** function is incorrectly used.

**Possible Causes**

The precision of the function provided by **Decimal** exceeds the limit. This error code may be thrown by the following functions: [pow](js-apis-arkts-decimal.md#pow), [exp](js-apis-arkts-decimal.md#exp), [log](js-apis-arkts-decimal.md#log), [ln](js-apis-arkts-decimal.md#ln), [acos](js-apis-arkts-decimal.md#acos), [asin](js-apis-arkts-decimal.md#asin), [atan](js-apis-arkts-decimal.md#atan), [acosh](js-apis-arkts-decimal.md#acosh), [asinh](js-apis-arkts-decimal.md#asinh), [atanh](js-apis-arkts-decimal.md#atanh), [log2](js-apis-arkts-decimal.md#log2), [log10](js-apis-arkts-decimal.md#log10), and [atan2](js-apis-arkts-decimal.md#atan2).

**Solution**

Use [Decimal.set](js-apis-arkts-decimal.md#set) to set a valid precision.

Example: Decimal.set({precision: 10})

## 10200061 Encryption Method Is Unavailable

**Error Message**

crypto unavailable.

**Description**

A **Decimal** function is incorrectly used.

**Possible Causes**

When [crypto](js-apis-arkts-decimal.md#decimalconfig) of **Decimal** is set or the [Decimal.random](js-apis-arkts-decimal.md#random) function is used, the encryption method fails to be used.

**Solution**

Use [Decimal.set](js-apis-arkts-decimal.md#set) to cancel the encryption algorithm.

Example: Decimal.set({crypto: false})

## 10200062 XML Cumulative Length Exceeded

**Error Message**

The cumulative length of xml has exceeded the upper limit 100000.

**Description**

The cumulative length of XML characters has exceeded the upper limit of 100,000.

**Possible Causes**

The total length of parameters set in the called API exceeds the upper limit of 100,000.

**Solution**

Reduce the length of the parameters set in the current API.

## 10200063 XML Declaration or Attribute Position Error

**Error Message**

Illegal position for xml.

**Description**

The XML file declaration or attribute position is incorrect.

**Possible Causes**

The element positions are not set according to the XML standard format.

**Solution**

Set the element positions according to the XML standard.

## 10200064 Input String Cannot Be Empty

**Error Message**

Cannot be an empty string.

**Description**

The input string cannot be empty.

**Possible Causes**

The input string is empty.

**Solution**

Provide a valid non-empty string as input.

## 10200065 Mismatched Element Start and End Tags

**Error Message**

There is no match between the startElement and the endElement.

**Description**

The start tag and end tag of an element are not properly matched.

**Possible Causes**

The end tag is written before the start tag.

**Solution**

Write the start tag before the end tag.

## 10200066 Incorrect Encoding Format

**Error Message**

Incorrect encoding format, only support utf-8.

**Description**

The encoding format is incorrect. Only UTF-8 is supported.

**Possible Causes**

The encoding format is not UTF-8.

**Solution**

Change the encoding format to UTF-8.

## 10200068 Using a Released or Detached ArrayBuffer

**Error Message**

The underlying ArrayBuffer is null or detach.

**Description**

An ArrayBuffer that has been released or detached is being used.

**Possible Causes**

The ArrayBuffer has been detached, or the ArrayBuffer is null.

**Solution**

Ensure that the ArrayBuffer being used is available. If you are not sure, capture exceptions.

## 10200301 Failed to Load the Native Module

**Error Message**

Loading native module failed.

**Description**

This error code is returned when the native module fails to be loaded.

**Possible Causes**

1. The native module does not exist in the corresponding path.
2. The module content is incorrect and cannot be loaded correctly.

**Solution**

Check whether the native module to be loaded is in the current package.
