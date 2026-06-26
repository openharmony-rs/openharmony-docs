# HTTP Error Codes

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:50:16.972Z pushedAt=2026-06-26T03:00:41.287Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 2300001 Protocol Not Supported

**Error Message**

Unsupported protocol.

**Description**

This error code is reported if the input protocol version is not supported by the server.

**Cause**

The input protocol version is not supported by the server.

**Solution**

Specify a protocol version supported by the server.

## 2300003 Incorrect URL Format

**Error Message**

Invalid URL format or missing URL.

**Description**

The URL format is incorrect or the URL is missing.

**Cause**

1. The input URL contains illegal characters or does not conform to the format specification.

2. The URL is empty or not passed in.

**Solution**

1. Check whether the format of the input URL is correct, and ensure that the URL does not contain illegal characters.

2. Ensure that the URL parameter is not empty.

3. You can search for the log keyword "HttpClient CURLcode result 3" to locate the error.

## 2300005 Failed to Resolve the Domain Name of the Proxy Server

**Error Message**

Failed to resolve the proxy name.

**Description**

This error code is reported if the domain name of the proxy server cannot be resolved.

**Cause**

The URL of the proxy server is incorrect.

**Solution**

Specify a URL of the correct format.

## 2300006 Failed to Resolve the Domain Name of the Host

**Error Message**

Failed to resolve the host name.

**Description**

This error code is reported if the domain name of the host cannot be resolved.

**Cause**

1. The input server domain name is incorrect or does not exist.

2. The network is blocked or the DNS server is inaccessible.

3. The local DNS cache is abnormal.

**Solution**

1. Check whether the domain name in the input URL is correct.

2. Check the network connection status to ensure that the network is available.

3. Try using another DNS server or flush the DNS cache.

4. You can search for the log keyword "HttpClient CURLcode result 6" to locate the error.

## 2300007 Failed to Connect to the Server

**Error Message**

Failed to connect to the server.

**Description**

Failed to establish a connection to the server.

**Cause**

1. The server address or port is incorrect.

2. The server is not started or cannot respond.

3. The network connection is blocked by a firewall.

4. The connection timed out.

**Solution**

1. Check whether the server address and port are correct.

2. Confirm whether the server is running properly.

3. Check whether the firewall configuration allows this connection.

4. Check the network connectivity.

5. You can search for the log keyword "HttpClient CURLcode result 7" to locate the error.

## 2300008 Invalid Data Returned by the Server

**Error Message**

Invalid server response.

**Description**

The server returned illegal data that cannot be parsed.

**Cause**

1. The data returned by the server does not conform to the HTTP protocol format.

2. The proxy server configuration is incorrect, and the proxy address points to a non-HTTP proxy service.

3. The service running on the requested port is not an HTTP/HTTPS service.

4. The server or proxy did not return data according to the protocol specification.

**Solution**

1. Check the server implementation and ensure that the returned data is in a valid HTTP format.

2. If a proxy is used, check whether the proxy configuration is correct, and ensure that the proxy address points to an HTTP proxy service.

3. Check whether the target port of the request runs an HTTP/HTTPS service.

## 2300009 Access to Remote Resources Denied

**Error Message**

Access to the remote resource denied.

**Description**

This error code is reported if the access to remote resources is denied by the server.

**Cause**

The access to the specified resource is denied by the server.

**Solution**

Check whether access to the requested resource is allowed.

## 2300016 HTTP2 Framing Layer Error

**Error Message**

Error in the HTTP2 framing layer.

**Description**

This error code is reported if an error occurs on the HTTP2 framing layer.

**Cause**

HTTP2 is not supported by the server.

**Solution**

Capture and analyze packets to check whether HTTP2 is supported by the server.

## 2300018 Incomplete Data Returned by the Server

**Error Message**

Transferred a partial file.

**Description**

This error code is reported if data returned by the server is incomplete.

**Cause**

1. The server interrupts the connection during transmission.

2. Network instability causes data transmission interruption.

3. The size of the data returned by the server does not match the declared size.

**Solution**

1. Check whether the server implementation is normal.

2. Ensure the stability of the network connection.

3. Check whether a range request is set, causing partial transmission.

4. You can search for the log keyword "HttpClient CURLcode result 18" to locate the error.

## 2300023 Failed to Write Received Data to a Disk or Application

**Error Message**

Failed to write the received data to the disk or application.

**Description**

Failed to write received data to the disk or application.

**Cause**

1. The application does not have the file write permission.

