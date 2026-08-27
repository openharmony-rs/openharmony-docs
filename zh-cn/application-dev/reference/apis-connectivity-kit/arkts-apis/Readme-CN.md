# ArkTS API<!--arkts-connectivitykit-->

- [@ohos.connectedTag](arkts-connectedtag.md)
  - [init](arkts-connectivity-connectedtag-init-f.md)
  - [initialize](arkts-connectivity-connectedtag-initialize-f.md)
  - [off](arkts-connectivity-connectedtag-off-f.md)
  - [on](arkts-connectivity-connectedtag-on-f.md)
  - [read](arkts-connectivity-connectedtag-read-f.md)
  - [readNdefTag](arkts-connectivity-connectedtag-readndeftag-f.md)
  - [uninit](arkts-connectivity-connectedtag-uninit-f.md)
  - [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md)
  - [write](arkts-connectivity-connectedtag-write-f.md)
  - [writeNdefTag](arkts-connectivity-connectedtag-writendeftag-f.md)
  - [NfcRfType](arkts-connectivity-connectedtag-nfcrftype-e.md)
- [@ohos.nearlink.advertising](arkts-nearlink-advertising.md)
  - [offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md)
  - [onAdvertisingStateChange](arkts-connectivity-advertising-onadvertisingstatechange-f.md)
  - [startAdvertising](arkts-connectivity-advertising-startadvertising-f.md)
  - [stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md)
  - [AdvertisingData](arkts-connectivity-advertising-advertisingdata-i.md)
  - [AdvertisingParams](arkts-connectivity-advertising-advertisingparams-i.md)
  - [AdvertisingSettings](arkts-connectivity-advertising-advertisingsettings-i.md)
  - [AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md)
  - [ManufacturerData](arkts-connectivity-advertising-manufacturerdata-i.md)
  - [ServiceData](arkts-connectivity-advertising-servicedata-i.md)
  - [AdvertisingState](arkts-connectivity-advertising-advertisingstate-e.md)
  - [TxPowerMode](arkts-connectivity-advertising-txpowermode-e.md)
- [@ohos.nearlink.cdsm](arkts-nearlink-cdsm.md)
  - [createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md)
  - [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md)
  - [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md)
  - [CdsmMemberInfo](arkts-connectivity-cdsm-cdsmmemberinfo-i.md)
  - [CdsmConnectionState](arkts-connectivity-cdsm-cdsmconnectionstate-e.md)
- [@ohos.nearlink.constant](arkts-nearlink-constant.md)
  - [AcbState](arkts-connectivity-nearlinkconstant-acbstate-e.md)
  <!--Del-->
  - [ConnectionInterval(系统接口)](arkts-connectivity-nearlinkconstant-connectioninterval-e-sys.md)<!--DelEnd-->
  - [ConnectionState](arkts-connectivity-nearlinkconstant-connectionstate-e.md)
  - [DeviceClass](arkts-connectivity-nearlinkconstant-deviceclass-e.md)
  - [PairingState](arkts-connectivity-nearlinkconstant-pairingstate-e.md)
- [@ohos.nearlink.dataTransfer](arkts-nearlink-datatransfer.md)
  - [connect](arkts-connectivity-datatransfer-connect-f.md)
  - [createPort](arkts-connectivity-datatransfer-createport-f.md)
  - [destroyPort](arkts-connectivity-datatransfer-destroyport-f.md)
  - [disconnect](arkts-connectivity-datatransfer-disconnect-f.md)
  - [getConnectionState](arkts-connectivity-datatransfer-getconnectionstate-f.md)
  - [offConnectionStateChanged](arkts-connectivity-datatransfer-offconnectionstatechanged-f.md)
  - [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md)
  - [onConnectionStateChanged](arkts-connectivity-datatransfer-onconnectionstatechanged-f.md)
  - [onReadData](arkts-connectivity-datatransfer-onreaddata-f.md)
  - [writeData](arkts-connectivity-datatransfer-writedata-f.md)
  - [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md)
  - [ConnectionResult](arkts-connectivity-datatransfer-connectionresult-i.md)
  - [ConnectionStateParams](arkts-connectivity-datatransfer-connectionstateparams-i.md)
  - [DataParams](arkts-connectivity-datatransfer-dataparams-i.md)
  - [ConnectionState](arkts-connectivity-datatransfer-connectionstate-t.md)
  - [TransferMode](arkts-connectivity-datatransfer-transfermode-e.md)
