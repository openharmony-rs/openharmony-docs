# 记忆链接错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 32100001 文件创建失败  
**错误信息**  
Internal handling failed. File creation failed.  

**错误描述**  
当调用记忆链接模块接口时，若服务异常，会报此错误码。  

**可能原因**  
服务状态异常。  

**处理步骤**
1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。  
2. 连续重试3次不可用则停止尝试，返回原始图片文件。  


## 32100002 编码程序执行失败  
**错误信息**  
Encoding failed. Possible causes: 1. Image processing error; 2. Channel coding error. 

**错误描述**  
调用记忆链接编码接口encodeImage时，若因为算法原因编码失败，会报此错误码。

**可能原因**  
算法流程执行时内存申请失败，或其他原因导致计算失败。  

**处理步骤**  
1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。  
2. 连续重试3次不可用则停止尝试，返回原始图片文件。  

## 32100003 解码程序执行失败  
**错误码信息**  
Decoding failed. Possible causes: 1. Image not encoded; 2. Image destroyed. 

**错误描述**  
当调用记忆链接解码接口decodeImage时，若因为算法原因导致解码失败，会报此错误码。

**可能原因**  
算法流程执行时内存申请失败，或其他原因导致计算失败。  

**处理步骤**  
1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。  
2. 连续重试3次不可用则停止尝试，返回空链接。  


## 32100004 订阅失败  
**错误码信息**  
Subscription failed. Possible causes: 1. Abnormal system capability; 2. IPC exception; 3. Algorithm loading exception. 

**错误描述**  
当调用metadataBinding模块on接口时，若订阅失败，会报此错误码。

**可能原因**  
订阅异常。  

**处理步骤**  
1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。
2. 连续重试3次不可用则停止尝试。  

## 32100005 取消订阅失败  

**错误码信息**  
Unsubscription failed. Possible causes: 1. Abnormal system capability; 2. IPC exception. 

**错误描述**  
当调用metadataBinding模块off接口时，若取消订阅失败，会报此错误码。  

**可能原因**  
取消订阅异常。  

**处理步骤**
1. 定时重试操作，如间隔1s或者按照指数增长间隔重试。
2. 连续重试3次不可用则停止尝试。