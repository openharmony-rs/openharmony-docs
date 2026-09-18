# @ohos.application.testRunner

The **TestRunner** module provides a test framework. You can use the APIs of this module to prepare the unit test
 environment and run test cases.
 To implement your own unit test framework, extend this class and override its APIs.

> **NOTE**
 >
 > The APIs of this module can be used only in [JsUnit](../../../application-test/unittest-guidelines.md).



## Modules to Import

```TypeScript
import { TestRunner } from '@kit.TestKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TestRunner](arkts-test-application-testrunner-testrunner-i.md) | Base class for the test framework. If you want to implement your own unit test framework, you must inherit this class and overrides all its methods. |

### Types

| Name | Description |
| --- | --- |
| [OnStopFn](arkts-test-onstopfn-t.md) | Stop all test cases. |
