## 1. 接口描述

本接口(SetSSLVpnDomain)用于设置sslVPN域。
接口请求域名：<font style="color:red">vpc.api.qcloud.com</font> 

 

## 2. 输入参数
 
以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见<a href="/doc/api/372/4153" title="公共请求参数">公共请求参数</a>页面。其中，此接口的Action字段为SetSSLVpnDomain。

| 参数名称 | 是否必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| vpcId | 是 | Int | 私有网络ID值，可使用vpcId或unVpcId，建议使用unVpcId。可通过<a href="http://cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a>接口查询。 |
| sslVpnId | 否 | Int | 系统分配的SSLvpn网关ID，例如：vpngw-l2tlvgb9。可通过<a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2sslVPN?viewType=preview" title="DescribeSSLVpn">DescribeSSLVpn</a>接口查询。 |
| groupId | 是 | String |  域的工作组。|
| ipPool.n | 否 | Array |  sslVPN终端IP段。|
| acl.n | 否 | Array |  acl策略。|
| acl.n.proto | 是 | String | acl协议，例如tcp。|
| acl.n.action | 是 | String | ACL策略，0：允许，1：拒绝。|
| acl.n.destinationPort | 是 | String | 目的端口。|
| acl.n.sourceCidr | 是 | String | 源IP或源网段。|
| acl.n.destinationCidr | 是 | String | 目的IP或目的网段。|

 

## 3. 输出参数
 
| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 错误码, 0: 成功, 其他值: 失败|
| message | String | 错误信息|
| taskId | Int | 任务ID，操作结果可以用taskId查询，详见<a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%bb%bb%e5%8a%a1%e6%89%a7%e8%a1%8c%e7%bb%93%e6%9e%9c%e6%8e%a5%e5%8f%a3">查询任务执行结果接口</a>。 |

## 4. 错误码表
该接口没有业务错误码，公共错误码详见<a href="https://cloud.tencent.com/doc/api/245/%e7%a7%81%e6%9c%89%e7%bd%91%e7%bb%9c%e9%94%99%e8%af%af%e7%a0%81?viewType=preview" title="私有网络错误码">vpc错误码</a>

## 5. 示例
 
输入
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=SetSSLVpnDomain
&<<a href="https://cloud.tencent.com/doc/api/229/6976">公共请求参数</a>>
&vpcId=vpc-39lpv32n
&sslVpnId=vpngw-m1ue61hx
&groupId=ugrp-975r1ku4
&sslvpnPort=443
&ipPool.0=192.168.16.119-192.168.16.121

</pre>

输出
```
{
    "code": 0,
    "message": "",
    "data": {
        "taskId": 13161
    }
}

```

