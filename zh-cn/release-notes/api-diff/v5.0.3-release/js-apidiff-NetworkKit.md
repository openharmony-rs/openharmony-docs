| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|API跨平台权限变更|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：crossplatform|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：request(url: string, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：request(url: string, options: HttpRequestOptions, callback: AsyncCallback\<HttpResponse>): void;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：request(url: string, options?: HttpRequestOptions): Promise\<HttpResponse>;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：2300997,2300998|api/@ohos.net.http.d.ts|
|新增错误码|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：NA|类名：UDPSocket；<br>API声明：send(options: UDPSendOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：NA|类名：TCPSocket；<br>API声明：connect(options: TCPConnectOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions, callback: AsyncCallback\<void>): void;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：NA|类名：TLSSocket；<br>API声明：connect(options: TLSConnectOptions): Promise\<void>;<br>差异内容：2301206,2301207,2301208,2301209,2301210,2301211,2301212,2301213|api/@ohos.net.socket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302998|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback\<boolean>): void;<br>差异内容：2302998|api/@ohos.net.webSocket.d.ts|
|新增错误码|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：NA|类名：WebSocket；<br>API声明：connect(url: string, options?: WebSocketRequestOptions): Promise\<boolean>;<br>差异内容：2302998|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace eap<br>差异内容：declare namespace eap|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：function regCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;<br>差异内容：function regCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：function unregCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;<br>差异内容：function unregCustomEapHandler(netType: number, eapCode: number, eapType: number, callback: Callback\<EapData>): void;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：function replyCustomEapData(result: CustomResult, data: EapData): void;<br>差异内容：function replyCustomEapData(result: CustomResult, data: EapData): void;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：function startEthEap(netId: number, profile: EthEapProfile): void;<br>差异内容：function startEthEap(netId: number, profile: EthEapProfile): void;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：function logOffEthEap(netId: number): void;<br>差异内容：function logOffEthEap(netId: number): void;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：interface EapData<br>差异内容：interface EapData|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapData；<br>API声明：msgId: number;<br>差异内容：msgId: number;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapData；<br>API声明：eapBuffer: Uint8Array;<br>差异内容：eapBuffer: Uint8Array;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapData；<br>API声明：bufferLen: number;<br>差异内容：bufferLen: number;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：enum CustomResult<br>差异内容：enum CustomResult|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：CustomResult；<br>API声明：RESULT_FAIL<br>差异内容：RESULT_FAIL|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：CustomResult；<br>API声明：RESULT_NEXT<br>差异内容：RESULT_NEXT|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：CustomResult；<br>API声明：RESULT_FINISH<br>差异内容：RESULT_FINISH|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：enum EapMethod<br>差异内容：enum EapMethod|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_NONE<br>差异内容：EAP_NONE|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_PEAP<br>差异内容：EAP_PEAP|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_TLS<br>差异内容：EAP_TLS|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_TTLS<br>差异内容：EAP_TTLS|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_PWD<br>差异内容：EAP_PWD|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_SIM<br>差异内容：EAP_SIM|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_AKA<br>差异内容：EAP_AKA|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_AKA_PRIME<br>差异内容：EAP_AKA_PRIME|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EapMethod；<br>API声明：EAP_UNAUTH_TLS<br>差异内容：EAP_UNAUTH_TLS|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：enum Phase2Method<br>差异内容：enum Phase2Method|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_NONE<br>差异内容：PHASE2_NONE|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_PAP<br>差异内容：PHASE2_PAP|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_MSCHAP<br>差异内容：PHASE2_MSCHAP|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_MSCHAPV2<br>差异内容：PHASE2_MSCHAPV2|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_GTC<br>差异内容：PHASE2_GTC|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_SIM<br>差异内容：PHASE2_SIM|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_AKA<br>差异内容：PHASE2_AKA|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：Phase2Method；<br>API声明：PHASE2_AKA_PRIME<br>差异内容：PHASE2_AKA_PRIME|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：eap；<br>API声明：interface EthEapProfile<br>差异内容：interface EthEapProfile|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：eapMethod: EapMethod;<br>差异内容：eapMethod: EapMethod;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：phase2Method: Phase2Method;<br>差异内容：phase2Method: Phase2Method;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：identity: string;<br>差异内容：identity: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：anonymousIdentity: string;<br>差异内容：anonymousIdentity: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：caCertAliases: string;<br>差异内容：caCertAliases: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：caPath: string;<br>差异内容：caPath: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：clientCertAliases: string;<br>差异内容：clientCertAliases: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：certEntry: Uint8Array;<br>差异内容：certEntry: Uint8Array;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：certPassword: string;<br>差异内容：certPassword: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：altSubjectMatch: string;<br>差异内容：altSubjectMatch: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：domainSuffixMatch: string;<br>差异内容：domainSuffixMatch: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：realm: string;<br>差异内容：realm: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：plmn: string;<br>差异内容：plmn: string;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：EthEapProfile；<br>API声明：eapSubId: number;<br>差异内容：eapSubId: number;|api/@ohos.net.eap.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace netFirewall<br>差异内容：declare namespace netFirewall|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function setNetFirewallPolicy(userId: number, policy: NetFirewallPolicy): Promise\<void>;<br>差异内容：function setNetFirewallPolicy(userId: number, policy: NetFirewallPolicy): Promise\<void>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function getNetFirewallPolicy(userId: number): Promise\<NetFirewallPolicy>;<br>差异内容：function getNetFirewallPolicy(userId: number): Promise\<NetFirewallPolicy>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function addNetFirewallRule(rule: NetFirewallRule): Promise\<number>;<br>差异内容：function addNetFirewallRule(rule: NetFirewallRule): Promise\<number>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function updateNetFirewallRule(rule: NetFirewallRule): Promise\<void>;<br>差异内容：function updateNetFirewallRule(rule: NetFirewallRule): Promise\<void>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function removeNetFirewallRule(userId: number, ruleId: number): Promise\<void>;<br>差异内容：function removeNetFirewallRule(userId: number, ruleId: number): Promise\<void>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function getNetFirewallRules(userId: number, requestParam: RequestParam): Promise\<FirewallRulePage>;<br>差异内容：function getNetFirewallRules(userId: number, requestParam: RequestParam): Promise\<FirewallRulePage>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：function getNetFirewallRule(userId: number, ruleId: number): Promise\<NetFirewallRule>;<br>差异内容：function getNetFirewallRule(userId: number, ruleId: number): Promise\<NetFirewallRule>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：enum NetFirewallRuleDirection<br>差异内容：enum NetFirewallRuleDirection|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRuleDirection；<br>API声明：RULE_IN = 1<br>差异内容：RULE_IN = 1|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRuleDirection；<br>API声明：RULE_OUT = 2<br>差异内容：RULE_OUT = 2|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：enum FirewallRuleAction<br>差异内容：enum FirewallRuleAction|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：FirewallRuleAction；<br>API声明：RULE_ALLOW = 0<br>差异内容：RULE_ALLOW = 0|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：FirewallRuleAction；<br>API声明：RULE_DENY = 1<br>差异内容：RULE_DENY = 1|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：enum NetFirewallRuleType<br>差异内容：enum NetFirewallRuleType|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRuleType；<br>API声明：RULE_IP = 1<br>差异内容：RULE_IP = 1|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRuleType；<br>API声明：RULE_DOMAIN = 2<br>差异内容：RULE_DOMAIN = 2|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRuleType；<br>API声明：RULE_DNS = 3<br>差异内容：RULE_DNS = 3|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：enum NetFirewallOrderField<br>差异内容：enum NetFirewallOrderField|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallOrderField；<br>API声明：ORDER_BY_RULE_NAME = 1<br>差异内容：ORDER_BY_RULE_NAME = 1|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallOrderField；<br>API声明：ORDER_BY_RECORD_TIME = 100<br>差异内容：ORDER_BY_RECORD_TIME = 100|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：enum NetFirewallOrderType<br>差异内容：enum NetFirewallOrderType|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallOrderType；<br>API声明：ORDER_ASC = 1<br>差异内容：ORDER_ASC = 1|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallOrderType；<br>API声明：ORDER_DESC = 100<br>差异内容：ORDER_DESC = 100|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface NetFirewallPolicy<br>差异内容：interface NetFirewallPolicy|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallPolicy；<br>API声明：isOpen: boolean;<br>差异内容：isOpen: boolean;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallPolicy；<br>API声明：inAction: FirewallRuleAction;<br>差异内容：inAction: FirewallRuleAction;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallPolicy；<br>API声明：outAction: FirewallRuleAction;<br>差异内容：outAction: FirewallRuleAction;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface NetFirewallIpParams<br>差异内容：interface NetFirewallIpParams|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallIpParams；<br>API声明：type: number;<br>差异内容：type: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallIpParams；<br>API声明：family?: number;<br>差异内容：family?: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallIpParams；<br>API声明：address?: string;<br>差异内容：address?: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallIpParams；<br>API声明：mask?: number;<br>差异内容：mask?: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallIpParams；<br>API声明：startIp?: string;<br>差异内容：startIp?: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallIpParams；<br>API声明：endIp?: string;<br>差异内容：endIp?: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface NetFirewallPortParams<br>差异内容：interface NetFirewallPortParams|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallPortParams；<br>API声明：startPort: number;<br>差异内容：startPort: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallPortParams；<br>API声明：endPort: number;<br>差异内容：endPort: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface NetFirewallDomainParams<br>差异内容：interface NetFirewallDomainParams|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallDomainParams；<br>API声明：isWildcard: boolean;<br>差异内容：isWildcard: boolean;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallDomainParams；<br>API声明：domain: string;<br>差异内容：domain: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface NetFirewallDnsParams<br>差异内容：interface NetFirewallDnsParams|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallDnsParams；<br>API声明：primaryDns: string;<br>差异内容：primaryDns: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallDnsParams；<br>API声明：standbyDns?: string;<br>差异内容：standbyDns?: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface NetFirewallRule<br>差异内容：interface NetFirewallRule|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：userId: number;<br>差异内容：userId: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：direction: NetFirewallRuleDirection;<br>差异内容：direction: NetFirewallRuleDirection;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：action: FirewallRuleAction;<br>差异内容：action: FirewallRuleAction;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：type: NetFirewallRuleType;<br>差异内容：type: NetFirewallRuleType;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：isEnabled: boolean;<br>差异内容：isEnabled: boolean;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：id?: number;<br>差异内容：id?: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：appUid?: number;<br>差异内容：appUid?: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：localIps?: Array\<NetFirewallIpParams>;<br>差异内容：localIps?: Array\<NetFirewallIpParams>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：remoteIps?: Array\<NetFirewallIpParams>;<br>差异内容：remoteIps?: Array\<NetFirewallIpParams>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：protocol?: number;<br>差异内容：protocol?: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：localPorts?: Array\<NetFirewallPortParams>;<br>差异内容：localPorts?: Array\<NetFirewallPortParams>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：remotePorts?: Array\<NetFirewallPortParams>;<br>差异内容：remotePorts?: Array\<NetFirewallPortParams>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：domains?: Array\<NetFirewallDomainParams>;<br>差异内容：domains?: Array\<NetFirewallDomainParams>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：NetFirewallRule；<br>API声明：dns?: NetFirewallDnsParams;<br>差异内容：dns?: NetFirewallDnsParams;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface RequestParam<br>差异内容：interface RequestParam|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：RequestParam；<br>API声明：page: number;<br>差异内容：page: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：RequestParam；<br>API声明：pageSize: number;<br>差异内容：pageSize: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：RequestParam；<br>API声明：orderField: NetFirewallOrderField;<br>差异内容：orderField: NetFirewallOrderField;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：RequestParam；<br>API声明：orderType: NetFirewallOrderType;<br>差异内容：orderType: NetFirewallOrderType;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：netFirewall；<br>API声明：interface FirewallRulePage<br>差异内容：interface FirewallRulePage|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：FirewallRulePage；<br>API声明：page: number;<br>差异内容：page: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：FirewallRulePage；<br>API声明：pageSize: number;<br>差异内容：pageSize: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：FirewallRulePage；<br>API声明：totalPage: number;<br>差异内容：totalPage: number;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：FirewallRulePage；<br>API声明：data: Array\<NetFirewallRule>;<br>差异内容：data: Array\<NetFirewallRule>;|api/@ohos.net.netFirewall.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setNetExtAttribute(netHandle: NetHandle, netExtAttribute: string): Promise\<void>;<br>差异内容：function setNetExtAttribute(netHandle: NetHandle, netExtAttribute: string): Promise\<void>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void;<br>差异内容：function setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getNetExtAttribute(netHandle: NetHandle): Promise\<string>;<br>差异内容：function getNetExtAttribute(netHandle: NetHandle): Promise\<string>;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getNetExtAttributeSync(netHandle: NetHandle): string;<br>差异内容：function getNetExtAttributeSync(netHandle: NetHandle): string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setPacUrl(pacUrl: string): void;<br>差异内容：function setPacUrl(pacUrl: string): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getPacUrl(): string;<br>差异内容：function getPacUrl(): string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function setPacFileUrl(pacFileUrl: string): void;<br>差异内容：function setPacFileUrl(pacFileUrl: string): void;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function getPacFileUrl(): string;<br>差异内容：function getPacFileUrl(): string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：connection；<br>API声明：function findProxyForUrl(url: string): string;<br>差异内容：function findProxyForUrl(url: string): string;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：RouteInfo；<br>API声明：isExcludedRoute?: boolean;<br>差异内容：isExcludedRoute?: boolean;|api/@ohos.net.connection.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum AddressFamily<br>差异内容：export enum AddressFamily|api/@ohos.net.http.d.ts|
|新增API|NA|类名：AddressFamily；<br>API声明：DEFAULT = 'CURL_IPRESOLVE_WHATEVER'<br>差异内容：DEFAULT = 'CURL_IPRESOLVE_WHATEVER'|api/@ohos.net.http.d.ts|
|新增API|NA|类名：AddressFamily；<br>API声明：ONLY_V4 = 'CURL_IPRESOLVE_V4'<br>差异内容：ONLY_V4 = 'CURL_IPRESOLVE_V4'|api/@ohos.net.http.d.ts|
|新增API|NA|类名：AddressFamily；<br>API声明：ONLY_V6 = 'CURL_IPRESOLVE_V6'<br>差异内容：ONLY_V6 = 'CURL_IPRESOLVE_V6'|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：caData?: string;<br>差异内容：caData?: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：sslType?: SslType;<br>差异内容：sslType?: SslType;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：clientEncCert?: ClientCert;<br>差异内容：clientEncCert?: ClientCert;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：remoteValidation?: RemoteValidation;<br>差异内容：remoteValidation?: RemoteValidation;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：tlsOptions?: TlsOptions;<br>差异内容：tlsOptions?: TlsOptions;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：serverAuthentication?: ServerAuthentication;<br>差异内容：serverAuthentication?: ServerAuthentication;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：HttpRequestOptions；<br>API声明：addressFamily?: AddressFamily;<br>差异内容：addressFamily?: AddressFamily;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface ServerAuthentication<br>差异内容：export interface ServerAuthentication|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ServerAuthentication；<br>API声明：credential: Credential;<br>差异内容：credential: Credential;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：ServerAuthentication；<br>API声明：authenticationType?: AuthenticationType;<br>差异内容：authenticationType?: AuthenticationType;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsOptions = 'system' \| TlsConfig;<br>差异内容：export type TlsOptions = 'system' \| TlsConfig;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type RemoteValidation = 'system' \| 'skip';<br>差异内容：export type RemoteValidation = 'system' \| 'skip';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type AuthenticationType = 'basic' \| 'ntlm' \| 'digest';<br>差异内容：export type AuthenticationType = 'basic' \| 'ntlm' \| 'digest';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type SslType = 'TLS' \| 'TLCP';<br>差异内容：export type SslType = 'TLS' \| 'TLCP';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface Credential<br>差异内容：export interface Credential|api/@ohos.net.http.d.ts|
|新增API|NA|类名：Credential；<br>API声明：username: string;<br>差异内容：username: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：Credential；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export interface TlsConfig<br>差异内容：export interface TlsConfig|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsConfig；<br>API声明：tlsVersionMin: TlsVersion;<br>差异内容：tlsVersionMin: TlsVersion;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsConfig；<br>API声明：tlsVersionMax: TlsVersion;<br>差异内容：tlsVersionMax: TlsVersion;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsConfig；<br>API声明：cipherSuites?: CipherSuite[];<br>差异内容：cipherSuites?: CipherSuite[];|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' \| 'TLS_AES_256_GCM_SHA384' \| 'TLS_CHACHA20_POLY1305_SHA256';<br>差异内容：export type TlsV13SpecificCipherSuite = 'TLS_AES_128_GCM_SHA256' \| 'TLS_AES_256_GCM_SHA384' \| 'TLS_CHACHA20_POLY1305_SHA256';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_RSA_WITH_AES_256_GCM_SHA384';<br>差异内容：export type TlsV12SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384' \| 'TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256' \| 'TLS_RSA_WITH_AES_128_GCM_SHA256' \| 'TLS_RSA_WITH_AES_256_GCM_SHA384';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA';<br>差异内容：export type TlsV10SpecificCipherSuite = 'TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA' \| 'TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_AES_128_CBC_SHA' \| 'TLS_RSA_WITH_AES_256_CBC_SHA' \| 'TLS_RSA_WITH_3DES_EDE_CBC_SHA';|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type CipherSuite = TlsV13CipherSuite;<br>差异内容：export type CipherSuite = TlsV13CipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV13CipherSuite = TlsV12CipherSuite \| TlsV13SpecificCipherSuite;<br>差异内容：export type TlsV13CipherSuite = TlsV12CipherSuite \| TlsV13SpecificCipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV12CipherSuite = TlsV11CipherSuite \| TlsV12SpecificCipherSuite;<br>差异内容：export type TlsV12CipherSuite = TlsV11CipherSuite \| TlsV12SpecificCipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV11CipherSuite = TlsV10CipherSuite;<br>差异内容：export type TlsV11CipherSuite = TlsV10CipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export type TlsV10CipherSuite = TlsV10SpecificCipherSuite;<br>差异内容：export type TlsV10CipherSuite = TlsV10SpecificCipherSuite;|api/@ohos.net.http.d.ts|
|新增API|NA|类名：http；<br>API声明：export enum TlsVersion<br>差异内容：export enum TlsVersion|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_0 = 4<br>差异内容：TLS_V_1_0 = 4|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_1 = 5<br>差异内容：TLS_V_1_1 = 5|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_2 = 6<br>差异内容：TLS_V_1_2 = 6|api/@ohos.net.http.d.ts|
|新增API|NA|类名：TlsVersion；<br>API声明：TLS_V_1_3 = 7<br>差异内容：TLS_V_1_3 = 7|api/@ohos.net.http.d.ts|
|新增API|NA|类名：UDPSendOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export enum ProxyTypes<br>差异内容：export enum ProxyTypes|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyTypes；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyTypes；<br>API声明：SOCKS5 = 1<br>差异内容：SOCKS5 = 1|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：socket；<br>API声明：export interface ProxyOptions<br>差异内容：export interface ProxyOptions|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：type: ProxyTypes;<br>差异内容：type: ProxyTypes;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：address: NetAddress;<br>差异内容：address: NetAddress;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：username?: string;<br>差异内容：username?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：ProxyOptions；<br>API声明：password?: string;<br>差异内容：password?: string;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：LocalSocketServer；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPConnectOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocket；<br>API声明：getSocketFd(): Promise\<number>;<br>差异内容：getSocketFd(): Promise\<number>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSConnectOptions；<br>API声明：proxy?: ProxyOptions;<br>差异内容：proxy?: ProxyOptions;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TCPSocketServer；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：TLSSocketServer；<br>API声明：close(): Promise\<void>;<br>差异内容：close(): Promise\<void>;|api/@ohos.net.socket.d.ts|
|新增API|NA|类名：VpnConnection；<br>API声明：generateVpnId(): Promise\<string>;<br>差异内容：generateVpnId(): Promise\<string>;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：VpnConfig；<br>API声明：vpnId?: string;<br>差异内容：vpnId?: string;|api/@ohos.net.vpnExtension.d.ts|
|新增API|NA|类名：WebSocketRequestOptions；<br>API声明：skipServerCertVerification?: boolean;<br>差异内容：skipServerCertVerification?: boolean;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：function createWebSocketServer(): WebSocketServer;<br>差异内容：function createWebSocketServer(): WebSocketServer;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocketServerConfig<br>差异内容：export interface WebSocketServerConfig|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServerConfig；<br>API声明：serverIP?: string;<br>差异内容：serverIP?: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServerConfig；<br>API声明：serverPort: number;<br>差异内容：serverPort: number;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServerConfig；<br>API声明：serverCert?: ServerCert;<br>差异内容：serverCert?: ServerCert;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServerConfig；<br>API声明：maxConcurrentClientsNumber: number;<br>差异内容：maxConcurrentClientsNumber: number;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServerConfig；<br>API声明：protocol?: string;<br>差异内容：protocol?: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServerConfig；<br>API声明：maxConnectionsForOneClient: number;<br>差异内容：maxConnectionsForOneClient: number;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface ServerCert<br>差异内容：export interface ServerCert|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：ServerCert；<br>API声明：certPath: string;<br>差异内容：certPath: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：ServerCert；<br>API声明：keyPath: string;<br>差异内容：keyPath: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocketConnection<br>差异内容：export interface WebSocketConnection|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketConnection；<br>API声明：clientIP: string;<br>差异内容：clientIP: string;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketConnection；<br>API声明：clientPort: number;<br>差异内容：clientPort: number;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocketMessage<br>差异内容：export interface WebSocketMessage|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketMessage；<br>API声明：data: string \| ArrayBuffer;<br>差异内容：data: string \| ArrayBuffer;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketMessage；<br>API声明：clientConnection: WebSocketConnection;<br>差异内容：clientConnection: WebSocketConnection;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason: CloseResult) => void;<br>差异内容：export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason: CloseResult) => void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：webSocket；<br>API声明：export interface WebSocketServer<br>差异内容：export interface WebSocketServer|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：start(config: WebSocketServerConfig): Promise\<boolean>;<br>差异内容：start(config: WebSocketServerConfig): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：listAllConnections(): WebSocketConnection[];<br>差异内容：listAllConnections(): WebSocketConnection[];|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：close(connection: WebSocketConnection, options?: webSocket.WebSocketCloseOptions): Promise\<boolean>;<br>差异内容：close(connection: WebSocketConnection, options?: webSocket.WebSocketCloseOptions): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：send(data: string \| ArrayBuffer, connection: WebSocketConnection): Promise\<boolean>;<br>差异内容：send(data: string \| ArrayBuffer, connection: WebSocketConnection): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：stop(): Promise\<boolean>;<br>差异内容：stop(): Promise\<boolean>;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：on(type: 'error', callback: ErrorCallback): void;<br>差异内容：on(type: 'error', callback: ErrorCallback): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：on(type: 'connect', callback: Callback\<WebSocketConnection>): void;<br>差异内容：on(type: 'connect', callback: Callback\<WebSocketConnection>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：on(type: 'messageReceive', callback: Callback\<WebSocketMessage>): void;<br>差异内容：on(type: 'messageReceive', callback: Callback\<WebSocketMessage>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：on(type: 'close', callback: ClientConnectionCloseCallback): void;<br>差异内容：on(type: 'close', callback: ClientConnectionCloseCallback): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：off(type: 'error', callback?: ErrorCallback): void;<br>差异内容：off(type: 'error', callback?: ErrorCallback): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：off(type: 'connect', callback?: Callback\<WebSocketConnection>): void;<br>差异内容：off(type: 'connect', callback?: Callback\<WebSocketConnection>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：off(type: 'close', callback?: ClientConnectionCloseCallback): void;<br>差异内容：off(type: 'close', callback?: ClientConnectionCloseCallback): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：WebSocketServer；<br>API声明：off(type: 'messageReceive', callback?: Callback\<WebSocketMessage>): void;<br>差异内容：off(type: 'messageReceive', callback?: Callback\<WebSocketMessage>): void;|api/@ohos.net.webSocket.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export function isCleartextPermitted(): boolean;<br>差异内容：export function isCleartextPermitted(): boolean;|api/@ohos.net.networkSecurity.d.ts|
|新增API|NA|类名：networkSecurity；<br>API声明：export function isCleartextPermittedByHostName(hostName: string): boolean;<br>差异内容：export function isCleartextPermittedByHostName(hostName: string): boolean;|api/@ohos.net.networkSecurity.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.eap.d.ts<br>差异内容：NetworkKit|api/@ohos.net.eap.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.net.netFirewall.d.ts<br>差异内容：NetworkKit|api/@ohos.net.netFirewall.d.ts|
|API从不支持元服务到支持元服务|类名：connection；<br>API声明：function addCustomDnsRule(host: string, ip: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：connection；<br>API声明：function addCustomDnsRule(host: string, ip: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：connection；<br>API声明：function addCustomDnsRule(host: string, ip: Array\<string>): Promise\<void>;<br>差异内容：NA|类名：connection；<br>API声明：function addCustomDnsRule(host: string, ip: Array\<string>): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：connection；<br>API声明：function removeCustomDnsRule(host: string, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：connection；<br>API声明：function removeCustomDnsRule(host: string, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：connection；<br>API声明：function removeCustomDnsRule(host: string): Promise\<void>;<br>差异内容：NA|类名：connection；<br>API声明：function removeCustomDnsRule(host: string): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：NetHandle；<br>API声明：getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;<br>差异内容：NA|类名：NetHandle；<br>API声明：getAddressesByName(host: string, callback: AsyncCallback\<Array\<NetAddress>>): void;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：NetHandle；<br>API声明：getAddressesByName(host: string): Promise\<Array\<NetAddress>>;<br>差异内容：NA|类名：NetHandle；<br>API声明：getAddressesByName(host: string): Promise\<Array\<NetAddress>>;<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：NetBearType；<br>API声明：BEARER_BLUETOOTH = 2<br>差异内容：NA|类名：NetBearType；<br>API声明：BEARER_BLUETOOTH = 2<br>差异内容：atomicservice|api/@ohos.net.connection.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options: HttpRequestOptions, callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：NA|类名：HttpRequest；<br>API声明：requestInStream(url: string, options?: HttpRequestOptions): Promise\<number>;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：once(type: "headersReceive", callback: Callback\<Object>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：once(type: "headersReceive", callback: Callback\<Object>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: "dataReceive", callback: Callback\<ArrayBuffer>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: "dataReceive", callback?: Callback\<ArrayBuffer>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: "dataEnd", callback: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: "dataEnd", callback?: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: 'dataReceiveProgress', callback: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: 'dataReceiveProgress', callback?: Callback\<DataReceiveProgressInfo>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：on(type: 'dataSendProgress', callback: Callback\<DataSendProgressInfo>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：HttpRequest；<br>API声明：off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;<br>差异内容：NA|类名：HttpRequest；<br>API声明：off(type: 'dataSendProgress', callback?: Callback\<DataSendProgressInfo>): void;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：http；<br>API声明：export interface DataReceiveProgressInfo<br>差异内容：NA|类名：http；<br>API声明：export interface DataReceiveProgressInfo<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：DataReceiveProgressInfo；<br>API声明：receiveSize: number;<br>差异内容：NA|类名：DataReceiveProgressInfo；<br>API声明：receiveSize: number;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：DataReceiveProgressInfo；<br>API声明：totalSize: number;<br>差异内容：NA|类名：DataReceiveProgressInfo；<br>API声明：totalSize: number;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：http；<br>API声明：export interface DataSendProgressInfo<br>差异内容：NA|类名：http；<br>API声明：export interface DataSendProgressInfo<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：DataSendProgressInfo；<br>API声明：sendSize: number;<br>差异内容：NA|类名：DataSendProgressInfo；<br>API声明：sendSize: number;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：DataSendProgressInfo；<br>API声明：totalSize: number;<br>差异内容：NA|类名：DataSendProgressInfo；<br>API声明：totalSize: number;<br>差异内容：atomicservice|api/@ohos.net.http.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace statistics<br>差异内容：NA|类名：global；<br>API声明：declare namespace statistics<br>差异内容：atomicservice|api/@ohos.net.statistics.d.ts|
|API从不支持元服务到支持元服务|类名：statistics；<br>API声明：function getAllRxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：statistics；<br>API声明：function getAllRxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.net.statistics.d.ts|
|API从不支持元服务到支持元服务|类名：statistics；<br>API声明：function getAllRxBytes(): Promise\<number>;<br>差异内容：NA|类名：statistics；<br>API声明：function getAllRxBytes(): Promise\<number>;<br>差异内容：atomicservice|api/@ohos.net.statistics.d.ts|
|API从不支持元服务到支持元服务|类名：statistics；<br>API声明：function getAllTxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：statistics；<br>API声明：function getAllTxBytes(callback: AsyncCallback\<number>): void;<br>差异内容：atomicservice|api/@ohos.net.statistics.d.ts|
|API从不支持元服务到支持元服务|类名：statistics；<br>API声明：function getAllTxBytes(): Promise\<number>;<br>差异内容：NA|类名：statistics；<br>API声明：function getAllTxBytes(): Promise\<number>;<br>差异内容：atomicservice|api/@ohos.net.statistics.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：VpnConnection；<br>API声明：destroy(): Promise\<void>;<br>差异内容：destroy(): Promise\<void>;|类名：VpnConnection；<br>API声明：destroy(vpnId: string): Promise\<void>;<br>差异内容：destroy(vpnId: string): Promise\<void>;|api/@ohos.net.vpnExtension.d.ts|
