# @system.fetch

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Fetch](arkts-network-system-fetch-fetch-depr-c.md) | **表1** data与Content-Type关系  \| data \| Content-Type \| 说明 \| \| -------- \| -------- \| -------- \| \| string \| 不设置 \| Content-Type默认为 & nbsp;text/plain，data值作为请求的body。 \ | \| string \| 任意 & nbsp;Type \ | data值作为请求的body。 \| \| Object \| 不设置 \| Content-Type默认为application/x-www-form-urlencoded，data按照资源地址规则进行encode拼接作为请求的body。 \| \| Object \| application/x-www-form-urlencoded \| data按照资源地址规则进行encode拼接作为请求的body。 \| |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FetchResponse](arkts-network-system-fetch-fetchresponse-depr-i.md) | **表2** responseType与success中data关系  \| responseType \| data \| 说明 \| \| -------- \| -------- \| -------- \| \| 无 \| string \| 服务器返回的header中的type如果是text/\*或application/json、application/javascript、application/xml，值为文本内容。 \| \| text \| string \| 返回文本内容。 \| \| json \| Object \| 返回json格式的对象。 \| |
