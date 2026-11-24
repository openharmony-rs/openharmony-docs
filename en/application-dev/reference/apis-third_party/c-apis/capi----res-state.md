# __res_state

## Overview

<!--Device-struct __res_state {...}--><!--Device-struct __res_state {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int retrans | <!--Device-int retrans--><!--Device-int retrans-End--> |
| int retry | <!--Device-int retry--><!--Device-int retry-End--> |
| unsigned long options | <!--Device-unsigned long options--><!--Device-unsigned long options-End--> |
| int nscount | <!--Device-int nscount--><!--Device-int nscount-End--> |
| struct sockaddr_in nsaddr_list[MAXNS] | <!--Device-struct sockaddr_in nsaddr_list[MAXNS]--><!--Device-struct sockaddr_in nsaddr_list[MAXNS]-End--> |
| # define nsaddr	nsaddr_list[0]
	unsigned short id | <!--Device-# define nsaddr nsaddr_list[0] unsigned short id--><!--Device-# define nsaddr nsaddr_list[0] unsigned short id-End--> |
| char *dnsrch[MAXDNSRCH+1] | <!--Device-char *dnsrch[MAXDNSRCH+1]--><!--Device-char *dnsrch[MAXDNSRCH+1]-End--> |
| char defdname[256] | <!--Device-char defdname[256]--><!--Device-char defdname[256]-End--> |
| unsigned long pfcode | <!--Device-unsigned long pfcode--><!--Device-unsigned long pfcode-End--> |
| unsigned ndots:4 | <!--Device-unsigned ndots:4--><!--Device-unsigned ndots:4-End--> |
| unsigned nsort:4 | <!--Device-unsigned nsort:4--><!--Device-unsigned nsort:4-End--> |
| unsigned ipv6_unavail:1 | <!--Device-unsigned ipv6_unavail:1--><!--Device-unsigned ipv6_unavail:1-End--> |
| unsigned unused:23 | <!--Device-unsigned unused:23--><!--Device-unsigned unused:23-End--> |
| sort_list.addr | <!--Device-sort_list.addr--><!--Device-sort_list.addr-End--> |
| sort_list.mask | <!--Device-sort_list.mask--><!--Device-sort_list.mask-End--> |
| void *qhook | <!--Device-void *qhook--><!--Device-void *qhook-End--> |
| void *rhook | <!--Device-void *rhook--><!--Device-void *rhook-End--> |
| int res_h_errno | <!--Device-int res_h_errno--><!--Device-int res_h_errno-End--> |
| int _vcsock | <!--Device-int _vcsock--><!--Device-int _vcsock-End--> |
| unsigned _flags | <!--Device-unsigned _flags--><!--Device-unsigned _flags-End--> |
| _u.pad | <!--Device-_u.pad--><!--Device-_u.pad-End--> |
| _u._ext.uint16_t		nscount | <!--Device-_u._ext.uint16_t nscount--><!--Device-_u._ext.uint16_t nscount-End--> |
| _u._ext.uint16_t		nsmap | <!--Device-_u._ext.uint16_t nsmap--><!--Device-_u._ext.uint16_t nsmap-End--> |
| _u._ext.int			nssocks | <!--Device-_u._ext.int nssocks--><!--Device-_u._ext.int nssocks-End--> |
| _u._ext.uint16_t		nscount6 | <!--Device-_u._ext.uint16_t nscount6--><!--Device-_u._ext.uint16_t nscount6-End--> |
| _u._ext.uint16_t		nsinit | <!--Device-_u._ext.uint16_t nsinit--><!--Device-_u._ext.uint16_t nsinit-End--> |
| _u._ext.sockaddr_in6	*nsaddrs | <!--Device-_u._ext.sockaddr_in6 *nsaddrs--><!--Device-_u._ext.sockaddr_in6 *nsaddrs-End--> |
| _u._ext.int		_initstamp | <!--Device-_u._ext.int _initstamp--><!--Device-_u._ext.int _initstamp-End--> |


