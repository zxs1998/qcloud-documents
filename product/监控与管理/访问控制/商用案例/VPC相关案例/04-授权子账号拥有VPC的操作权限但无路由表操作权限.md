
企业帐号CompanyExample（ownerUin为12345678）下有一个子账号Developer，该子账号需要拥有对企业帐号CompanyExample的VPC服务的读写VPC及其相关资源的权限，但是不允许对路由表进行相关操作。

步骤1：通过策略语法方式创建以下策略
```
{
    "version": "2.0",
    "statement": [
        {
            "action": [
                "vpc:*"
            ],
            "resource": "*",
            "effect": "allow"
        },
        {
            "action": [
                "vpc:AssociateRouteTable",
                "vpc:CreateRoute",
                "vpc:CreateRouteTable",
                "vpc:DeleteRoute",
                "vpc:DeleteRouteTable",
                "vpc:ModifyRouteTableAttribute"
            ],
            "resource": "*",
            "effect": "deny"
        }
    ]
}
```
步骤2：将该策略授权给子账号。授权方式请参考[授权管理](https://cloud.tencent.com/document/product/378/8961)。