2. The [request](./js-apis-http.md#request) API is called to download data exceeding the size limit (5 MB before API version 23, and 50 MB since API version 23), and the **maxLimit** parameter is not set in [HttpRequestOptions](./js-apis-http.md#httprequestoptions).

3. Insufficient disk space.

4. The [destroy](./js-apis-http.md#destroy) method was called before the data from the previous request was completely received, resulting in incomplete received data.

**Solution**

1. Check whether the application has the file write permission.

2. To download data exceeding 5 MB, set an appropriate **maxLimit** parameter in [HttpRequestOptions](./js-apis-http.md#httprequestoptions), or use the [requestInStream](./js-apis-http.md#requestinstream10) API to initiate a streaming request.

3. Check whether the disk space is sufficient.

4. Ensure that the [destroy](./js-apis-http.md#destroy) method is called after the request is complete.

5. You can search for the log keyword "HttpClient CURLcode result 23" to locate the error.

## 2300025 Failed to Upload Data

**Error Message**

Upload failed.

**Description**

This error code is reported if data upload fails.

**Cause**

The file is too large or the network is faulty. The server may reject the **STOR** command if FTP is used. The error buffer usually contains the reason from the server.

**Solution**

Check the file size and network status.

## 2300026 Failed to Open or Read Local Data from a File or Application

**Error Message**

Failed to open or read local data from the file or application.

**Description**

This error code is reported if an error occurs while opening or reading local data from a file or application.

**Cause**

The application does not have the data read permission.

**Solution**

Check the permissions granted to the application.

## 2300027 Insufficient Memory

**Error Message**

Out of memory.

**Description**

This error code is reported if the memory is insufficient.

**Cause**

The memory is insufficient.

**Solution**

Check the system memory.

## 2300028 Operation Timeout

**Error Message**

Operation timeout.

**Description**

This error code is reported if the operation times out.

**Cause**

1. TCP connection timed out (**connectTimeout** defaults to 60000 ms).

2. Data read/write timed out (**readTimeout** defaults to 60000 ms).

3. Network instability caused a response delay.

4. The server load is too high, and the processing speed is slow.

**Solution**

1. Check the network connection status and ensure that the network is stable.

2. Adjust the **readTimeout** or **connectTimeout** parameters as required.

3. Check the server load.

4. You can search for the log keyword "HttpClient CURLcode result 28" to locate the error.

## 2300047 Maximum Redirections Reached

**Error Message**

The number of redirections reaches the maximum allowed.

**Description**

This error code is reported if the number of redirections reaches the maximum.

**Cause**

Redirections are too frequent.

**Solution**

Check the server implementation.

## 2300052 No Content Returned by the Server

**Error Message**

The server returned nothing (no header or data).

**Description**

This error code is reported if no content is returned by the server.

**Cause**

This problem is probable due to server implementation.

**Solution**

Check the server implementation.

## 2300055 Failed to Send Network Data

**Error Message**

Failed to send data to the peer.

**Description**

This error code is reported if an error occurs while sending network data to the peer end.

**Cause**

This problem is probable due to a network fault.

**Solution**

Rectify network faults.

## 2300056 Failed to Receive Network Data

**Error Message**

Failed to receive data from the peer.

**Description**

Failed to receive data from the peer; network data reception failed.

**Cause**

1. The network connection is interrupted or unstable.

2. The server closed the connection.

3. An exception occurred while the peer was sending data.

**Solution**

1. Check the network connection status.

2. Ensure whether the server is running properly.

3. Initiate the request again.

4. You can search for the log keyword "HttpClient CURLcode result 56" to locate the error.

## 2300058 Local SSL Certificate Error

**Error Message**

Local SSL certificate error.

**Description**

This error code is reported if the local SSL certificate is incorrect.

**Cause**

The format of the SSL certificate is incorrect.

**Solution**

Check the format of the SSL certificate.

## 2300059 Failed to Use the Specified SSL Cipher Algorithm

**Error Message**

The specified SSL cipher cannot be used.

**Description**

This error code is reported if the specified SSL cipher algorithm cannot be used.

**Cause**

The system does not support the cipher algorithm negotiated between the client and server.

**Solution**

Capture and analyze packets to check whether the cipher algorithm is supported.

## 2300060 Incorrect SSL Certificate or SSH Key of the Remote Server

**Error Message**

Invalid SSL peer certificate or SSH remote key.

**Description**

Remote server SSL certificate or SSH key verification failed.

**Cause**

1. The server certificate has expired.

2. The certificate is not issued by a trusted CA.

3. The certificate domain name does not match the requested domain name.

4. SSL Pinning (**certificatePinning**) is configured for the certificate, but the public key hash does not match. The log prompts "Specified pinned public key did not match".

5. The certificate chain is incomplete.

**Solution**

1. It is recommended to refer to [Certificate Verification Process on the TLS Client](../../network/http-request.md#certificate-verification-process-on-the-tls-client) to locate the cause of the problem.

2. If **certificatePinning** is configured, check whether the public key hash is correct.

3. Check whether the server certificate has expired or whether the domain name matches.

4. You can search for the log keyword "HttpClient CURLcode result 60" to locate the error.

## 2300061 Unrecognized or Incorrect HTTP Encoding Format

**Error Message**

Invalid HTTP encoding format.

**Description**

This error code is reported if the HTTP encoding format cannot be identified or is incorrect.

**Cause**

The HTTP encoding format is incorrect.

**Solution**

Check the server implementation. Currently, only gzip encoding is supported.

## 2300063 Maximum File Size Exceeded

**Error Message**

Maximum file size exceeded.

**Description**

This error code is reported if the maximum file size is exceeded.

**Cause**

The downloaded file is too large.

**Solution**

Check the server implementation.

## 2300070 Insufficient Server Disk Space

**Error Message**

Remote disk full.

**Description**

This error code is reported if the server disk space is insufficient.

**Cause**

The server disk is full.

**Solution**

Check the server disk space.

## 2300073 Uploaded File Already Exists

**Error Message**

Remote file already exists.

**Description**

This error code is reported if the server finds that the uploaded file already exists.

**Cause**

The uploaded file already exists.

**Solution**

Check the server for files that already exist.

## 2300077 No SSL CA Certificate or Access Permission

**Error Message**

The SSL CA certificate does not exist or is inaccessible.

**Description**

This error code is reported if the SSL CA certificate does not exist or the access permission is not available.

**Cause**

The SSL CA certificate is not available or the access permission is not granted.

**Solution**

Check whether the SSL CA certificate exists or the access permission is granted.

## 2300078 URL Requested File Not Found

**Error Message**

Remote file not found.

**Description**

This error code is reported if the file requested by the specified URL does not exist.

**Cause**

The file requested by the specified URL does not exist.

**Solution**

Check whether the file requested by the specified URL exists.

## 2300094 Identity Verification Failed

**Error Message**

Authentication error.

**Description**

This error code is reported if identity verification fails.

**Cause**

The specified identity verification field does not match that on the server.

**Solution**

Check whether the specified identity verification field matches that on the server.

## 2300997 Plaintext HTTP Access Intercepted

**Error Message**

Cleartext traffic not permitted.

**Description**

This error code is reported if plaintext HTTP access is intercepted.

**Cause**

The plaintext access is not allowed in the **network_config.json** file.

**Solution**

Check the setting of the **cleartextTrafficPermitted** field in the **network_config.json** file.

## 2300998 Domain Access Denied

**Error Message**

It is not allowed to access this domain.

**Description**

This error code is reported if access to a certain domain is prohibited.

**Cause**

1. The atomic service application did not correctly configure the server domain name.

2. The accessed domain name is not in the configured trustlist.

3. The domain name configuration has not taken effect yet (it takes more than one day for the configuration to take effect).

**Solution**

Configure a correct server domain name for the atomic service. For details, see [Configuring Server Domain Names](https://developer.huawei.com/consumer/en/doc/atomic-guides/agc-help-harmonyos-server-domain). The server domain name configuration takes effect more than one day after being set.

## 2300999 Internal Error

**Error Message**

Internal error.

**Description**

Internal error of the HTTP module, usually caused by unmapped errors returned by the underlying network library or other internal exceptions.

**Cause**

1. **Unmapped error from the underlying network library**:

   - The HTTP error code mapping rule is 2300000 + CURL error code. When the error code returned by CURL is not defined in the mapping table, 2300999 is returned uniformly.

   - For example, CURL error code 1 maps to 2300001, and CURL error code 28 maps to 2300028. If the error code returned by CURL has no corresponding mapping, 2300999 is returned.

   - **Log keyword**: `CURLcode result` (The specific CURL error code value will be printed in the log.)

2. **HTTP3 protocol issue**:

   - When the HTTP3 protocol is used, there are other configuration errors before the request starts.

   - **Log keyword**: `error_.GetErrorCode()=`. The request protocol is HTTP3.

3. **Global interceptor verification failed**:

   - The global request interceptor verification failed.

   - **Log keywords**: `GlobalRequestInterceptorCheck fail`, `GlobalRequestInterceptorCheck failed`

**Solution**

1. **For underlying network library errors**:

   - View the complete log to obtain the underlying CURL error code.

   - Refer to the [CURL Error Code Documentation](https://curl.se/libcurl/c/libcurl-errors.html) to understand the specific error meaning.

   - Take corresponding measures based on the error type (network connection, SSL certificate, timeout, etc.).

2. **For HTTP3 protocol issues**:

   - If the HTTP3 protocol is used, check whether there are other errors in the request configuration (such as URL format, permissions, etc.).

   - Check the specific error information in the log and prioritize resolving that error.

   - Consider downgrading to the HTTP/2 or HTTP/1.1 protocol.

3. **For global interceptor issues**:

   - Check whether a global HTTP interceptor is configured.

   - Check whether the implementation of the interceptor callback is correct.

4. **General measures**:

   - Try to recreate the HTTP request object to avoid using an invalidated object.

   - Check the memory usage to ensure that system resources are sufficient.

   - If the problem persists, collect complete logs and submit a problem report, and contact technical support for help.

   - Simplify the request configuration and locate which configuration item causes the problem.