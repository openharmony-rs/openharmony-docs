# PrintTask

打印任务完成后的事件监听回调接口类。

**起始版本：** 10

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## off('block')

```TypeScript
off(type: 'block', callback?: Callback<void>): void
```

取消打印任务阻塞的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'block' | 是 | 取消监听，监听字段：block，表示打印任务阻塞。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务阻塞事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('block', () => {
                            console.info('unregister state block');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## off('succeed')

```TypeScript
off(type: 'succeed', callback?: Callback<void>): void
```

取消打印任务成功的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'succeed' | 是 | 取消监听，监听字段：succeed，表示打印任务成功。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务成功事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('succeed', () => {
                            console.info('unregister state succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## off('fail')

```TypeScript
off(type: 'fail', callback?: Callback<void>): void
```

取消打印任务失败的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fail' | 是 | 取消监听，监听字段：fail，表示打印任务失败。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务失败事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('fail', () => {
                            console.info('unregister state fail');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## off('cancel')

```TypeScript
off(type: 'cancel', callback?: Callback<void>): void
```

取消打印任务被取消的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cancel' | 是 | 取消监听，监听字段：cancel，表示打印任务被取消。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务被取消事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('cancel', () => {
                            console.info('unregister state cancel');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on('block')

```TypeScript
on(type: 'block', callback: Callback<void>): void
```

注册打印任务阻塞的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'block' | 是 | 注册监听，监听字段：block，表示打印任务阻塞。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务阻塞。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('block', () => {
                            console.info('print state is block');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on('succeed')

```TypeScript
on(type: 'succeed', callback: Callback<void>): void
```

注册打印任务成功的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'succeed' | 是 | 注册监听，监听字段：succeed，表示打印任务成功。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('succeed', () => {
                            console.info('print state is succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on('fail')

```TypeScript
on(type: 'fail', callback: Callback<void>): void
```

注册打印任务失败的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fail' | 是 | 注册监听，监听字段：fail，表示打印任务失败。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('fail', () => {
                            console.info('print state is fail');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on('cancel')

```TypeScript
on(type: 'cancel', callback: Callback<void>): void
```

注册打印任务被取消的监听，使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.PRINT

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cancel' | 是 | 注册监听，监听字段：cancel，表示打印任务被取消。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务被取消。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('cancel', () => {
                            console.info('print state is cancel');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error(`Failed to print. Code: ${error.code}, message: ${error.message}`);
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```
