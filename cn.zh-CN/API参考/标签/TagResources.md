# TagResources {#doc_api_1057764 .reference}

为指定的ECS资源列表统一创建并绑定标签。

## 接口说明 {#description .section}

绑定标签前，阿里云会校验资源已有标签数量。超过限制值后返回报错信息。更多详情，请参见[使用限制](~~25412~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=TagResources)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|资源所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|ResourceId.N|RepeatList|是|i-bp1j6qtvdm8w0z1o0XXX|资源ID，N的取值范围为1~50。

 |
|ResourceType|String|是|ECS\_INSTANCE\("ALIYUN::ECS::INSTANCE"\)|资源类型定义。取值范围：

 -   instance：ECS实例
-   disk：磁盘
-   snapshot：快照
-   image：镜像
-   securitygroup：安全组
-   volume：存储卷
-   eni：弹性网卡
-   ddh：专有宿主机
-   keypair：SSH密钥对
-   launchtemplate：启动模板

 |
|Action|String|否|TagResources|系统规定参数。取值：TagResources

 |
|OwnerAccount|String|否|ECSforCloud@Alibaba.com|RAM用户的账号登录名称。

 |
|Tag.N.Key|String|否|FinanceDept|资源的标签键。N的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持64个字符，不能以 aliyun、acs:、http:// 或者 https:// 开头。

 |
|Tag.N.Value|String|否|FinanceJoshua|资源的标签值。N的取值范围：1~20。一旦使用标签，该值可以为空字符串。最多支持128个字符，不能以 aliyun、acs:、http:// 或者 https:// 开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=TagResources
&RegionId=cn-hangzhou
&ResourceId.1=i-bp1j6qtvdm8w0z1o0XXX
&ResourceType=instance
&Tag.1.Key=FinanceDept
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<TagResourcesResponse>
  <RequestId>C46FF5A8-C5F0-4024-8262-B16B639225A0</RequestId>
</TagResourcesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C46FF5A8-C5F0-4024-8262-B16B639225A0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|MissingParameter.TagOwnerUid|The parameter - TagOwnerUid should not be null|标签归属用户不存在。|
|404|MissingParameter.TagOwnerBid|The parameter - TagOwnerBid should not be null|标签归属渠道不存在。|
|404|MissingParameter.Tags|The parameter - Tags should not be null|标签参数不存在。|
|404|MissingParameter.RegionId|The parameter - RegionId should not be null|地域参数不存在。|
|403|PermissionDenied.TagOwnerUid|The specified operator not have permission to set TagOwnerUid value.|无权设置标签归属者。|
|403|PermissionDenied.Scope|The specified operator not have permission to set Scope value.|可见范围参数不可修改。|
|400|NumberExceed.ResourceIds|The ResourceIds parameter's number is exceed , Valid : 50|资源ID参数不能超过50个。|
|400|NumberExceed.Tags|The Tags parameter's number is exceed , Valid : 20|标签列表参数不能超过20个。|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|标签键中存在重复的键。|
|404|InvalidResourceId.NotFound|The specified ResourceIds are not found in our records.|资源不存在。|
|404|InvalidResourceType.NotFound|The ResourceType provided does not exist in our records.|指定的资源类型不存在。|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|指定的标签值不合法。|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|Invalid.Scope|The specified scope is invalid.|可见范围参数非法。|
|403|NoPermission.Tag|The operator is not permission for the tag.|没有操作该资源标签的权限。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

