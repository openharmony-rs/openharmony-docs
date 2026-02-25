# Firewall Error Codes


<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 29400000 User ID Does Not Exist

**Error Message**

The specified user does not exist.

**Description**

The specified system user ID does not exist.

**Possible causes**

The entered user ID does not exist.

**Solution**

Check whether the user ID exists in the system.

## 29400001 Number of Firewall Rules Exceeds the Maximum

**Error Message**

The number of firewall rules exceeds the maximum.

**Description**

The number of firewall rules exceeds the maximum.

**Possible causes**

1. The number of firewall rules of a single **userid** exceeds 1000.

2. The number of firewall rules of all **userid** exceeds 2000.

**Solution**

Delete useless firewall rules and add new firewall rules.

## 29400002 Number of IP Address Rules in the Firewall Rule Exceeds the Maximum

**Error Message**

The number of IP address rules in the firewall rule exceeds the maximum.

**Description**

The number of IP address rules in the IP firewall rule exceeds the maximum.

**Possible causes**

The number of **NetFirewallIpParams** in the local IP address or remote IP address of the IP rule to be added or updated is greater than 10.

**Solution**

Check whether the number of **NetFirewallIpParams** in the IP rule to be added is greater than 10.

## 29400003 Number of Port Rules in the Firewall Rule Exceeds the Maximum

**Error Message**

The number of port rules in the firewall rule exceeds the maximum.

**Description**

The number of port rules in the IP firewall rule exceeds the maximum.

**Possible causes**

The number of **NetFirewallPortParams** in the local or remote port of the IP rule to be added or updated exceeds 10.

**Solution**

Check whether the number of **NetFirewallPortParams** in the IP rule to be added exceeds 10.

## 29400004 Number of Domain Name Rules in the Firewall Rule Exceeds the Maximum

**Error Message**

The number of domain rules in the firewall rule exceeds the maximum.

**Description**

The number of domain name rules in the firewall rule of the **domain** type exceeds the maximum.

**Possible causes**

The number of **NetFirewallDomainParams** in the added or updated domain rule is greater than 100.

**Solution**

Check whether the number of **NetFirewallDomainParams** in the added domain rule is greater than 100.

## 29400005 Number of Fuzzy Domain Name Rules Exceeds the Maximum

**Error Message**

The number of domain rules exceeds the maximum.

**Description**

The number of fuzzy domain name rules in the firewall rule of the **domain** type exceeds the maximum.

**Possible causes**

The number of added/updated fuzzy domain name rules of all user IDs is greater than 100.

**Solution**

Check whether the number of fuzzy domain name rules of all user IDs is greater than 100.

## 29400006 Specified Rule Does Not Exist

**Error Message**

The specified rule does not exist.

**Description**

The specified rule does not exist.

**Possible causes**

The specified rule does not exist when the rule is queried, updated, or deleted.

**Solution**

Check whether the input parameter **ruleid** exists.

## 29400007 DNS Rule Duplication

**Error Message**

The dns rule is duplication.

**Description**

The DNS rule is duplicate.

**Possible causes**

The DNS rule to be added or updated is duplicate.

**Solution**

Check whether the DNS rule to be added or updated already exists.
