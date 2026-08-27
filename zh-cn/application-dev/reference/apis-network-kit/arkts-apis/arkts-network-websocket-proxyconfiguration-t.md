# ProxyConfiguration

```TypeScript
export type ProxyConfiguration = 'system' | 'no-proxy' | HttpProxy
```

网络代理配置信息

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'system' | 使用系统默认网络代理。 |
| 'no-proxy' | 不使用网络代理。 |
| HttpProxy | 使用指定的网络代理。 |
