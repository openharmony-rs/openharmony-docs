# ProxyConstructor

```TypeScript
interface ProxyConstructor
```

## Modules to Import

```TypeScript
```

## [[Construct]]

```TypeScript
new <T extends object>(target: T, handler: ProxyHandler<T>): T
```

Creates a Proxy object. The Proxy object allows you to create an object that can be used in place of the original object, but which may redefine fundamental Object operations like getting, setting, and defining properties. Proxy objects are commonly used to log property accesses, validate, format, or sanitize inputs.

<!--Device-ProxyConstructor-new <T extends object>(target: T, handler: ProxyHandler<T>): T--><!--Device-ProxyConstructor-new <T extends object>(target: T, handler: ProxyHandler<T>): T-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| handler | [ProxyHandler](arkts-lib-es2015-proxy-proxyhandler-i.md)&lt;T&gt; | Yes |  |

## revocable

```TypeScript
revocable<T extends object>(target: T, handler: ProxyHandler<T>): { proxy: T; revoke: () => void; }
```

Creates a revocable Proxy object.

<!--Device-ProxyConstructor-revocable<T extends object>(target: T, handler: ProxyHandler<T>): { proxy: T; revoke: () => void; }--><!--Device-ProxyConstructor-revocable<T extends object>(target: T, handler: ProxyHandler<T>): { proxy: T; revoke: () => void; }-End-->

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | T | Yes |  |
| handler | [ProxyHandler](arkts-lib-es2015-proxy-proxyhandler-i.md)&lt;T&gt; | Yes |  |