- [@ohos.nearlink.manager](arkts-nearlink-manager.md)
  <!--Del-->
  - [disable(系统接口)](arkts-connectivity-manager-disable-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [enable(系统接口)](arkts-connectivity-manager-enable-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [factoryReset(系统接口)](arkts-connectivity-manager-factoryreset-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getLocalAddress(系统接口)](arkts-connectivity-manager-getlocaladdress-f-sys.md)<!--DelEnd-->
  - [getLocalName](arkts-connectivity-manager-getlocalname-f.md)
  - [getPairedDevices](arkts-connectivity-manager-getpaireddevices-f.md)
  - [getState](arkts-connectivity-manager-getstate-f.md)
  - [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)
  - [offStateChange](arkts-connectivity-manager-offstatechange-f.md)
  - [onStateChange](arkts-connectivity-manager-onstatechange-f.md)
  <!--Del-->
  - [setConnectionMode(系统接口)](arkts-connectivity-manager-setconnectionmode-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [ConnectionMode(系统接口)](arkts-connectivity-manager-connectionmode-e-sys.md)<!--DelEnd-->
  - [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md)
- [@ohos.nearlink.remoteDevice](arkts-nearlink-remotedevice.md)
  - [createRemoteDevice](arkts-connectivity-remotedevice-createremotedevice-f.md)
  - [offAcbStateChange](arkts-connectivity-remotedevice-offacbstatechange-f.md)
  - [offConnectionStateChange](arkts-connectivity-remotedevice-offconnectionstatechange-f.md)
  <!--Del-->
  - [offPairingRequest(系统接口)](arkts-connectivity-remotedevice-offpairingrequest-f-sys.md)<!--DelEnd-->
  - [offPairingStateChange](arkts-connectivity-remotedevice-offpairingstatechange-f.md)
  - [onAcbStateChange](arkts-connectivity-remotedevice-onacbstatechange-f.md)
  - [onConnectionStateChange](arkts-connectivity-remotedevice-onconnectionstatechange-f.md)
  <!--Del-->
  - [onPairingRequest(系统接口)](arkts-connectivity-remotedevice-onpairingrequest-f-sys.md)<!--DelEnd-->
  - [onPairingStateChange](arkts-connectivity-remotedevice-onpairingstatechange-f.md)
  - [AcbStateParam](arkts-connectivity-remotedevice-acbstateparam-i.md)
  - [ConnectionStateParam](arkts-connectivity-remotedevice-connectionstateparam-i.md)
  - [DeviceInformation](arkts-connectivity-remotedevice-deviceinformation-i.md)
  <!--Del-->
  - [DeviceModel(系统接口)](arkts-connectivity-remotedevice-devicemodel-i-sys.md)<!--DelEnd-->
  - [PairingRequestParam](arkts-connectivity-remotedevice-pairingrequestparam-i.md)
  - [PairingStateParam](arkts-connectivity-remotedevice-pairingstateparam-i.md)
  - [RemoteDevice](arkts-connectivity-remotedevice-remotedevice-i.md)
  <!--Del-->
  - [RemoteDevice(系统接口)](arkts-connectivity-remotedevice-remotedevice-i-sys.md)<!--DelEnd-->
  - [AcbState](arkts-connectivity-remotedevice-acbstate-t.md)
  <!--Del-->
  - [ConnectionInterval(系统接口)](arkts-connectivity-remotedevice-connectioninterval-t-sys.md)<!--DelEnd-->
  - [ConnectionState](arkts-connectivity-remotedevice-connectionstate-t.md)
  - [DeviceClass](arkts-connectivity-remotedevice-deviceclass-t.md)
  - [PairingState](arkts-connectivity-remotedevice-pairingstate-t.md)
  - [ConnectionReason](arkts-connectivity-remotedevice-connectionreason-e.md)
  - [PairingReason](arkts-connectivity-remotedevice-pairingreason-e.md)
  - [PairingType](arkts-connectivity-remotedevice-pairingtype-e.md)
- [@ohos.nearlink.scan](arkts-nearlink-scan.md)
  - [offDeviceFound](arkts-connectivity-scan-offdevicefound-f.md)
  - [onDeviceFound](arkts-connectivity-scan-ondevicefound-f.md)
  - [startScan](arkts-connectivity-scan-startscan-f.md)
  - [stopScan](arkts-connectivity-scan-stopscan-f.md)
  - [ScanFilters](arkts-connectivity-scan-scanfilters-i.md)
  - [ScanOptions](arkts-connectivity-scan-scanoptions-i.md)
  - [ScanResults](arkts-connectivity-scan-scanresults-i.md)
  - [ScanMode](arkts-connectivity-scan-scanmode-e.md)
  <!--Del-->
  - [ScanMode(系统接口)](arkts-connectivity-scan-scanmode-e-sys.md)<!--DelEnd-->
- [@ohos.nearlink.ssap](arkts-nearlink-ssap.md)
  - [createClient](arkts-connectivity-ssap-createclient-f.md)
  - [createServer](arkts-connectivity-ssap-createserver-f.md)
  - [Client](arkts-connectivity-ssap-client-i.md)
  <!--Del-->
  - [Client(系统接口)](arkts-connectivity-ssap-client-i-sys.md)<!--DelEnd-->
  - [ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)
  <!--Del-->
  - [Event(系统接口)](arkts-connectivity-ssap-event-i-sys.md)<!--DelEnd-->
  <!--Del-->
  - [Method(系统接口)](arkts-connectivity-ssap-method-i-sys.md)<!--DelEnd-->
  - [Property](arkts-connectivity-ssap-property-i.md)
  - [PropertyDescriptor](arkts-connectivity-ssap-propertydescriptor-i.md)
  - [PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md)
  - [PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md)
  - [Server](arkts-connectivity-ssap-server-i.md)
  - [ServerResponse](arkts-connectivity-ssap-serverresponse-i.md)
  - [Service](arkts-connectivity-ssap-service-i.md)
  <!--Del-->
  - [Service(系统接口)](arkts-connectivity-ssap-service-i-sys.md)<!--DelEnd-->
  - [ConnectionState](arkts-connectivity-ssap-connectionstate-t.md)
  - [Operation](arkts-connectivity-ssap-operation-e.md)
  - [PropertyDescriptorType](arkts-connectivity-ssap-propertydescriptortype-e.md)
  - [PropertyWriteType](arkts-connectivity-ssap-propertywritetype-e.md)
- [@ohos.nfc.cardEmulation](arkts-nfc-cardemulation.md)
  <!--Del-->
  - [getPaymentServices(系统接口)](arkts-connectivity-cardemulation-getpaymentservices-f-sys.md)<!--DelEnd-->
  - [hasHceCapability](arkts-connectivity-cardemulation-hashcecapability-f.md)
  - [isDefaultService](arkts-connectivity-cardemulation-isdefaultservice-f.md)
  - [isSupported](arkts-connectivity-cardemulation-issupported-f.md)
  - [HceService](arkts-connectivity-cardemulation-hceservice-c.md)
  - [CardType](arkts-connectivity-cardemulation-cardtype-e.md)
  - [FeatureType](arkts-connectivity-cardemulation-featuretype-e.md)
- [@ohos.nfc.controller](arkts-nfc-controller.md)
  - [closeNfc](arkts-connectivity-nfccontroller-closenfc-f.md)
  - [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md)
  - [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md)
  - [getNfcState](arkts-connectivity-nfccontroller-getnfcstate-f.md)
  - [isNfcAvailable](arkts-connectivity-nfccontroller-isnfcavailable-f.md)
  - [isNfcOpen](arkts-connectivity-nfccontroller-isnfcopen-f.md)
  - [isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md)
  - [off](arkts-connectivity-nfccontroller-off-f.md)
  - [on](arkts-connectivity-nfccontroller-on-f.md)
  - [openNfc](arkts-connectivity-nfccontroller-opennfc-f.md)
  - [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md)
- [@ohos.nfc.tag](arkts-nfc-tag.md)
  - [tag](arkts-connectivity-tag-n.md)
    - [ndef](arkts-connectivity-tag-ndef-n.md)
      - [createNdefMessage](arkts-connectivity-ndef-createndefmessage-f.md)
      - [makeApplicationRecord](arkts-connectivity-ndef-makeapplicationrecord-f.md)
      - [makeExternalRecord](arkts-connectivity-ndef-makeexternalrecord-f.md)
      - [makeMimeRecord](arkts-connectivity-ndef-makemimerecord-f.md)
      - [makeTextRecord](arkts-connectivity-ndef-maketextrecord-f.md)
      - [makeUriRecord](arkts-connectivity-ndef-makeurirecord-f.md)
      - [messageToBytes](arkts-connectivity-ndef-messagetobytes-f.md)
    - [getBarcodeTag](arkts-connectivity-tag-getbarcodetag-f.md)
    - [getIsoDep](arkts-connectivity-tag-getisodep-f.md)
    - [getMifareClassic](arkts-connectivity-tag-getmifareclassic-f.md)
    - [getMifareUltralight](arkts-connectivity-tag-getmifareultralight-f.md)
    - [getNdef](arkts-connectivity-tag-getndef-f.md)
    - [getNdefFormatable](arkts-connectivity-tag-getndefformatable-f.md)
    - [getNfcA](arkts-connectivity-tag-getnfca-f.md)
    - [getNfcATag](arkts-connectivity-tag-getnfcatag-f.md)
    - [getNfcB](arkts-connectivity-tag-getnfcb-f.md)
    - [getNfcBTag](arkts-connectivity-tag-getnfcbtag-f.md)
    - [getNfcF](arkts-connectivity-tag-getnfcf-f.md)
    - [getNfcFTag](arkts-connectivity-tag-getnfcftag-f.md)
    - [getNfcV](arkts-connectivity-tag-getnfcv-f.md)
    - [getNfcVTag](arkts-connectivity-tag-getnfcvtag-f.md)
    - [getTagInfo](arkts-connectivity-tag-gettaginfo-f.md)
    - [off](arkts-connectivity-tag-off-f.md)
    - [on](arkts-connectivity-tag-on-f.md)
    - [registerForegroundDispatch](arkts-connectivity-tag-registerforegrounddispatch-f.md)
    - [unregisterForegroundDispatch](arkts-connectivity-tag-unregisterforegrounddispatch-f.md)
    - [NdefRecord](arkts-connectivity-tag-ndefrecord-i.md)
    - [TagInfo](arkts-connectivity-tag-taginfo-i.md)
    <!--Del-->
    - [TagInfo(系统接口)](arkts-connectivity-tag-taginfo-i-sys.md)<!--DelEnd-->
    - [BarcodeTag](arkts-connectivity-tag-barcodetag-t.md)
    - [IsoDepTag](arkts-connectivity-tag-isodeptag-t.md)
    - [MifareClassicTag](arkts-connectivity-tag-mifareclassictag-t.md)
    - [MifareUltralightTag](arkts-connectivity-tag-mifareultralighttag-t.md)
    - [NdefFormatableTag](arkts-connectivity-tag-ndefformatabletag-t.md)
    - [NdefMessage](arkts-connectivity-tag-ndefmessage-t.md)
    - [NdefTag](arkts-connectivity-tag-ndeftag-t.md)
    - [NfcATag](arkts-connectivity-tag-nfcatag-t.md)
    - [NfcBTag](arkts-connectivity-tag-nfcbtag-t.md)
    - [NfcFTag](arkts-connectivity-tag-nfcftag-t.md)
    - [NfcVTag](arkts-connectivity-tag-nfcvtag-t.md)
    - [TagSession](arkts-connectivity-tag-tagsession-t.md)
    - [MifareClassicSize](arkts-connectivity-tag-mifareclassicsize-e.md)
    - [MifareClassicType](arkts-connectivity-tag-mifareclassictype-e.md)
    - [MifareUltralightType](arkts-connectivity-tag-mifareultralighttype-e.md)
    - [NfcForumType](arkts-connectivity-tag-nfcforumtype-e.md)
    - [TnfType](arkts-connectivity-tag-tnftype-e.md)
    - [常量](arkts-connectivity-tag-con.md)
- [@ohos.secureElement](arkts-secureelement.md)
  - [createService](arkts-connectivity-omapi-createservice-f.md)
  - [newSEService](arkts-connectivity-omapi-newseservice-f.md)
  - [off](arkts-connectivity-omapi-off-f.md)
  - [on](arkts-connectivity-omapi-on-f.md)
  - [Channel](arkts-connectivity-omapi-channel-i.md)
  - [Reader](arkts-connectivity-omapi-reader-i.md)
  - [SEService](arkts-connectivity-omapi-seservice-i.md)
  - [Session](arkts-connectivity-omapi-session-i.md)
  - [ServiceState](arkts-connectivity-omapi-servicestate-e.md)
- [@ohos.wifi](arkts-wifi.md)
  <!--Del-->
  - [addDeviceConfig(系统接口)](arkts-connectivity-wifi-adddeviceconfig-f-sys.md)<!--DelEnd-->
  - [addUntrustedConfig](arkts-connectivity-wifi-adduntrustedconfig-f.md)
  <!--Del-->
  - [connectToDevice(系统接口)](arkts-connectivity-wifi-connecttodevice-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [connectToNetwork(系统接口)](arkts-connectivity-wifi-connecttonetwork-f-sys.md)<!--DelEnd-->
  - [createGroup](arkts-connectivity-wifi-creategroup-f.md)
  <!--Del-->
  - [deletePersistentGroup(系统接口)](arkts-connectivity-wifi-deletepersistentgroup-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [disableHotspot(系统接口)](arkts-connectivity-wifi-disablehotspot-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [disableNetwork(系统接口)](arkts-connectivity-wifi-disablenetwork-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [disableWifi(系统接口)](arkts-connectivity-wifi-disablewifi-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [disconnect(系统接口)](arkts-connectivity-wifi-disconnect-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [enableHotspot(系统接口)](arkts-connectivity-wifi-enablehotspot-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [enableWifi(系统接口)](arkts-connectivity-wifi-enablewifi-f-sys.md)<!--DelEnd-->
  - [getCountryCode](arkts-connectivity-wifi-getcountrycode-f.md)
  - [getCurrentGroup](arkts-connectivity-wifi-getcurrentgroup-f.md)
  <!--Del-->
  - [getDeviceConfigs(系统接口)](arkts-connectivity-wifi-getdeviceconfigs-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getDeviceMacAddress(系统接口)](arkts-connectivity-wifi-getdevicemacaddress-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getHotspotConfig(系统接口)](arkts-connectivity-wifi-gethotspotconfig-f-sys.md)<!--DelEnd-->
  - [getIpInfo](arkts-connectivity-wifi-getipinfo-f.md)
  - [getLinkedInfo](arkts-connectivity-wifi-getlinkedinfo-f.md)
  - [getP2pLinkedInfo](arkts-connectivity-wifi-getp2plinkedinfo-f.md)
  - [getP2pPeerDevices](arkts-connectivity-wifi-getp2ppeerdevices-f.md)
  - [getScanInfos](arkts-connectivity-wifi-getscaninfos-f.md)
  - [getSignalLevel](arkts-connectivity-wifi-getsignallevel-f.md)
  <!--Del-->
  - [getStations(系统接口)](arkts-connectivity-wifi-getstations-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getSupportedFeatures(系统接口)](arkts-connectivity-wifi-getsupportedfeatures-f-sys.md)<!--DelEnd-->
  - [isConnected](arkts-connectivity-wifi-isconnected-f.md)
  - [isFeatureSupported](arkts-connectivity-wifi-isfeaturesupported-f.md)
  <!--Del-->
  - [isHotspotActive(系统接口)](arkts-connectivity-wifi-ishotspotactive-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [isHotspotDualBandSupported(系统接口)](arkts-connectivity-wifi-ishotspotdualbandsupported-f-sys.md)<!--DelEnd-->
  - [isWifiActive](arkts-connectivity-wifi-iswifiactive-f.md)
  - [off](arkts-connectivity-wifi-off-f.md)
  <!--Del-->
  - [off(系统接口)](arkts-connectivity-wifi-off-f-sys.md)<!--DelEnd-->
  - [on](arkts-connectivity-wifi-on-f.md)
  <!--Del-->
  - [on(系统接口)](arkts-connectivity-wifi-on-f-sys.md)<!--DelEnd-->
  - [p2pCancelConnect](arkts-connectivity-wifi-p2pcancelconnect-f.md)
  - [p2pConnect](arkts-connectivity-wifi-p2pconnect-f.md)
  <!--Del-->
  - [reassociate(系统接口)](arkts-connectivity-wifi-reassociate-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [reconnect(系统接口)](arkts-connectivity-wifi-reconnect-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [removeAllNetwork(系统接口)](arkts-connectivity-wifi-removeallnetwork-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [removeDevice(系统接口)](arkts-connectivity-wifi-removedevice-f-sys.md)<!--DelEnd-->
  - [removeGroup](arkts-connectivity-wifi-removegroup-f.md)
  - [removeUntrustedConfig](arkts-connectivity-wifi-removeuntrustedconfig-f.md)
  - [scan](arkts-connectivity-wifi-scan-f.md)
  <!--Del-->
  - [setDeviceName(系统接口)](arkts-connectivity-wifi-setdevicename-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [setHotspotConfig(系统接口)](arkts-connectivity-wifi-sethotspotconfig-f-sys.md)<!--DelEnd-->
  - [startDiscoverDevices](arkts-connectivity-wifi-startdiscoverdevices-f.md)
  - [stopDiscoverDevices](arkts-connectivity-wifi-stopdiscoverdevices-f.md)
  <!--Del-->
  - [updateNetwork(系统接口)](arkts-connectivity-wifi-updatenetwork-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [HotspotConfig(系统接口)](arkts-connectivity-wifi-hotspotconfig-i-sys.md)<!--DelEnd-->
  <!--Del-->
  - [IpConfig(系统接口)](arkts-connectivity-wifi-ipconfig-i-sys.md)<!--DelEnd-->
  - [IpInfo](arkts-connectivity-wifi-ipinfo-i.md)
  <!--Del-->
  - [StationInfo(系统接口)](arkts-connectivity-wifi-stationinfo-i-sys.md)<!--DelEnd-->
  - [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md)
  <!--Del-->
  - [WifiDeviceConfig(系统接口)](arkts-connectivity-wifi-wifideviceconfig-i-sys.md)<!--DelEnd-->
  - [WifiLinkedInfo](arkts-connectivity-wifi-wifilinkedinfo-i.md)
  <!--Del-->
  - [WifiLinkedInfo(系统接口)](arkts-connectivity-wifi-wifilinkedinfo-i-sys.md)<!--DelEnd-->
  - [WifiP2PConfig](arkts-connectivity-wifi-wifip2pconfig-i.md)
  - [WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)
  - [WifiP2pGroupInfo](arkts-connectivity-wifi-wifip2pgroupinfo-i.md)
  - [WifiP2pLinkedInfo](arkts-connectivity-wifi-wifip2plinkedinfo-i.md)
  - [WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md)
  - [ConnState](arkts-connectivity-wifi-connstate-e.md)
  - [GroupOwnerBand](arkts-connectivity-wifi-groupownerband-e.md)
  <!--Del-->
  - [IpType(系统接口)](arkts-connectivity-wifi-iptype-e-sys.md)<!--DelEnd-->
  - [P2pConnectState](arkts-connectivity-wifi-p2pconnectstate-e.md)
  - [P2pDeviceStatus](arkts-connectivity-wifi-p2pdevicestatus-e.md)
  <!--Del-->
  - [SuppState(系统接口)](arkts-connectivity-wifi-suppstate-e-sys.md)<!--DelEnd-->
  - [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)
- [@ohos.wifiext](arkts-wifiext.md)
  - [disableHotspot](arkts-connectivity-wifiext-disablehotspot-f.md)
  - [enableHotspot](arkts-connectivity-wifiext-enablehotspot-f.md)
  - [getPowerModel](arkts-connectivity-wifiext-getpowermodel-f.md)
  - [getSupportedPowerModel](arkts-connectivity-wifiext-getsupportedpowermodel-f.md)
  - [setPowerModel](arkts-connectivity-wifiext-setpowermodel-f.md)
  - [PowerModel](arkts-connectivity-wifiext-powermodel-e.md)
- [@ohos.wifiManager](arkts-wifimanager.md)
  - [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md)
  - [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)
  <!--Del-->
  - [addHotspotBlockList(系统接口)](arkts-connectivity-wifimanager-addhotspotblocklist-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [allowAutoConnect(系统接口)](arkts-connectivity-wifimanager-allowautoconnect-f-sys.md)<!--DelEnd-->
  - [connectToCandidateConfig](arkts-connectivity-wifimanager-connecttocandidateconfig-f.md)
  - [connectToCandidateConfigWithUserAction](arkts-connectivity-wifimanager-connecttocandidateconfigwithuseraction-f.md)
  <!--Del-->
  - [connectToDevice(系统接口)](arkts-connectivity-wifimanager-connecttodevice-f-sys.md)<!--DelEnd-->
  - [connectToNetwork](arkts-connectivity-wifimanager-connecttonetwork-f.md)
  - [createGroup](arkts-connectivity-wifimanager-creategroup-f.md)
  <!--Del-->
  - [deletePersistentGroup(系统接口)](arkts-connectivity-wifimanager-deletepersistentgroup-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [delHotspotBlockList(系统接口)](arkts-connectivity-wifimanager-delhotspotblocklist-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [disableHotspot(系统接口)](arkts-connectivity-wifimanager-disablehotspot-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [disableNetwork(系统接口)](arkts-connectivity-wifimanager-disablenetwork-f-sys.md)<!--DelEnd-->
  - [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md)
  - [disconnect](arkts-connectivity-wifimanager-disconnect-f.md)
  <!--Del-->
  - [enableHiLinkHandshake(系统接口)](arkts-connectivity-wifimanager-enablehilinkhandshake-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [enableHotspot(系统接口)](arkts-connectivity-wifimanager-enablehotspot-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [enableSemiWifi(系统接口)](arkts-connectivity-wifimanager-enablesemiwifi-f-sys.md)<!--DelEnd-->
  - [enableWifi](arkts-connectivity-wifimanager-enablewifi-f.md)
  <!--Del-->
  - [factoryReset(系统接口)](arkts-connectivity-wifimanager-factoryreset-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [get5GChannelList(系统接口)](arkts-connectivity-wifimanager-get5gchannellist-f-sys.md)<!--DelEnd-->
  - [getCandidateConfigs](arkts-connectivity-wifimanager-getcandidateconfigs-f.md)
  - [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md)
  - [getCurrentGroup](arkts-connectivity-wifimanager-getcurrentgroup-f.md)
  <!--Del-->
  - [getDeviceConfig(系统接口)](arkts-connectivity-wifimanager-getdeviceconfig-f-sys.md)<!--DelEnd-->
  - [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md)
  - [getDeviceMacAddress](arkts-connectivity-wifimanager-getdevicemacaddress-f.md)
  <!--Del-->
  - [getDisconnectedReason(系统接口)](arkts-connectivity-wifimanager-getdisconnectedreason-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getHotspotBlockList(系统接口)](arkts-connectivity-wifimanager-gethotspotblocklist-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getHotspotConfig(系统接口)](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md)<!--DelEnd-->
  - [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md)
  - [getIpv6Info](arkts-connectivity-wifimanager-getipv6info-f.md)
  - [getLinkedInfo](arkts-connectivity-wifimanager-getlinkedinfo-f.md)
  - [getLinkedInfoSync](arkts-connectivity-wifimanager-getlinkedinfosync-f.md)
  - [getMultiLinkedInfo](arkts-connectivity-wifimanager-getmultilinkedinfo-f.md)
  <!--Del-->
  - [getP2pGroups(系统接口)](arkts-connectivity-wifimanager-getp2pgroups-f-sys.md)<!--DelEnd-->
  - [getP2pLinkedInfo](arkts-connectivity-wifimanager-getp2plinkedinfo-f.md)
  - [getP2pLocalDevice](arkts-connectivity-wifimanager-getp2plocaldevice-f.md)
  - [getP2pPeerDevices](arkts-connectivity-wifimanager-getp2ppeerdevices-f.md)
  <!--Del-->
  - [getScanAlwaysAllowed(系统接口)](arkts-connectivity-wifimanager-getscanalwaysallowed-f-sys.md)<!--DelEnd-->
  - [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)
  - [getScanResults](arkts-connectivity-wifimanager-getscanresults-f.md)
  - [getScanResultsSync](arkts-connectivity-wifimanager-getscanresultssync-f.md)
  - [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md)
  <!--Del-->
  - [getStations(系统接口)](arkts-connectivity-wifimanager-getstations-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getSupportedFeatures(系统接口)](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getWifiCapability(系统接口)](arkts-connectivity-wifimanager-getwificapability-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [getWifiDetailState(系统接口)](arkts-connectivity-wifimanager-getwifidetailstate-f-sys.md)<!--DelEnd-->
  - [isBandTypeSupported](arkts-connectivity-wifimanager-isbandtypesupported-f.md)
  - [isConnected](arkts-connectivity-wifimanager-isconnected-f.md)
  - [isFeatureSupported](arkts-connectivity-wifimanager-isfeaturesupported-f.md)
  <!--Del-->
  - [isHotspotActive(系统接口)](arkts-connectivity-wifimanager-ishotspotactive-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [isHotspotDualBandSupported(系统接口)](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md)<!--DelEnd-->
  - [isMeteredHotspot](arkts-connectivity-wifimanager-ismeteredhotspot-f.md)
  <!--Del-->
  - [isOpenSoftApAllowed(系统接口)](arkts-connectivity-wifimanager-isopensoftapallowed-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [isRandomMacDisabled(系统接口)](arkts-connectivity-wifimanager-israndommacdisabled-f-sys.md)<!--DelEnd-->
  - [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md)
  - [isWlanSupported](arkts-connectivity-wifimanager-iswlansupported-f.md)
  - [off](arkts-connectivity-wifimanager-off-f.md)
  <!--Del-->
  - [off(系统接口)](arkts-connectivity-wifimanager-off-f-sys.md)<!--DelEnd-->
  - [on](arkts-connectivity-wifimanager-on-f.md)
  <!--Del-->
  - [on(系统接口)](arkts-connectivity-wifimanager-on-f-sys.md)<!--DelEnd-->
  - [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md)
  - [p2pConnect](arkts-connectivity-wifimanager-p2pconnect-f.md)
  <!--Del-->
  - [reassociate(系统接口)](arkts-connectivity-wifimanager-reassociate-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [reconnect(系统接口)](arkts-connectivity-wifimanager-reconnect-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [removeAllNetwork(系统接口)](arkts-connectivity-wifimanager-removeallnetwork-f-sys.md)<!--DelEnd-->
  - [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md)
  - [removeDevice](arkts-connectivity-wifimanager-removedevice-f.md)
  - [removeGroup](arkts-connectivity-wifimanager-removegroup-f.md)
  - [scan](arkts-connectivity-wifimanager-scan-f.md)
  <!--Del-->
  - [setDeviceName(系统接口)](arkts-connectivity-wifimanager-setdevicename-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [setHotspotConfig(系统接口)](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [setScanAlwaysAllowed(系统接口)](arkts-connectivity-wifimanager-setscanalwaysallowed-f-sys.md)<!--DelEnd-->
  <!--Del-->
  - [setWifiCapability(系统接口)](arkts-connectivity-wifimanager-setwificapability-f-sys.md)<!--DelEnd-->
  - [startDiscoverDevices](arkts-connectivity-wifimanager-startdiscoverdevices-f.md)
  <!--Del-->
  - [startPortalCertification(系统接口)](arkts-connectivity-wifimanager-startportalcertification-f-sys.md)<!--DelEnd-->
  - [startScan](arkts-connectivity-wifimanager-startscan-f.md)
  <!--Del-->
  - [startWifiDetection(系统接口)](arkts-connectivity-wifimanager-startwifidetection-f-sys.md)<!--DelEnd-->
  - [stopDiscoverDevices](arkts-connectivity-wifimanager-stopdiscoverdevices-f.md)
  <!--Del-->
  - [updateNetwork(系统接口)](arkts-connectivity-wifimanager-updatenetwork-f-sys.md)<!--DelEnd-->
  - [ConnectSettings](arkts-connectivity-wifimanager-connectsettings-i.md)
  <!--Del-->
  - [HotspotConfig(系统接口)](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md)<!--DelEnd-->
  <!--Del-->
  - [IpConfig(系统接口)](arkts-connectivity-wifimanager-ipconfig-i-sys.md)<!--DelEnd-->
  - [IpInfo](arkts-connectivity-wifimanager-ipinfo-i.md)
  <!--Del-->
  - [Ipv6Config(系统接口)](arkts-connectivity-wifimanager-ipv6config-i-sys.md)<!--DelEnd-->
  - [Ipv6Info](arkts-connectivity-wifimanager-ipv6info-i.md)
  <!--Del-->
  - [StationInfo(系统接口)](arkts-connectivity-wifimanager-stationinfo-i-sys.md)<!--DelEnd-->
  - [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md)
  <!--Del-->
  - [WifiDeviceConfig(系统接口)](arkts-connectivity-wifimanager-wifideviceconfig-i-sys.md)<!--DelEnd-->
  - [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md)
  - [WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md)
  - [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)
  <!--Del-->
  - [WifiLinkedInfo(系统接口)](arkts-connectivity-wifimanager-wifilinkedinfo-i-sys.md)<!--DelEnd-->
  - [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md)
  - [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)
  - [WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md)
  - [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md)
  <!--Del-->
  - [WifiProxyConfig(系统接口)](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md)<!--DelEnd-->
  - [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md)
  <!--Del-->
  - [WifiScanInfo(系统接口)](arkts-connectivity-wifimanager-wifiscaninfo-i-sys.md)<!--DelEnd-->
  - [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md)
  - [ConnState](arkts-connectivity-wifimanager-connstate-e.md)
  - [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)
  <!--Del-->
  - [DisconnectedReason(系统接口)](arkts-connectivity-wifimanager-disconnectedreason-e-sys.md)<!--DelEnd-->
  - [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md)
  - [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md)
  <!--Del-->
  - [IpType(系统接口)](arkts-connectivity-wifimanager-iptype-e-sys.md)<!--DelEnd-->
  - [P2pConnectState](arkts-connectivity-wifimanager-p2pconnectstate-e.md)
  - [P2pDeviceStatus](arkts-connectivity-wifimanager-p2pdevicestatus-e.md)
  - [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md)
  <!--Del-->
  - [ProxyMethod(系统接口)](arkts-connectivity-wifimanager-proxymethod-e-sys.md)<!--DelEnd-->
  <!--Del-->
  - [SuppState(系统接口)](arkts-connectivity-wifimanager-suppstate-e-sys.md)<!--DelEnd-->
  - [WapiPskType](arkts-connectivity-wifimanager-wapipsktype-e.md)
  - [WifiBandType](arkts-connectivity-wifimanager-wifibandtype-e.md)
  - [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md)
  - [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)
  - [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md)
  <!--Del-->
  - [WifiDetailState(系统接口)](arkts-connectivity-wifimanager-wifidetailstate-e-sys.md)<!--DelEnd-->
  - [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md)
  - [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)
  - [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md)
- [@ohos.wifiManagerExt](arkts-wifimanagerext.md)
  - [disableHotspot](arkts-connectivity-wifimanagerext-disablehotspot-f.md)
  - [enableHotspot](arkts-connectivity-wifimanagerext-enablehotspot-f.md)
  - [getPowerMode](arkts-connectivity-wifimanagerext-getpowermode-f.md)
  - [getSupportedPowerMode](arkts-connectivity-wifimanagerext-getsupportedpowermode-f.md)
  - [setPowerMode](arkts-connectivity-wifimanagerext-setpowermode-f.md)
  - [PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md)
- tag<!--arkts-connectivitykit-tag-->
  - [nfctech](arkts-nfctech.md)
    - [BarcodeTag](arkts-connectivity-nfctech-barcodetag-i.md)
    - [IsoDepTag](arkts-connectivity-nfctech-isodeptag-i.md)
    - [MifareClassicTag](arkts-connectivity-nfctech-mifareclassictag-i.md)
    - [MifareUltralightTag](arkts-connectivity-nfctech-mifareultralighttag-i.md)
    - [NdefFormatableTag](arkts-connectivity-nfctech-ndefformatabletag-i.md)
    - [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md)
    - [NdefTag](arkts-connectivity-nfctech-ndeftag-i.md)
    - [NfcATag](arkts-connectivity-nfctech-nfcatag-i.md)
    - [NfcBTag](arkts-connectivity-nfctech-nfcbtag-i.md)
    - [NfcFTag](arkts-connectivity-nfctech-nfcftag-i.md)
    - [NfcVTag](arkts-connectivity-nfctech-nfcvtag-i.md)
  - [tagSession](arkts-tagsession.md)
    - [TagSession](arkts-connectivity-tagsession-tagsession-i.md)