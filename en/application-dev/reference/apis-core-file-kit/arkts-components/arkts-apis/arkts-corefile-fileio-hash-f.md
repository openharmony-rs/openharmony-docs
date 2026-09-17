# hash

## Modules to Import

```TypeScript
```

## hash

```TypeScript
declare function hash(path: string, algorithm: string): Promise<string>
```

Calculates the hash value of a file. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [hash](arkts-corefile-file-hash.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| algorithm | string | Yes | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise that returns the hash value. The hash value is a hexadecimal string consisting of digits and uppercase letters. |


## hash

```TypeScript
declare function hash(path: string, algorithm: string, callback: AsyncCallback<string>): void
```

Calculates the hash value of a file. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [hash](arkts-corefile-file-hash.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file. |
| algorithm | string | Yes | Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**. **sha256** is recommended for security purposes. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the hash value obtained. The hash value is a hexadecimal string consisting of digits and uppercase letters. |
