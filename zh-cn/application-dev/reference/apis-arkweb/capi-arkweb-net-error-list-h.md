# arkweb_net_error_list.h
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloCrease-->

## 概述

声明ArkWeb网络协议栈错误码。

**库：** libohweb.so

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWeb_NetError](#arkweb_neterror) | ArkWeb_NetError | 定义ArkWeb网络协议栈错误码。 |

## 枚举类型说明

### ArkWeb_NetError

```
enum ArkWeb_NetError
```

**描述：**

定义ArkWeb网络协议栈错误码。

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKWEB_NET_OK = 0 | 正常。 |
| ARKWEB_ERR_IO_PENDING = -1 | 异步IO操作尚未完成。这通常并不表示致命错误。通常，这个错误将作为通知生成，以等待某个外部通知，表明IO操作最终已完成。 |
| ARKWEB_ERR_FAILED = -2 | 发生了通用故障。 |
| ARKWEB_ERR_ABORTED = -3 | 操作被中止（由于用户操作）。 |
| ARKWEB_ERR_INVALID_ARGUMENT = -4 | 该函数的参数不正确。 |
| ARKWEB_ERR_INVALID_HANDLE = -5 | 句柄或文件描述符无效。 |
| ARKWEB_ERR_FILE_NOT_FOUND = -6 | 文件或目录无法找到。 |
| ARKWEB_ERR_TIMED_OUT = -7 | 操作超时。 |
| ARKWEB_ERR_FILE_TOO_LARGE = -8 | 文件过大。 |
| ARKWEB_ERR_UNEXPECTED = -9 | 发生了一个意外的错误。这可能是由编程错误或无效的假设导致的。 |
| ARKWEB_ERR_ACCESS_DENIED = -10 | 访问除网络外的资源被拒绝。 |
| ARKWEB_ERR_NOT_IMPLEMENTED = -11 | 由于功能未实现，操作失败。 |
| ARKWEB_ERR_INSUFFICIENT_RESOURCES = -12 | 没有足够的资源来完成操作。 |
| ARKWEB_ERR_OUT_OF_MEMORY = -13 | 内存溢出。 |
| ARKWEB_ERR_UPLOAD_FILE_CHANGED = -14 | 文件上传失败，因为文件的修改时间与预期不同。 |
| ARKWEB_ERR_SOCKET_NOT_CONNECTED = -15 | socket未连接。 |
| ARKWEB_ERR_FILE_EXISTS = -16 | 文件已存在。 |
| ARKWEB_ERR_FILE_PATH_TOO_LONG = -17 | 文件路径或者文件名过长。 |
| ARKWEB_ERR_FILE_NO_SPACE = -18 | 磁盘上剩余空间不足。 |
| ARKWEB_ERR_FILE_VIRUS_INFECTED = -19 | 文件含有病毒。 |
| ARKWEB_ERR_BLOCKED_BY_CLIENT = -20 | 客户端选择阻止该请求。 |
| ARKWEB_ERR_NETWORK_CHANGED = -21 | 网络发生变化。 |
| ARKWEB_ERR_BLOCKED_BY_ADMINISTRATOR = -22 | 请求被域管理员配置的URL阻止列表所阻止。 |
| ARKWEB_ERR_SOCKET_CONNECTED = -23 | socket已连接。 |
| ARKWEB_ERR_UPLOAD_STREAM_REWIND_NOT_SUPPORTED = -25 | 由于重试或重定向，需要重新读取上传流，但上传流不支持该操作，因此上传失败。 |
| ARKWEB_ERR_CONTEXT_SHUT_DOWN = -26 | 请求失败，因为URLRequestContext正在关闭或已经关闭。 |
| ARKWEB_ERR_BLOCKED_BY_RESPONSE = -27 | 请求失败，因为响应不满足要求（例如“X-Frame-Options”和“Content Security Policy”检查以及“Cross Origin Resource Policy”）。 |
| ARKWEB_ERR_CLEARTEXT_NOT_PERMITTED = -29 | 由于系统策略禁止某些或所有明文请求，请求被阻止。 |
| ARKWEB_ERR_BLOCKED_BY_CSP = -30 | 请求被内容安全策略阻止。 |
| ARKWEB_ERR_H2_OR_QUIC_REQUIRED = -31 | 由于没有H/2或QUIC会话，请求被阻止。 |
| ARKWEB_ERR_BLOCKED_BY_ORB = -32 | 请求被CORB或ORB阻止。 |
| ARKWEB_ERR_CONNECTION_CLOSED = -100 | 连接已关闭（对应于TCP FIN）。 |
| ARKWEB_ERR_CONNECTION_RESET = -101 | 连接被重置（对应于TCP RST）。 |
| ARKWEB_ERR_CONNECTION_REFUSED = -102 | 连接尝试被拒绝。 |
| ARKWEB_ERR_CONNECTION_ABORTED = -103 | 由于未收到发送数据的ACK而导致连接超时。这可能包括未收到ACK的FIN数据包。 |
| ARKWEB_ERR_CONNECTION_FAILED = -104 | 连接尝试失败。 |
| ARKWEB_ERR_NAME_NOT_RESOLVED = -105 | 域名无法解析。 |
| ARKWEB_ERR_INTERNET_DISCONNECTED = -106 | 网络断开。 |
| ARKWEB_ERR_SSL_PROTOCOL_ERROR = -107 | 发生了SSL协议错误。 |
| ARKWEB_ERR_ADDRESS_INVALID = -108 | IP地址或端口号无效（例如，无法连接到IP地址0或端口0）。 |
| ARKWEB_ERR_ADDRESS_UNREACHABLE = -109 | IP地址无法访问。这通常意味着没有到达指定主机或网络的路由。 |
| ARKWEB_ERR_SSL_CLIENT_AUTH_CERT_NEEDED = -110 | 服务器请求SSL客户端身份验证的客户端证书。 |
| ARKWEB_ERR_TUNNEL_CONNECTION_FAILED = -111 | 无法通过代理建立隧道连接。 |
| ARKWEB_ERR_NO_SSL_VERSIONS_ENABLED = -112 | 未启用任何SSL协议版本。 |
| ARKWEB_ERR_SSL_VERSION_OR_CIPHER_MISMATCH = -113 | 客户端和服务器不支持通用的SSL协议版本或密码套件。 |
| ARKWEB_ERR_SSL_RENEGOTIATION_REQUESTED = -114 | 服务器请求重新协商（重新握手）。 |
| ARKWEB_ERR_PROXY_AUTH_UNSUPPORTED = -115 | 代理请求进行身份验证（用于建立隧道，但使用的方法不受支持）。 |
| ARKWEB_ERR_BAD_SSL_CLIENT_AUTH_CERT = -117 | SSL握手未能成功，原因是客户端证书不正确或缺失。 |
| ARKWEB_ERR_CONNECTION_TIMED_OUT = -118 | 连接尝试超时。 |
| ARKWEB_ERR_HOST_RESOLVER_QUEUE_TOO_LARGE = -119 | 有太多待处理的DNS解析，因此队列中的一个请求被中止了。 |
| ARKWEB_ERR_SOCKS_CONNECTION_FAILED = -120 | 为目标主机建立到SOCKS代理服务器的连接失败。 |
| ARKWEB_ERR_SOCKS_CONNECTION_HOST_UNREACHABLE = -121 | SOCKS代理服务器无法建立与目标主机的连接，因为该主机无法访问。 |
| ARKWEB_ERR_ALPN_NEGOTIATION_FAILED = -122 | 协商备用协议的请求失败。 |
| ARKWEB_ERR_SSL_NO_RENEGOTIATION = -123 | 对等端发送了SSL no_regregation警报消息。 |
| ARKWEB_ERR_WINSOCK_UNEXPECTED_WRITTEN_BYTES = -124 | Winsock有时会报告写入的数据多于传递的数据。这可能是由于LSP损坏。 |
| ARKWEB_ERR_SSL_DECOMPRESSION_FAILURE_ALERT = -125 | SSL对等端向我们发送了一个致命的decompression_failure警告。这通常发生在对等端错误地认为它支持DEFLATE压缩并选择它时。 |
| ARKWEB_ERR_SSL_BAD_RECORD_MAC_ALERT = -126 | SSL对等端向我们发送了一个致命的bad_record_mac警告。这通常发生在错误支持DEFLATE的服务器上。 |
| ARKWEB_ERR_PROXY_AUTH_REQUESTED = -127 | 代理请求身份验证（用于建立隧道）。 |
| ARKWEB_ERR_PROXY_CONNECTION_FAILED = -130 | 无法创建到代理服务器的连接。在解析其名称或将其套接字连接到代理服务器时发生错误。请注意，这不包括HTTP代理的实际“CONNECT”方法期间的失败。 |
| ARKWEB_ERR_MANDATORY_PROXY_CONFIGURATION_FAILED = -131 | 无法使用强制代理配置。目前，这意味着无法获取、解析或执行强制PAC脚本。 |
| ARKWEB_ERR_PRECONNECT_MAX_SOCKET_LIMIT = -133 | 在预连接时，我们已达到套接字池的最大套接字限制。我们不再尝试预连接更多套接字。 |
| ARKWEB_ERR_SSL_CLIENT_AUTH_PRIVATE_KEY_ACCESS_DENIED = -134 | 使用SSL客户端证书的私钥的权限被拒绝。 |
| ARKWEB_ERR_SSL_CLIENT_AUTH_CERT_NO_PRIVATE_KEY = -135 | SSL客户端证书没有私钥。 |
| ARKWEB_ERR_PROXY_CERTIFICATE_INVALID = -136 | HTTPS代理提供的证书无效。 |
| ARKWEB_ERR_NAME_RESOLUTION_FAILED = -137 | 在尝试进行域名解析（DNS）时发生错误。 |
| ARKWEB_ERR_NETWORK_ACCESS_DENIED = -138 | 访问网络的权限被拒绝。这用于区分很可能是由防火墙导致的错误和其他访问被拒绝的错误。另请参阅ERR_ACCESS_DENIED。 |
| ARKWEB_ERR_TEMPORARILY_THROTTLED = -139 | 请求节流模块取消了此请求，以避免DDOS攻击。 |
| ARKWEB_ERR_HTTPS_PROXY_TUNNEL_RESPONSE_REDIRECT = -140 | 通过HTTPS代理创建SSL隧道连接的请求收到了302（临时重定向）响应。响应体可能包含请求失败原因的说明。 |
| ARKWEB_ERR_SSL_CLIENT_AUTH_SIGNATURE_FAILED = -141 | 我们无法使用客户端证书的私钥签署SSL客户端身份验证握手的CertificateVerify数据。 |
| ARKWEB_ERR_MSG_TOO_BIG = -142 | 消息对于传输来说太大了。（例如，UDP消息超过了大小阈值）。 |
| ARKWEB_ERR_WS_PROTOCOL_ERROR = -145 | Websocket协议错误。表示由于帧格式错误或其他协议违规，我们正在终止连接。 |
| ARKWEB_ERR_ADDRESS_IN_USE = -147 | 当尝试绑定已使用的地址时返回。 |
| ARKWEB_ERR_SSL_HANDSHAKE_NOT_COMPLETED = -148 | 由于SSL握手尚未完成，操作失败。 |
| ARKWEB_ERR_SSL_BAD_PEER_PUBLIC_KEY = -149 | SSL对等方的公钥无效。 |
| ARKWEB_ERR_SSL_PINNED_KEY_NOT_IN_CERT_CHAIN = -150 | 证书与主机名的内置公钥Pins不匹配。Pin在net/http/transport_security_state.cc中设置，并且要求在从叶节点到根节点的路径上存在一组公钥中的一个。 |
| ARKWEB_ERR_CLIENT_AUTH_CERT_TYPE_UNSUPPORTED = -151 | 服务器请求客户端证书，但请求中未包含我们支持的任何类型。 |
| ARKWEB_ERR_SSL_DECRYPT_ERROR_ALERT = -153 | SSL对等端向我们发送了一个致命的decrypt_error警告。这通常发生在对等端无法正确验证签名（在CertificateVerify或ServerKeyExchange中）或验证Finished消息时。 |
| ARKWEB_ERR_WS_THROTTLE_QUEUE_TOO_LARGE = -154 | 待处理的WebSocketJob实例太多，因此新任务没有推送到队列中。 |
| ARKWEB_ERR_SSL_SERVER_CERT_CHANGED = -156 | 在重新协商过程中，SSL服务器证书发生了更改。 |
| ARKWEB_ERR_SSL_UNRECOGNIZED_NAME_ALERT = -159 | SSL服务器向我们发送了一个致命的unrecognized_name警告。 |
| ARKWEB_ERR_SOCKET_SET_RECEIVE_BUFFER_SIZE_ERROR = -160 | 无法按照请求设置套接字的接收缓冲区大小。 |
| ARKWEB_ERR_SOCKET_SET_SEND_BUFFER_SIZE_ERROR = -161 | 无法按照请求设置套接字的发送缓冲区大小。 |
| ARKWEB_ERR_SOCKET_RECEIVE_BUFFER_SIZE_UNCHANGEABLE = -162 |尽管setsockopt返回成功代码，但无法将套接字的接收缓冲区大小设置为所请求的值。 |
| ARKWEB_ERR_SOCKET_SEND_BUFFER_SIZE_UNCHANGEABLE = -163 | 尽管setsockopt返回成功代码，但无法将套接字的发送缓冲区大小设置为所请求的值。 |
| ARKWEB_ERR_SSL_CLIENT_AUTH_CERT_BAD_FORMAT = -164 | 无法将客户端证书从平台存储导入到SSL库中。 |
| ARKWEB_ERR_ICANN_NAME_COLLISION = -166 | 将主机名解析为IP地址列表时，包含了IPv4地址“127.0.53.53”。这是ICANN推荐的一个特殊IP地址，用于指示存在名称冲突，并提醒管理员注意潜在问题。 |
| ARKWEB_ERR_SSL_SERVER_CERT_BAD_FORMAT = -167 | SSL服务器提供了一个无法解码的证书。这不是一个证书错误代码，因为没有可用的X509Certificate对象。这个错误是致命的。 |
| ARKWEB_ERR_CT_STH_PARSING_FAILED = -168 | Certificate Transparency:收到的Signed Tree Head无法解析。 |
| ARKWEB_ERR_CT_STH_INCOMPLETE = -169 | 证书透明度：收到的已签名树头可以成功解析为JSON，但缺少某些字段。 |
| ARKWEB_ERR_UNABLE_TO_REUSE_CONNECTION_FOR_PROXY_AUTH = -170 | 在AuthController用于生成凭据之前，尝试重用连接以发送代理身份验证凭据失败。调用者应该使用新连接重新使用控制器。此错误仅由网络堆栈内部使用。 |
| ARKWEB_ERR_CT_CONSISTENCY_PROOF_PARSING_FAILED = -171 | 证书透明度：无法解析收到的一致性证明。 |
| ARKWEB_ERR_SSL_OBSOLETE_CIPHER = -172 | SSL服务器要求一个已被移除的不受支持的密码套件。在这个密码套件被移除后的一两个版本更新中，作为回退策略，这个错误将被临时发出信号，之后回退策略将被移除。 |
| ARKWEB_ERR_WS_UPGRADE = -173 | 当WebSocket握手成功完成并且连接已升级时，将使用此错误代码取消URLRequest。 |
| ARKWEB_ERR_READ_IF_READY_NOT_IMPLEMENTED = -174 |  Socket ReadIfReady支持尚未实现。这个错误不应该被用户看到，因为正常的Read方法将作为备选方案使用。 |
| ARKWEB_ERR_NO_BUFFER_SPACE = -176 | 没有可用的套接字缓冲区空间。 |
| ARKWEB_ERR_SSL_CLIENT_AUTH_NO_COMMON_ALGORITHMS = -177 | 我们的客户端证书私钥和服务器的首选项之间没有共同的签名算法。 |
| ARKWEB_ERR_EARLY_DATA_REJECTED = -178 | TLS 1.3 Early Data被服务器拒绝。这将在从套接字返回任何数据之前收到。应该禁用Early Data并重试请求。 |
| ARKWEB_ERR_WRONG_VERSION_ON_EARLY_DATA = -179 | 提供了TLS 1.3 Early Data，但服务器以TLS 1.2或更早版本进行响应。这是为了解决Early Data和TLS 1.2之间向后兼容问题的内部错误代码。 |
| ARKWEB_ERR_TLS13_DOWNGRADE_DETECTED = -180 | 启用了TLS 1.3，但协商了一个较低版本，并且服务器返回了一个值，表明它支持TLS 1.3。 |
| ARKWEB_ERR_SSL_KEY_USAGE_INCOMPATIBLE = -181 |  服务器的证书有一个与协商的TLS密钥交换方法不兼容的keyUsage扩展。 |
| ARKWEB_ERR_INVALID_ECH_CONFIG_LIST = -182 | 通过DNS获取的ECHConfigList无法解析。 |
| ARKWEB_ERR_ECH_NOT_NEGOTIATED = -183 | 已启用ECH（Encrypted Client Hello，加密客户端Hello），但服务器无法解密加密的ClientHello。 |
| ARKWEB_ERR_ECH_FALLBACK_CERTIFICATE_INVALID = -184 | ECH（Encrypted Client Hello）已启用，但服务器无法解密加密的ClientHello，并且没有提供对公共名称有效的证书。 |
| ARKWEB_ERR_CERT_COMMON_NAME_INVALID = -200 | 服务器响应了一个证书，其通用名称与主机名不匹配。这可能意味着：1. 攻击者已将我们的流量重定向到他们的服务器，并呈现了一个他们知道私钥的证书。 |
| ARKWEB_ERR_CERT_DATE_INVALID = -201 | 服务器以证书作为响应，但根据我们的时钟，该证书似乎尚未生效或已过期。这可能是以下情况之一：1. 攻击者提供了旧的证书，并设法获取了私钥。2. 服务器配置错误，没有提供有效的证书。3. 我们的时钟错误。 |
| ARKWEB_ERR_CERT_AUTHORITY_INVALID = -202 | 服务器回应了一个由我们不信任的机构签名的证书。这可能意味着：1. 攻击者已经将真实的证书替换为包含其公钥并由其同伙签名的证书。 |
| ARKWEB_ERR_CERT_CONTAINS_ERRORS = -203 | 服务器返回的证书包含错误。此错误无法恢复。MSDN对此错误的描述如下："SSL证书包含错误。"注意：目前尚不清楚这与ERR_CERT_INVALID有何不同。 |
| ARKWEB_ERR_CERT_NO_REVOCATION_MECHANISM = -204 | 该证书没有用于确定其是否被吊销的机制。实际上，此证书无法被吊销。 |
| ARKWEB_ERR_CERT_UNABLE_TO_CHECK_REVOCATION = -205 | 此站点的安全证书的吊销信息不可用。这可能意味着：1. 攻击者已破解证书中的私钥，并阻止了我们尝试查明证书已被吊销的操作。2. 证书未被吊销，但吊销服务器繁忙或不可用。 |
| ARKWEB_ERR_CERT_REVOKED = -206 | 服务器响应的证书已被吊销。我们有能力忽略此错误，但这可能不是正确的做法。 |
| ARKWEB_ERR_CERT_INVALID = -207 | 服务器以无效的证书进行了响应。这个错误无法恢复。MSDN描述此错误如下："SSL证书无效。" |
| ARKWEB_ERR_CERT_WEAK_SIGNATURE_ALGORITHM = -208 | 服务器使用弱签名算法签名的证书进行了响应。 |
| ARKWEB_ERR_CERT_NON_UNIQUE_NAME = -210 | 证书中指定的主机名不是唯一的。 |
| ARKWEB_ERR_CERT_WEAK_KEY = -211 | 服务器响应了一个包含弱密钥（例如，太小的RSA密钥）的证书。 |
| ARKWEB_ERR_CERT_NAME_CONSTRAINT_VIOLATION = -212 | 证书中声明的DNS名称违反了名称约束。 |
| ARKWEB_ERR_CERT_VALIDITY_TOO_LONG = -213 | 证书的有效期太长。 |
| ARKWEB_ERR_CERTIFICATE_TRANSPARENCY_REQUIRED = -214 | 此连接需要证书透明度，但服务器未提供符合策略的CT信息。 |
| ARKWEB_ERR_CERT_SYMANTEC_LEGACY = -215 | 证书链接到不再受信任的旧版Symantec根证书。 |
| ARKWEB_ERR_CERT_KNOWN_INTERCEPTION_BLOCKED = -217 |已知该证书被除设备所有者之外的其他实体拦截。 |
| ARKWEB_ERR_SSL_OBSOLETE_VERSION_OR_CIPHER = -218 | 连接使用了SSL/TLS或加密算法的过时版本。 |
| ARKWEB_ERR_CERT_END = -219 | 紧接在最后一个证书错误代码之后的值。 |
| ARKWEB_ERR_INVALID_URL = -300 | URL无效。 |
| ARKWEB_ERR_DISALLOWED_URL_SCHEME = -301 | URL的scheme不被允许。 |
| ARKWEB_ERR_UNKNOWN_URL_SCHEME = -302 | 该URL的scheme未知。 |
| ARKWEB_ERR_INVALID_REDIRECT = -303 | 尝试加载一个URL导致重定向到一个无效的URL。 |
| ARKWEB_ERR_TOO_MANY_REDIRECTS = -310 | 尝试加载一个URL时发生了太多次重定向。 |
| ARKWEB_ERR_UNSAFE_REDIRECT = -311 | 尝试加载某个URL时出现了不安全的重定向（例如，重定向到file://被视为不安全）。 |
| ARKWEB_ERR_UNSAFE_PORT = -312 | 尝试加载带有不安全端口号的URL。 |
| ARKWEB_ERR_INVALID_RESPONSE = -320 | 服务器的响应无效。 |
| ARKWEB_ERR_INVALID_CHUNKED_ENCODING = -321 | 块传输编码中出现错误。 |
| ARKWEB_ERR_METHOD_UNSUPPORTED = -322 | 服务器不支持该请求方法。 |
| ARKWEB_ERR_UNEXPECTED_PROXY_AUTH = -323 | 响应是407（需要代理身份验证），但我们并没有将请求发送到代理。 |
| ARKWEB_ERR_EMPTY_RESPONSE = -324 | 服务器关闭了连接而没有发送任何数据。 |
| ARKWEB_ERR_RESPONSE_HEADERS_TOO_BIG = -325 | 响应的headers部分过大。 |
| ARKWEB_ERR_PAC_SCRIPT_FAILED = -327 | PAC脚本的执行失败。 |
| ARKWEB_ERR_REQUEST_RANGE_NOT_SATISFIABLE = -328 | 响应是416（请求的范围无法满足，服务器无法满足请求的范围）。 |
| ARKWEB_ERR_MALFORMED_IDENTITY = -329 | 用于身份验证的身份无效。 |
| ARKWEB_ERR_CONTENT_DECODING_FAILED = -330 | 响应体的内容解码失败。 |
| ARKWEB_ERR_NETWORK_IO_SUSPENDED = -331 | 一个操作无法完成，因为所有网络IO都已挂起。 |
| ARKWEB_ERR_SYN_REPLY_NOT_RECEIVED = -332 | 在流上未收到SYN_REPLY就接收到了FLIP数据。 |
| ARKWEB_ERR_ENCODING_CONVERSION_FAILED = -333 | 将响应转换为目标编码失败。 |
| ARKWEB_ERR_UNRECOGNIZED_FTP_DIRECTORY_LISTING_FORMAT = -334 | 服务器发送了一个我们无法理解的FTP目录列表格式。 |
| ARKWEB_ERR_NO_SUPPORTED_PROXIES = -336 | 提供的列表中没有任何受支持的代理。 |
| ARKWEB_ERR_HTTP2_PROTOCOL_ERROR = -337 | 存在一个HTTP/2协议错误。 |
| ARKWEB_ERR_INVALID_AUTH_CREDENTIALS = -338 | 在HTTP认证过程中无法建立凭据。 |
| ARKWEB_ERR_UNSUPPORTED_AUTH_SCHEME = -339 | 尝试了一种此计算机不支持的HTTP身份验证方案。 |
| ARKWEB_ERR_ENCODING_DETECTION_FAILED = -340 | 检测响应的编码失败。 |
| ARKWEB_ERR_MISSING_AUTH_CREDENTIALS = -341 | （GSSAPI）在HTTP身份验证期间没有可用的Kerberos凭据。 |
| ARKWEB_ERR_UNEXPECTED_SECURITY_LIBRARY_STATUS = -342 | 返回了一个意外但已记录的SSPI或GSSAPI状态码。 |
| ARKWEB_ERR_MISCONFIGURED_AUTH_ENVIRONMENT = -343 | 认证环境未正确设置（例如，找不到KDC或主体未知）。 |
| ARKWEB_ERR_UNDOCUMENTED_SECURITY_LIBRARY_STATUS = -344 | 返回了一个未记录的SSPI或GSSAPI状态码。 |
| ARKWEB_ERR_RESPONSE_BODY_TOO_BIG_TO_DRAIN = -345 | HTTP响应太大，无法完全读取。 |
| ARKWEB_ERR_RESPONSE_HEADERS_MULTIPLE_CONTENT_LENGTH = -346 | HTTP响应包含了多个不同的Content-Length响应头。 |
| ARKWEB_ERR_INCOMPLETE_HTTP2_HEADERS = -347 | 已经接收到HTTP/2的响应头，但并非全部——缺失了状态码或版本等响应头，因此我们期望更多的帧来完成它们。 |
| ARKWEB_ERR_PAC_NOT_IN_DHCP = -348 | 无法从DHCP检索PAC URL配置。这可能表明检索DHCP配置失败，或者在DHCP中没有配置PAC URL。 |
| ARKWEB_ERR_RESPONSE_HEADERS_MULTIPLE_CONTENT_DISPOSITION = -349 | HTTP响应包含多个Content-Disposition响应头。 |
| ARKWEB_ERR_RESPONSE_HEADERS_MULTIPLE_LOCATION = -350 | HTTP响应包含了多个Location响应头。 |
| ARKWEB_ERR_HTTP2_SERVER_REFUSED_STREAM = -351 | HTTP/2服务器在未处理请求的情况下拒绝了请求，并发送了带有错误代码NO_ERROR和低于与请求对应的流ID的Last-Stream-ID的GOAWAY帧， |
| ARKWEB_ERR_HTTP2_PING_FAILED = -352 | HTTP/2服务器未响应PING消息。 |
| ARKWEB_ERR_CONTENT_LENGTH_MISMATCH = -354 | 当连接关闭时，HTTP响应主体传输的字节数少于Content-Length头中公布的字节数。 |
| ARKWEB_ERR_INCOMPLETE_CHUNKED_ENCODING = -355 | HTTP响应体使用分块编码传输，但在连接关闭时，终止的零长度区块从未被发送。 |
| ARKWEB_ERR_QUIC_PROTOCOL_ERROR = -356 | 存在QUIC协议错误。 |
| ARKWEB_ERR_RESPONSE_HEADERS_TRUNCATED = -357 | HTTP响应头信息被文件结束符（EOF）截断。 |
| ARKWEB_ERR_QUIC_HANDSHAKE_FAILED = -358 | QUIC加密握手失败。这意味着服务器无法读取发送的任何请求，因此它们可能会被重新发送。 |
| ARKWEB_ERR_HTTP2_INADEQUATE_TRANSPORT_SECURITY = -360 | 传输安全性不适合HTTP/2版本。 |
| ARKWEB_ERR_HTTP2_FLOW_CONTROL_ERROR = -361 | 对等方违反了HTTP/2流控制。 |
| ARKWEB_ERR_HTTP2_FRAME_SIZE_ERROR = -362 | 对等方发送了大小不正确的HTTP/2帧。 |
| ARKWEB_ERR_HTTP2_COMPRESSION_ERROR = -363 | 压缩HTTP/2响应头信息的解码或编码失败。 |
| ARKWEB_ERR_PROXY_AUTH_REQUESTED_WITH_NO_CONNECTION = -364 | 请求的代理身份验证没有有效的客户端套接字句柄。 |
| ARKWEB_ERR_HTTP_1_1_REQUIRED = -365 | 在HTTP/2会话中收到HTTP_1_1_REQUIRED错误代码。 |
| ARKWEB_ERR_PROXY_HTTP_1_1_REQUIRED = -366 | 在通过HTTP/2会话代理时收到HTTP_1_1_REQUIRED错误代码。 |
| ARKWEB_ERR_PAC_SCRIPT_TERMINATED = -367 | PAC脚本已终止并必须重新加载。 |
| ARKWEB_ERR_INVALID_HTTP_RESPONSE = -370 | 服务器应返回HTTP/1.x响应，但未返回。而不是将其视为HTTP/0.9，返回此错误。 |
| ARKWEB_ERR_CONTENT_DECODING_INIT_FAILED = -371 | 初始化内容解码失败。 |
| ARKWEB_ERR_HTTP2_RST_STREAM_NO_ERROR_RECEIVED = -372 | 收到带有NO_ERROR错误代码的HTTP/2 RST_STREAM帧。此错误应由HTTP/2代码内部处理，而不应超过SpdyStream层。 |
| ARKWEB_ERR_HTTP2_PUSHED_STREAM_NOT_AVAILABLE = -373 | 请求声明的推送流不再可用。 |
| ARKWEB_ERR_HTTP2_CLAIMED_PUSHED_STREAM_RESET_BY_SERVER = -374 | 已声明推送的流，随后服务器将其重置。发生这种情况时，应该重试请求。 |
| ARKWEB_ERR_TOO_MANY_RETRIES = -375 | 由于身份验证或证书无效，重试次数过多。 |
| ARKWEB_ERR_HTTP2_STREAM_CLOSED = -376 | 在已关闭的流上收到一个HTTP/2帧。 |
| ARKWEB_ERR_HTTP2_CLIENT_REFUSED_STREAM = -377 | 客户端拒绝了一个HTTP/2流。 |
| ARKWEB_ERR_HTTP2_PUSHED_RESPONSE_DOES_NOT_MATCH = -378 | 基于匹配的URL和请求头，一个HTTP/2推送的流被请求所接收，但是推送的响应头并不匹配请求。 |
| ARKWEB_ERR_HTTP_RESPONSE_CODE_FAILURE = -379 | 服务器返回了非2xx的HTTP响应代码。 |
| ARKWEB_ERR_QUIC_UNKNOWN_CERT_ROOT = -380 | 在QUIC连接上展示的证书未链接到已知根证书，并且连接到的原始服务器不在允许未知根证书的域名列表中。 |
| ARKWEB_ERR_QUIC_GOAWAY_REQUEST_CAN_BE_RETRIED = -381 | 已接收到一个GOAWAY帧，表明请求未得到处理，因此可以安全地在不同的连接上重试。 |
| ARKWEB_ERR_TOO_MANY_ACCEPT_CH_RESTARTS = -382 | ACCEPT_CH重启已被触发太多次。 |
| ARKWEB_ERR_INCONSISTENT_IP_ADDRESS_SPACE = -383 | 在相同的请求期间，远程端点的IP地址空间与先前观察到的值不同。任何受影响的请求的缓存条目都应被标记为无效。 |
| ARKWEB_ERR_CACHED_IP_ADDRESS_SPACE_BLOCKED_BY_LOCAL_NETWORK_ACCESS_POLICY = -384 | 缓存的远程端点的IP地址空间被本地网络访问检查所阻止。 |
| ARKWEB_ERR_CACHE_MISS = -400 | 缓存中没有请求的条目。 |
| ARKWEB_ERR_CACHE_READ_FAILURE = -401 | 无法从磁盘缓存中读取。 |
| ARKWEB_ERR_CACHE_WRITE_FAILURE = -402 | 无法写入磁盘缓存。 |
| ARKWEB_ERR_CACHE_OPERATION_UNSUPPORTED = -403 | 此条目不支持此操作。 |
| ARKWEB_ERR_CACHE_OPEN_FAILURE = -404 | 磁盘缓存无法打开此条目。 |
| ARKWEB_ERR_CACHE_CREATE_FAILURE = -405 | 磁盘缓存无法创建此条目。 |
| ARKWEB_ERR_CACHE_RACE = -406 | 多个事务正在竞相创建磁盘缓存条目。 |
| ARKWEB_ERR_CACHE_CHECKSUM_READ_FAILURE = -407 | 缓存无法读取条目上的校验和记录。 |
| ARKWEB_ERR_CACHE_CHECKSUM_MISMATCH = -408 | 缓存发现一个具有无效校验和的条目。 |
| ARKWEB_ERR_CACHE_LOCK_TIMEOUT = -409 | HTTP缓存的内部错误代码。 |
| ARKWEB_ERR_CACHE_AUTH_FAILURE_AFTER_READ = -410 | 在事务读取某些数据后收到质询，但凭据不可用。 |
| ARKWEB_ERR_CACHE_ENTRY_NOT_SUITABLE = -411 | 针对HTTP缓存的一个内部使用的、非标准的错误代码。 |
| ARKWEB_ERR_CACHE_DOOM_FAILURE = -412 | 磁盘缓存无法删除此条目。 |
| ARKWEB_ERR_CACHE_OPEN_OR_CREATE_FAILURE = -413 | 磁盘缓存无法打开或创建此条目。 |
| ARKWEB_ERR_INSECURE_RESPONSE = -501 | 服务器的响应不安全（例如，存在证书错误）。 |
| ARKWEB_ERR_NO_PRIVATE_KEY_FOR_CERT = -502 | 尝试导入客户端证书失败，因为用户的密钥数据库缺少相应的私钥。 |
| ARKWEB_ERR_ADD_USER_CERT_FAILED = -503 | 向操作系统证书数据库添加证书时发生错误。 |
| ARKWEB_ERR_INVALID_SIGNED_EXCHANGE = -504 | 处理已签名的交换时发生错误。 |
| ARKWEB_ERR_INVALID_WEB_BUNDLE = -505 | 处理Web Bundle源时发生错误。 |
| ARKWEB_ERR_TRUST_TOKEN_OPERATION_FAILED = -506 | 执行Trust Tokens协议操作的请求失败（原因包括：预置条件失败、内部错误、不良响应）。 |
| ARKWEB_ERR_TRUST_TOKEN_OPERATION_SUCCESS_WITHOUT_SENDING_REQUEST = -507 | 在处理一个与Trust Tokens协议相关的操作执行请求时，系统能够执行该请求中的Trust Tokens操作，但并没有将请求发送到其指定的目的地。 |
| ARKWEB_ERR_FTP_FAILED = -601 | FTP控制连接命令失败的通用错误。如果可能的话，请使用或添加一个更具体的错误代码。 |
| ARKWEB_ERR_FTP_SERVICE_UNAVAILABLE = -602 | 服务器目前无法满足请求。这是一个临时错误。FTP响应代码421。 |
| ARKWEB_ERR_FTP_TRANSFER_ABORTED = -603 | 服务器已中止传输。FTP响应代码426。 |
| ARKWEB_ERR_FTP_FILE_BUSY = -604 | 文件正在使用中，或在打开文件时发生了一些其他临时错误条件。FTP响应代码450。 |
| ARKWEB_ERR_FTP_SYNTAX_ERROR = -605 | 由于语法错误，服务器拒绝了我们的命令。FTP响应代码500、501。 |
| ARKWEB_ERR_FTP_COMMAND_UNSUPPORTED = -606 | 服务器不支持我们发出的命令。FTP响应代码502、504。 |
| ARKWEB_ERR_FTP_BAD_COMMAND_SEQUENCE = -607 | 服务器拒绝了我们的命令，因为我们没有按照正确的顺序发出命令。FTP响应代码503。 |
| ARKWEB_ERR_PKCS12_IMPORT_BAD_PASSWORD = -701 | 由于密码不正确，PKCS #12导入失败。 |
| ARKWEB_ERR_PKCS12_IMPORT_FAILED = -702 | 由于其他错误，PKCS #12导入失败。 |
| ARKWEB_ERR_IMPORT_CA_CERT_NOT_CA = -703 | CA导入失败——不是CA证书。 |
| ARKWEB_ERR_IMPORT_CERT_ALREADY_EXISTS = -704 | 导入失败——数据库中已存在证书。 |
| ARKWEB_ERR_IMPORT_CA_CERT_FAILED = -705 | 由于其他错误，CA导入失败。 |
| ARKWEB_ERR_IMPORT_SERVER_CERT_FAILED = -706 | 由于某些内部错误，服务器证书导入失败。 |
| ARKWEB_ERR_PKCS12_IMPORT_INVALID_MAC = -707 | PKCS #12导入失败，因为MAC（消息认证码）无效。 |
| ARKWEB_ERR_PKCS12_IMPORT_INVALID_FILE = -708 | PKCS #12导入失败，因为文件无效或已损坏。 |
| ARKWEB_ERR_PKCS12_IMPORT_UNSUPPORTED = -709 | 由于不支持的特性，PKCS #12导入失败。 |
| ARKWEB_ERR_KEY_GENERATION_FAILED = -710 | 密钥生成失败。 |
| ARKWEB_ERR_PRIVATE_KEY_EXPORT_FAILED = -712 | 无法导出私钥。 |
| ARKWEB_ERR_SELF_SIGNED_CERT_GENERATION_FAILED = -713 | 自签名证书生成失败。 |
| ARKWEB_ERR_CERT_DATABASE_CHANGED = -714 | 证书数据库已发生某种更改。 |
| ARKWEB_ERR_CERT_VERIFIER_CHANGED = -716 | 证书验证配置已发生某种更改。 |
| ARKWEB_ERR_DNS_MALFORMED_RESPONSE = -800 | DNS解析程序收到格式错误的响应。 |
| ARKWEB_ERR_DNS_SERVER_REQUIRES_TCP = -801 | DNS服务器需要TCP。 |
| ARKWEB_ERR_DNS_SERVER_FAILED = -802 | DNS服务器失败。对于以下所有错误情况，都会返回此错误：1 - 格式错误 - 名称服务器无法解释查询。2 - 服务器故障 - 名称服务器由于自身问题无法处理这个查询。4 - 未实现 - 名称服务器不支持请求的查询类型。 |
| ARKWEB_ERR_DNS_TIMED_OUT = -803 | DNS事务超时。 |
| ARKWEB_ERR_DNS_CACHE_MISS = -804 | 对于只查询本地源的查找，在缓存或其他本地源中未找到该条目。 |
| ARKWEB_ERR_DNS_SEARCH_EMPTY = -805 | 后缀搜索列表规则阻止了给定主机名的解析。 |
| ARKWEB_ERR_DNS_SORT_ERROR = -806 | 未能根据RFC3484对地址进行排序。 |
| ARKWEB_ERR_DNS_SECURE_RESOLVER_HOSTNAME_RESOLUTION_FAILED = -808 | 未能解析DNS-over-HTTPS服务器的主机名。 |
| ARKWEB_ERR_DNS_NAME_HTTPS_ONLY = -809 | DNS已识别请求因不安全的连接（http/ws）而被禁止。应用程序应该像处理HTTP重定向一样处理这个错误，将连接重定向到安全的https或wss。 |
| ARKWEB_ERR_DNS_REQUEST_CANCELED = -810 | 与此任务相关的所有DNS请求已被取消。 |
| ARKWEB_ERR_DNS_NO_MATCHING_SUPPORTED_ALPN = -811 | HTTPS记录的主机名解析预期未能使用受支持协议的ALPN值进行解析。 |


