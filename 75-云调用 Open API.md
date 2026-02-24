# 云调用 Open API

返回文档云调用意为在云函数中使用支付宝开放接口 Open API。通过 SDK 提供的 Open API 接口，无需进行复杂的加签操作，由平台进行身份验证和鉴权操作，使得开发者更便捷地调用 Open API。当前云开发已经涵盖26个开放平台产品、49个权限集、420+ API 供大家调用。

## API 命名规则

云调用 API 均通过 cloud.Open API 对象透出。支付宝开放接口 Open API 名由.连接，需要转换为驼峰命名结构，例如小程序生成推广二维码的 Open API 接口名为alipay.open.app.qrcode.create，在云调用中的 API 名为alipayOpenAppQrcodeCreate。

## 前提条件

在使用云调用之前，需要在控制台中绑定产品，否则会报错提示无权限，绑定产品请参见产品绑定（以小程序码产品为例）。

## 集成说明

Open API 集成前的配置方式请参见集成说明。

## 调用方式

每个云调用 API 需要通过request方法触发实际的调用操作，request的入参为支付宝开放接口 Open API 的请求参数，返回值即为对应 Open API 的响应参数。
```
const res = await cloud.openapi.alipayOpenAppQrcodeCreate.request({
// ... 请求参数
});
```


## 示例代码

云调用示例：
```JavaScript
const cloud = require("@alipay/faas-server-sdk");
//环境管理 - 云调用 - 开通云调用，并增加接口白名单 alipayOpenAppQrcodeCreate
exports.main = async (event, context) => {
return await cloud.openapi.alipayOpenAppQrcodeCreate.request({
'biz_content':{
'url_param':"page/component/component-pages/view/view",
"query_param":"x=1",
color:"0x00BFFF",
size:"s",
describe:"二维码描述"
}
});
return res;
};
```


## Open API

### 私域产品

支付宝全面开放公域场景打通小程序私域，助力私域运营的拉新、留存和转化，通过小程序和支付宝开放各用户触达运营渠道（消息、支付成功页等）的连接，具备更多手段实现拉新、留存、召回复访以及转化变现的用户日常运营。详情情参见产品简介。

#### 小程序

搜索关键词：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenSearchBaseorderModify | 搜索运营提报基础信息工单接口 |
| alipayOpenSearchOrderdetailQuery | 查询搜索服务工单的详细信息接口 |
| alipayOpenSearchServiceorderBatchquery | 搜索运营服务查询接口 |
| alipayOpenSearchSubservicekeywordQuerystatus | 查询小程序服务关键词的审核工单的状态 |
| alipayOpenSearchAppkeywordDelete | 删除搜索关键词接口 |
| alipayOpenSearchSubservicekeywordBatchquery | 服务关键词批量查询接口 |
| alipayOpenSearchAppkeywordBatchquery | 查询小程序已配置关键词 |
| alipayOpenSearchAppkeywordApply | 提报搜索关键词 |
| alipayOpenSearchAppkeywordquotaQuery | 查询小程序可配置关键词数 |
| alipayOpenSearchAppkeywordQuerystatus | 查询小程序搜索关键词的审核工单的状态 |
| alipayOpenSearchSubservicekeywordApply | 小程序-服务推广-提报服务关键词 |
| alipayOpenSearchSubservicekeywordDelete | 删除服务关键词 |
小程序开发管理：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenMiniVersionAuditApply | 小程序提交审核 |
| alipayOpenMiniExperienceQuery | 小程序体验版状态查询接口 |
| alipayOpenMiniQrcodeBind | 关联普通二维码 |
| alipayOpenMiniPluginuseconfigQuery | 插件使用关系查询 |
| alipayOpenMiniExperienceCreate | 小程序生成体验版 |
| alipayOpenMiniIsvQuery | isv查询代商家创建小程序记录 |
| alipayOpenMiniVersionAuditCancel | 三方实例化小程序撤销审核 |
| alipayOpenMiniMiniappServiceconfigModify | 小程序设置客服方式 |
| alipayOpenMiniVersionAuditedCancel | 小程序退回开发 |
| alipayOpenMiniBaseinfoModify | 小程序修改基础信息 |
| alipayOpenMiniSafedomainDelete | 小程序删除域白名单 |
| alipayOpenMiniVersionDetailQuery | 小程序版本详情查询 |
| alipayOpenViolationViolationeventBatchquery | 违规记录列表查询 |
| alipayOpenMiniVersionUpload | 小程序基于模板上传版本 |
| alipayOpenViolationViolationdetailQuery | 违规记录详情查询 |
| alipayOpenMiniVersionOnline | 小程序上架 |
| alipayOpenMiniVersionDelete | 小程序删除版本 |
| alipayOpenMiniPluginuseconfigUpgrade | 插件版本升级 |
| alipayOpenMiniTemplateUsageQuery | 查询使用模板的小程序列表 |
| alipayOpenMiniCategoryRequireQuery | 查询类目所需资质信息 |
| alipayOpenMiniQrcodeUnbind | 删除已关联普通二维码 |
| alipayOpenMiniExperienceCancel | 小程序取消体验版 |
| alipayOpenMiniVersionListQuery | 小程序版本列表查询 |
| alipayOpenMiniVersionRollback | 小程序回滚 |
| alipayOpenAppMembersCreate | 应用添加成员 |
| alipayOpenMiniBaseinfoQuery | 查询小程序基础信息 |
| alipayOpenMiniVersionGrayCancel | 小程序结束灰度 |
| alipayOpenMiniCategoryQuery | 小程序类目树查询 |
| alipayOpenMiniVersionBuildQuery | 小程序查询版本构建状态 |
| alipayOpenMiniSafedomainCreate | 小程序添加域白名单 |
| alipayOpenMiniVersionGrayOnline | 小程序灰度上架 |
| alipayOpenAppMembersQuery | 应用查询成员列表 |
| alipayOpenMiniIndividualBusinessCertify | 个人账户升级为个体工商户 |
| alipayOpenAppMembersDelete | 删除应用成员 |
| alipayOpenMiniVersionOffline | 小程序下架 |
| alipayOpenMiniPluginuseconfigOnline | 全量插件使用端版本配置 |
| alipayOpenMiniPluginuseconfigUpgradeCancel | 插件版本撤销灰度 |
| alipayOpenMiniIsvCreate | isv服务商代商户创建小程序 |
小程序商品：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenAppLocalitemTemplateQuery | 获取本地商品模板信息 |
| alipayOpenAppItemAllcategoryQuery | 获取普通商品类目接口 |
| alipayMarketingCertificateCertificationPrepareuse | 凭证核销准备 |
| alipayMarketingCertificateCertificationUse | 同步凭证核销状态 |
| spiAlipayMarketingCertificateOrderRefundconfirm | 退款前向商户确认是否可以退款 |
| spiAlipayMarketingCertificateCertificationSend | 三方凭证发放 |
| alipayOpenAppLocalitemCreate | 创建小程序本地商品 |
| alipayOpenAppItemListQuery | 小程序商品分页查询接口 |
| alipayOpenAppLocalitemModify | 小程序本地商品修改接口 |
| alipayOpenAppLocalitemAllcategoryQuery | 获取本地商品类目接口 |
| alipayOpenAppItemCreate | 小程序商品创建接口 |
| alipayOpenAppItemQuery | 小程序商品详情查询接口 |
| alipayOpenAppLocalitemDirectModify | 小程序本地商品免审更新商品接口 |
| alipayMarketingCertificateCertificationRefund | 撤销凭证核销状态 |
| alipayOpenAppItemDirectModify | 商品免审更新接口 |
| alipayOpenAppItemModify | 小程序商品更新接口 |
| alipayOpenAppLocalitemQuery | 小程序本地商品详情查询接口 |
| alipayMarketingCertificateOrderRefundconfirmcommit | 订单退款前商户回复确认退款结果 |
| alipayOpenAppItemDelete | 小程序商品移除接口 |
| alipayMarketingCertificateCertificationBatchquery | 查询凭证信息 |
| alipayMarketingCertificateUserBatchquery | 条件查询用户凭证 |
搜索直达：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenSearchboxUpgradeSave | 小程序升级成品牌直达 |
| alipayOpenSearchboxDowngradeSave | 搜索直达降级 |
| alipayOpenSearchBoxApply | 申请创建搜索直达配置 |
| alipayOpenMiniMiniappBrandCancel | 小程序品牌提交认证后取消品牌认证 |
| alipayOpenSearchboxDowngradePreconsult | 直达降级准入 |
| alipayOpenSearchBoxactivityQuery | 查询搜索直达活动配置详情 |
| alipayOpenSearchBoxModify | 修改搜索直达配置 |
| alipayOpenSearchBoxactivityApply | 申请创建搜索直达活动配置 |
| alipayOpenSearchBoxConsult | 搜索直达创建预校验 |
| alipayOpenMiniMiniappBrandQuery | 小程序品牌提交认证后查询品牌审核结果以及商户已有品牌 |
| alipayOpenSearchboxUpgradePreconsult | 搜索直达升级准入 |
| alipayOpenSearchBoxOffline | 下架搜索直达 |
| alipayOpenSearchBoxOnline | 上架搜索直达 |
| alipayOpenMiniMiniappBrandSubmit | 小程序品牌提交认证 |
| alipayOpenSearchBoxQuery | 查询搜索直达配置详情 |
| alipayOpenSearchboxBusinessdistrictQuery | 查询可绑定的商圈查询 |
| alipayOpenSearchBoxBatchquery | 批量查询搜索直达配置列表 |
小程序交易组件：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenMiniOrderCreate | 订单创建 |
| alipayOpenMiniOrderQuery | 查询订单 |
| alipayOpenMiniOrderDeliverySend | 订单发货 |
| alipayOpenMiniOrderDeliveryReceive | 订单确认收货 |
消息：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenMiniMessageTemplatelibBatchquery | 消息母板批量查询接口 |
| alipayMarketingActivityDeliveryQuery | 查询推广计划 |
| antMerchantExpandApprecommendAvailableQuery | 查询可关联APP的账号列表 |
| antMerchantExpandApprecommendAccountQuery | 查询已关联指定APP的账号列表 |
| antMerchantExpandApprecommendAccountCreate | 关联账号和小程序 |
| alipayOpenMiniMessageTemplateApply | 消息模板申领接口 |
| alipayOpenMiniTemplatemsgTinypayswitchConfirm | 小程序支付消息确认接口 |
| alipayMarketingActivityDeliveryChanged | 推广计划状态变更消息 |
| alipayOpenAppMiniTemplatemessageSend | 小程序发送模板消息 |
| alipayMarketingActivityDeliveryCreate | 创建推广计划 |
| alipayMarketingActivityDeliveryStop | 停止推广计划 |
小程序码：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenAppQrcodeCreate | 小程序生成推广二维码接口 |
| alipayOpenMiniQrcodePatternCreate | 创建关联普通二维码模式 |
收藏：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenMiniTipsDeliveryCreate | 小程序收藏引导投放活动配置创建 |
| alipayOpenMiniTipsDeliveryBatchquery | 小程序收藏引导投放活动配置批量查询 |
| alipayOpenMiniTipsDeliveryModify | 小程序收藏引导投放活动修改 |
| alipayOpenMiniTipsStatisticQuery | 小程序收藏引导汇总数据查询 |
| alipayOpenMiniTipsDeliveryQuery | 小程序收藏引导投放活动详情查询 |
小程序服务：
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenAppServiceListQuery | 服务批量查询 |
| alipayOpenAppServiceSchemaQuery | 服务 schema下发 |
| alipayOpenAppServiceQuery | 服务查询 |
| alipayOpenAppServiceDelete | 服务失效接口 |
| alipayOpenAppServiceApply | 服务提报申请 |
订单中心：
| API 名称 | 使用文档 |
| --- | --- |
| spiAlipayMerchantOrderRealtimeinfoQuery | 商户订单实时信息查询 |
| alipayMerchantOrderSync | 订单数据同步接口 |
生物核身：
| API 名称 | 使用文档 |
| --- | --- |
| alipaySecurityRiskVerifyidentityMiniappConfirm | 小程序核验服务结果确认接口 |


### 安全产品

交易安全防护产品面向支付宝的企业合作伙伴，实时输出支付宝核心风控系统识别出的风险交易，风险类型包括用户投诉、欺诈、花呗套现、赌博和虚假交易等类型，并会随着业务发展不断新增，详情请参见交易安全防护产品介绍。

#### 交易安全防护


| API 名称 | 使用文档 |
| --- | --- |
| alipaySecurityRiskCustomerriskSend | 商户数据同步 |


### 支付产品

App 支付是指商家在商家移动端 App 中集成支付宝 SDK，调起支付宝来完成付款的一种支付产品。适用于在商家移动端 App 内使用支付宝支付功能的场景。该产品在签约完成后，需要技术集成完成后方可使用，详情请参见产品介绍。

#### 新当面资金授权：

新当面预授权是指商家通过扫用户付款码先冻结用户一定资金作为押金，后按实际消费金额从用户冻结资金中扣除给商家，剩余金额解冻返还用户的一种支付产品。该产品在签约完成后，需要技术集成方可使用，详情请参见新当面资金授权产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayFundAuthOperationDetailQuery | 资金授权操作查询接口 |
| alipayTradeOrderinfoSync | 支付宝订单信息同步接口 |
| alipayFundAuthOrderUnfreeze | 资金授权解冻接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradePay | 统一收单交易支付接口 |
| alipayFundAuthOrderVoucherCreate | 资金授权发码接口 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayFundAuthOrderFreeze | 资金授权冻结接口 |
| alipayFundAuthOperationCancel | 资金授权撤销接口 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |


#### 当面付

当面付收单：
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradeCancel | 统一收单交易撤销接口 |
| alipayTradePrecreate | 统一收单线下交易预创建 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradePay | 统一收单交易支付接口 |
| alipayTradeCreate | 统一收单交易创建接口 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |


#### 刷脸付

支付宝刷脸付是基于人工智能、生物识别、3D传感、大数据风控技术，最新实现的新型支付方式。用户在无需打开手机的情况下，凭借刷脸完成支付。刷脸付的使用，有效提升用户的消费体验，提高了商家的收银效率，详情请参见刷脸付产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| zolozAuthenticationSmilepayInitialize | 刷脸支付初始化 |
| zolozAuthenticationCustomerFtokenQuery | 人脸 ftoken 查询消费接口 |


#### 手机网站支付

手机网站支付是指商家在移动端网页展示商品或服务，用户在商家页面确认使用支付宝支付后，浏览器自动跳转支付宝 App 或支付宝网页完成付款的支付产品。该产品在签约完成后，需要技术集成方可使用，详情请参见手机网站支付产品介绍。快捷收集 wap 支付：
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradeRefundDepositbackCompleted | 收单退款冲退完成通知 |
| alipayTradeWapPay | 手机网站支付接口 2.0 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |


#### 商家扣款

商家扣款是商家引导用户进行签约授权，签约成功后商家根据签约协议号，再主动调接口完成扣款的支付产品，支持周期性的扣款模式，详情请参见商家扣款产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayUserAgreementUnsign | 支付宝个人代扣协议解约接口 |
| alipayUserAgreementPageSign | 支付宝个人协议页面签约接口 |
| alipayTradeCancel | 统一收单交易撤销接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradePay | 统一收单交易支付接口 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayUserAgreementExecutionplanModify | 周期性扣款协议执行计划修改接口 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |
| alipayTradeAppPay | app支付接口2.0 |
| alipayUserAgreementQuery | 支付宝个人代扣协议查询接口 |
| alipayTradeOrderSettle | 交易分账查询接口 |
| alipayTradeRoyaltyRateQuery | 分账比例查询 |
| alipayTradeRoyaltyRelationBind | 分账关系绑定 |
| alipayTradeOrderSettleQuery | 交易分账查询接口 |
| alipayTradeRoyaltyRelationBatchquery | 分账关系查询 |
| alipayTradeOrderOnsettleQuery | 分账剩余金额查询 |
| alipayTradeRoyaltyRelationUnbind | 分账关系解绑 |


#### APP 支付

App 支付是指商家在商家移动端 App 中集成支付宝 SDK，调起支付宝来完成付款的一种支付产品。适用于在商家移动端 App 内使用支付宝支付功能的场景。该产品在签约完成后，需要技术集成完成后方可使用，详情请参见 APP 支付产品介绍。快捷收集安全支付：
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradeRefundDepositbackCompleted | 收单退款冲退完成通知 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradeAppPay | app 支付接口2.0 |


#### 预授权支付

预授权支付指用户产生实际消费前，商家可以提前冻结用户一定资金作为押金，后续按实际消费金额从用户冻结资金中扣除给商家，剩余金额解冻返还用户的一种支付产品，详情请参见预授权支付产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayFundAuthOperationDetailQuery | 资金授权操作查询接口 |
| alipayFundAuthOrderUnfreeze | 资金授权解冻接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradePay | 统一收单交易支付接口 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayFundAuthOperationCancel | 资金授权撤销接口 |
| alipayFundAuthOrderAppFreeze | 线上资金授权冻结接口 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |


#### JSAPI 支付

JSAPI支付指商家在支付宝 App 中，通过调用支付宝提供的 JSAPI 接口，在支付场景中唤起支付宝收银台完成收款的一款支付产品，详情请参见 JSAPI 支付产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradeRefundDepositbackCompleted | 收单退款冲退完成通知 |
| alipayTradeCancel | 统一收单交易撤销接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradeCreate | 统一收单交易创建接口 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |


#### 电脑网站支付

电脑网站支付是指商户在电脑网页展示商品或服务，用户在商户页面确认使用支付宝支付时，浏览器自动跳转支付宝电脑网页完成付款的支付产品。该产品在签约完成后，需要技术集成方可使用，详情请参见产品介绍。快捷即时到账：
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradeRefundDepositbackCompleted | 收单退款冲退完成通知 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |
| alipayDataDataserviceBillDownloadurlQuery | 查询对账单下载地址 |
| alipayTradePagePay | 统一收单下单并支付页面接口 |


### 商家会员卡产品

会员卡产品是商家会员营销的基础产品，为满足商家对于持有会员卡用户的营销需求。商家会员卡（原商户会员卡）产品提供了创建、领取、修改以及同步交易设置了一系列产品，开发者可以根据自己想实现的效果选择合适的接口产品进行开发，以实现各行业有特色的会员卡应用。开发者可根据自己需求，自由组合实现电子会员卡功能：引导用户开卡、积分查询、交易记录、卡会员等级查询、卡权益展示、卡适用门店展示等能力，详情请参见商家会员卡产品介绍。

#### APP支付宝登录

无线账户授权：
| API 名称 | 使用文档 |
| --- | --- |
| alipaySystemOauthToken | 换取授权访问令牌 |
| alipayUserInfoShare | 支付宝会员授权信息查询接口 |
| alipayUserInfoAuth | 用户登录授权 |


#### 获取会员信息

获取用户信息：
| API 名称 | 使用文档 |
| --- | --- |
| alipaySystemOauthToken | 换取授权访问令牌 |
| alipayUserInfoShare | 支付宝会员授权信息查询接口 |
| alipayOpenAuthUserauthRelationshipQuery | 用户授权关系查询 |
| alipayOpenAuthUserauthCancelled | 用户授权取消消息 |


#### 支付宝身份验证

支付宝身份验证是基于支付宝客户端的实人认证产品，采用多因子认证技术快速得出认证结果；主要解决线上实人开户、账号实名认证、账号实人登录等场景中个人身份的识别问题，详情请参见支付宝身份验证产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayUserCertifyOpenCertify | 身份认证开始认证 |
| alipayUserCertifyOpenQuery | 身份认证记录查询 |
| alipayUserCertifyOpenInitialize | 身份认证初始化服务 |


#### 人脸认证

人脸认证源于支付宝的实人认证产品，是一款对用户身份信息真实性进行验证审核的服务套件，提供人脸核身、活体检测、卡证识别等三大子产品，详情请参见人脸验证产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| datadigitalFincloudGeneralsaasFaceVerificationQuery | 人脸核身结果查询 |
| datadigitalFincloudGeneralsaasOcrServerDetect | 服务端OCR |
| datadigitalFincloudGeneralsaasFaceSourceCertify | 权威核验源的核验接口 |
| datadigitalFincloudGeneralsaasFaceCheckInitialize | 人脸检测初始化 |
| datadigitalFincloudGeneralsaasFaceCertifyVerify | H5人脸核身开始认证 |
| datadigitalFincloudGeneralsaasOcrMobileInitialize | OCR端云一体化识别初始化 |
| datadigitalFincloudGeneralsaasFaceCertifyInitialize | H5人脸核身初始化 |
| datadigitalFincloudGeneralsaasFaceCheckQuery | 人脸检测结果数据查询 |
| datadigitalFincloudGeneralsaasFaceCertifyQuery | H5人脸核身查询记录 |
| datadigitalFincloudGeneralsaasFaceVerificationInitialize | 人脸核身初始化 |


### 公域

支持消费圈、支付成功页、首页等多个频道，商家可根据自己的需求选择频道提报，详情请参见产品介绍。

#### 日常推广-优惠券


| API 名称 | 使用文档 |
| --- | --- |
| alipayMarketingActivityDeliveryCreate | 创建推广计划 |
| alipayMarketingActivityDeliveryQuery | 查询推广计划 |
| alipayMarketingActivityDeliveryChanged | 推广计划状态变更消息 |
| alipayMarketingActivityDeliveryStop | 停止推广计划 |


### 其他

#### 应用 AES 密钥管理

AES（高级加密标准，Advanced Encryption Standard）是目前对称密钥加密中比较通用的一种加密方式。通过应用 AES 密钥管理功能，服务商可以获取名下商家已授权应用的 AES 密钥，解密开放平台加密的用户信息内容，如代商家获取会员手机号。如果商家没有 AES 密钥，或者需要重新设置，服务商则可以通过此功能代商家设置授权应用的 AES 密钥，详情请参见应用 AES 密钥管理产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenAuthAppAesGet | 授权应用 aes 密钥查询 |
| alipayOpenAuthAppAesSet | 授权应用 aes 密钥设置 |


#### 服务商代运营基础包

代运营基础功能包提供、代商家报名返佣政策、IoT 设备三绑定等功能。为服务商代商家进行数字化经营的基础产品，详情请参见服务商代运营基础产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenSpOperationQrcodeQuery | 查询代运营授权或者账号绑定二维码 |
| alipayOpenSpBlueseaactivityQuery | 服务商返佣活动申请单详情查询 |
| alipayMerchantIotDeviceVerify | IoT设备绑定校验 |
| alipayMerchantIotDeviceBind | IoT 设备绑定门店 |
| alipayMerchantIotDeviceQuery | IoT设备绑定关系查询 |
| alipayOpenSpBlueseaactivityCreate | 服务商返佣活动报名申请 |
| alipayOpenSpOperationApply | 向商户发起代运营操作 |
| alipayOpenSpBlueseaactivityModify | 服务商返佣活动申请单修改 |


#### 车主平台停车在线缴费

支付宝车主平台停车在线缴费是面向停车场业主方及车主用户，提供使用支付宝便捷查询和缴纳停车费用从而减少现金支付、提升停车场通行效率的解决方案。停车系统通过接入停车在线缴费解决方案，可获得更多场景入口能力、更直接的用户触达能力、更高效的支付能力，详情请参见车主平台停车在线缴费产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayEcoMycarParkingCharginginfoSync | 车辆停车计费接口 |
| alipayCommerceTransportParkingPaymentinfoSync | 停车支付模板消息配置 |
| alipayCommerceTransportParkingExitinfoSync | 停车离场消息模板配置 |
| alipayEcoMycarParkingParkinglotinfoUpdate | 修改停车场信息 |
| alipayEcoMycarParkingParkinglotinfoQuery | 停车场信息查询接口 |
| alipayEcoMycarParkingEnterinfoSync | 车辆驶入接口 |
| alipayEcoMycarParkingExitinfoSync | 车辆驶出接口 |
| alipayEcoMycarParkingSpaceinfoSync | 停车场车位信息同步接口 |
| alipayEcoMycarParkingVehicleQuery | 车牌查询接口 |
| alipayCommerceTransportParkingEnterinfoSync | 停车入场模板消息配置 |
| alipayEcoMycarParkingOrderSync | 订单同步接口 |
| alipayEcoMycarParkingChargeinfoSync | 停车场价格信息同步 |
| alipayEcoMycarParkingConfigSet | 停车 ISV 系统配置接口 |
| alipayEcoMycarParkingOrderUpdate | 订单更新接口 |
| alipayEcoMycarParkingConfigQuery | ISV 系统配置查询接口 |
| alipayEcoMycarParkingParkinglotinfoCreate | 录入停车场信息接口 |


#### 支付宝广告投放

为方便商家及广告代理商通过 API 快速进行留资管理、转化管理等操作，支付宝向支付宝数字推广平台

的所有商家及代理商提供了支付宝广告投放产品，详情请参见支付宝广告投放产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayDataDataserviceDspcreativeUpload | 外部DSP创意送审接口 |
| alipayDataDataserviceDspcreativeBatchquery | DSP广告状态查询接口 |
| alipayDataDataserviceDspcreativeBatchquery | DSP 创意送审和创意状态查询 |
| alipayDataDataserviceAdPromotepageDownload | 自建推广页留资数据查询 |
| alipayDataDataserviceAdPromotepageBatchquery | 自建推广页列表批量查询 |


#### 第三方应用授权

通过第三方应用授权，服务商在取得商家授权后，可以代商家调用支付宝开放接口，以完成相应的业务逻辑（如代替商家发起当面付的收单请求等）。授权采用标准的 OAuth 2.0 流程，要进行第三方代调用，服务商需要在第三方应用中添加对应功能并获得商家授权，本文介绍服务商的第三方应用如何取得商家应用的授权，详情请参见第三方应用授权产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayOpenAuthTokenApp | 换取应用授权令牌 |
| alipayOpenAuthAppauthInviteCreate | ISV向商户发起应用授权邀约 |
| alipayOpenAuthAppauthCancelled | 第三方应用授权取消消息 |
| alipayOpenAuthTokenAppQuery | 查询某个应用授权AppAuthToken的授权信息 |


#### 电子发票

支付宝向商家提供电子发票功能可以开具电子发票。商家通过开票平台开具电子发票，经过用户授权后将电子发票存入发票管家。用户可以在发票管家中查看管理自己的电子发票，详情请参见点子发票产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayEbppInvoiceMerchantlistEnterApply | 商户批量入驻申请接口 |
| alipayEbppInvoiceInfoSend | 发票信息回传接口（新版） |
| alipayEbppInvoiceApplyResultSync | ISV向支付宝同步发票申请结果 |
| alipayEbppInvoiceTitleDynamicGet | 根据动态码查询发票抬头 |


#### 分享到支付宝

分享到支付宝是指第三方移动应用通过接入该功能，让用户可以分享图片、网页至支付宝。详情请参见分享到支付宝产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipaySdkShareAuth | 接入准备 |


### 营销产品

#### 商家券

商家券是支付宝为商家/服务商提供的电子优惠券，可通过该产品实现商家优惠券创建、投放、领取，并且满足商家/服务商在自身系统核销优惠券，核销后同步核销状态到支付宝，同时也满足商家/服务商将自有营销体系内的优惠券在支付宝的经营场景（支付宝小程序、卡包、支付有礼、经营推广、活动大促等）进行发放和运营，详情请参见商家劵产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayMarketingActivityOrdervoucherCreate | 创建商家券活动 |
| antMerchantExpandOrderQuery | 商户申请单查询 |
| alipayMarketingActivityOrdervoucherQuery | 查询商家券活动 |
| alipayMarketingActivityConsult | 活动领取咨询接口 |
| alipayMarketingActivityShopBatchquery | 查询活动可用门店 |
| antMerchantExpandShopModify | 修改蚂蚁店铺 |
| alipayMarketingActivityOrdervoucherUse | 同步券核销状态 |
| alipayMarketingCampaignOrderVoucherConsult | 订单优惠前置咨询 |
| alipayMarketingActivityMessageUsed | 券核销消息 |
| alipayMarketingActivityQuery | 查询活动详情 |
| antMerchantExpandShopReceiptaccountSave | 店铺增加收单账号 |
| alipayMarketingActivityMerchantBatchquery | 查询活动可用商户 |
| antMerchantExpandShopClose | 蚂蚁店铺关闭 |
| alipayMarketingActivityGoodsBatchquery | 查询活动适用商品 |
| alipayMarketingActivityAppBatchquery | 查询活动可用小程序 |
| alipayMarketingActivityUserQueryvoucher | 查询用户券详情 |
| alipayMarketingActivityOrdervoucherAppend | 查询用户券详情 |
| alipayMarketingActivityMessageReceived | 券领取通知 |
| antMerchantExpandShopPageQuery | 店铺分页查询接口 |
| alipayMarketingActivityOrdervoucherCodecount | 统计商家券券码数量 |
| alipayMarketingActivityMessageAppended | 券活动预算追加通知 |
| alipayMarketingActivityOrdervoucherModify | 修改商家券活动基本信息 |
| alipayMarketingActivityOrdervoucherRefund | 取消券核销状态 |
| alipayMarketingActivityOrdervoucherCodedeposit | 同步商家券券码 |
| antMerchantExpandShopCreate | 蚂蚁店铺创建 |
| antMerchantExpandShopQuery | 店铺查询接口 |
| alipayMarketingActivityBatchquery | 条件查询活动列表 |
| antMerchantExpandShopSaveRejected | 店铺保存拒绝消息 |
| antMerchantExpandMccQuery | 商户mcc信息查询 |
| alipayMarketingActivityOrdervoucherStop | 停止商家券活动 |
| alipayMarketingActivityMessageExpired | 券过期消息 |
| alipayMarketingActivityUserBatchqueryvoucher | 条件查询用户券 |
| alipayMarketingActivityMessageModified | 券活动修改通知 |
| antMerchantExpandShopSavePassed | 店铺保存审核通过消息 |


#### 棋盘密云

棋盘密云为商家提供用户资产的概览、数据融合、分析洞察、人群管理 及应用的能力，可运营的范围既包含商家在支付宝沉淀的私域用户资产，也包含商家的全域用户资产。帮助商家实现持续性、精细化用户运营，促进用户增长、用户活跃及交易转化，详情请参见棋盘密云产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayMerchantQipanCrowduserAdd | 人群中追加用户 |
| alipayMerchantQipanCrowdBatchquery | 查询人群列表 |
| alipayMarketingQipanCrowdtagQuery | 查询圈选标签列表 |
| alipayMerchantQipanInsightcityQuery | 常住省市查询 |
| alipayMarketingQipanCrowdwithtagQuery | 标签圈选预估人群规模 |
| alipayMerchantQipanCrowdCreate | 上传创建人群 |
| alipayMerchantQipanCrowdQuery | 查询人群详情 |
| alipayMerchantQipanCrowduserDelete | 人群中删除用户 |
| alipayMerchantQipanCrowdModify | 修改人群 |
| alipayMerchantQipanInsightQuery | 画像分析 |


#### 支付券

支付券是支付宝面向商家/服务商提供的一种营销工具。商家在创建支付券后，可以通过不同渠道（支付宝小程序、卡包、支付有礼、日常推广、活动大促等）发送给用户，当用户使用支付宝交易时，支付券便会伴随交易自动核销/抵扣。商家只需要完成配券、投放的步骤，能够快速便捷地帮助商家落地营销活动，详情请参见支付劵产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| antMerchantExpandOrderQuery | 商户申请单查询 |
| alipayMarketingActivityVoucherAppend | 追加支付券预算 |
| alipayMarketingActivityVoucherQuery | 查询支付券详情 |
| alipayMarketingActivityMessageStopped | 券活动停止通知 |
| alipayMarketingActivityConsult | 活动领取咨询接口 |
| alipayMarketingActivityShopBatchquery | 查询活动可用门店 |
| antMerchantExpandShopModify | 修改蚂蚁店铺 |
| alipayMarketingActivityVoucherStop | 停止支付券 |
| antMerchantExpandIndirectImageUpload | 图片上传 |
| alipayMarketingCampaignOrderVoucherConsult | 订单优惠前置咨询 |
| alipayMarketingActivityQuery | 查询活动详情 |
| antMerchantExpandShopReceiptaccountSave | 店铺增加收单账号 |
| alipayMarketingActivityMerchantBatchquery | 查询活动可用商户 |
| antMerchantExpandShopClose | 蚂蚁店铺关闭 |
| alipayMarketingActivityGoodsBatchquery | 查询活动适用商品 |
| alipayMarketingActivityMessageCreated | 券活动创建通知 |
| alipayMarketingActivityVoucherModify | 修改支付券基本信息 |
| alipayMarketingActivityAppBatchquery | 查询活动可用小程序 |
| alipayMarketingActivityUserQueryvoucher | 查询用户券详情 |
| alipayMarketingActivityVoucherCreate | 创建支付券 |
| antMerchantExpandShopPageQuery | 店铺分页查询接口 |
| antMerchantExpandShopCreate | 蚂蚁店铺创建 |
| antMerchantExpandShopQuery | 店铺查询接口 |
| alipayMarketingActivityBatchquery | 条件查询活动列表 |
| alipayMarketingActivityVoucherPublish | 激活支付券 |
| antMerchantExpandMccQuery | 商户mcc信息查询 |
| alipayMarketingActivityMessageExpired | 券过期消息 |
| alipayMarketingActivityUserBatchqueryvoucher | 条件查询用户券 |


#### 商家会员卡

会员卡产品是商家会员营销的基础产品，为满足商家对于持有会员卡用户的营销需求。商家会员卡（原商户会员卡）产品提供了创建、领取、修改以及同步交易设置了一系列产品，开发者可以根据自己想实现的效果选择合适的接口产品进行开发，以实现各行业有特色的会员卡应用，详情请参见商家会员卡产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayMarketingCardTemplateModify | 会员卡模板修改 |
| alipayMarketingCardBenefitModify | 会员卡模板外部权益修改 |
| alipaySystemOauthToken | 换取授权访问令牌 |
| alipayMarketingCardQuery | 会员卡查询 |
| alipayMarketingCardOpen | 会员卡开卡 |
| alipayMarketingCardTemplateCreate | 会员卡模板创建 |
| alipayMarketingCardBenefitDelete | 会员卡模板外部权益删除 |
| alipayMarketingCardTemplateQuery | 会员卡模板查询接口 |
| alipayMarketingCardActivateurlApply | 获取会员卡领卡投放链接 |
| alipayMarketingCardDelete | 会员卡删卡 |
| alipayMarketingCardMessageNotify | 会员卡消息通知 |
| alipayUserOpencardResultNotify | 会员卡开卡结果通知 |
| alipayMarketingCardBenefitQuery | 会员卡模板外部权益查询 |
| alipayMarketingCardBenefitCreate | 会员卡模板外部权益创建 |
| alipayMarketingCardFormtemplateSet | 会员卡开卡表单模板配置 |
| alipayMarketingCardActivateformQuery | 查询用户提交的会员卡表单信息 |
| spiAlipayUserOpencardGet | 会员卡开通，获取会员卡信息 |
| alipayMarketingCardUpdate | 会员卡更新 |


### 资金

#### 花呗分期

花呗分期是蚂蚁集团推出的消费金融产品，用户在商家端网站或线下门店购物时使用花呗分期支付，订单全额实时支付到商家支付宝账户中，用户分期偿还花呗，详情请参见花呗分期产品介绍。花呗分期淘外 Z97：
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradePay | 统一收单交易支付接口 |
| alipayTradeWapPay | 手机网站支付接口2.0 |
| alipayTradePrecreate | 统一收单线下交易预创建 |
| alipayTradeAppPay | app 支付接口2.0 |


#### 商家分账

商家分账，指资金在到达商家的支付宝账号后，支付宝根据商家传入的分账规则，将相应的资金从商家的支付宝账号划转至分账对象的支付宝账号，详情请参见商家分账产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradeOrderSettleQuery | 交易分账查询接口 |
| alipayTradeOrderSettle | 统一收单交易结算接口 |
| alipayTradeRoyaltyRateQuery | 分账比例查询 |
| alipayTradeRoyaltyRelationBind | 分账关系绑定 |
| alipayTradeRoyaltyRelationBatchquery | 分账关系查询 |
| alipayTradeOrderSettleNotify | 交易分账结果通知 |
| alipayTradeOrderOnsettleQuery | 分账剩余金额查询 |
| alipayTradeRoyaltyRelationUnbind | 分账关系解绑 |


### 信用产品

#### 芝麻免押

芝麻免押是一款结合芝麻信用与预授权支付的免押金信用产品，旨在为商家提升商业效率的同时，为用户创造 因为信用，所以简单 的便捷生活方式，详情请参见芝麻免押产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| alipayTradePay | 统一收单交易支付接口 |
| alipayTradeFastpayRefundQuery | 统一收单交易退款查询 |
| alipayTradeClose | 统一收单交易关闭接口 |
| alipayFundAuthOperationCancel | 资金授权撤销接口 |
| alipayFundAuthOperationDetailQuery | 资金授权操作查询接口 |
| alipayFundAuthOrderAppFreeze | 线上资金授权冻结接口 |
| alipayTradeOrderinfoSync | 支付宝订单信息同步接口 |
| alipayFundAuthOrderUnfreeze | 资金授权解冻接口 |
| alipayTradeQuery | 统一收单交易查询 |
| alipayTradeRefund | 统一收单交易退款接口 |


#### 芝麻 GO

芝麻 GO 是一款低门槛、高效、灵活的商家营销工具，帮助商家降低用户决策门槛，有效锁定用户消费；助力商家拉新、复购、提升客单价，并获得确定性营销 ROI。商家可让用户“先享权益，承诺任务”或者“先享权益，后支付会员费”，使用户切实享受到实惠，打消资金安全和消费陷阱顾虑，详情请参见芝麻 GO 产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| zhimaCreditPeZmgoAgreementQuery | 芝麻Go协议查询接口 |
| zhimaMerchantZmgoTemplateCreate | 商户创建芝麻GO模板接口 |
| zhimaCreditPeZmgoSettleRefund | 芝麻GO结算退款接口 |
| zhimaMerchantZmgoCumulateQuery | 商家芝麻GO累计数据查询接口 |
| zhimaCreditPeZmgoSignApply | 芝麻GO页面签约接口 |
| zhimaMerchantZmgoCumulateSync | 商家芝麻GO累计数据回传接口 |
| zhimaCreditPeZmgoSettleApply | 芝麻GO结算申请 |
| zhimaCreditPeZmgoAgreementUnsign | 芝麻GO协议解约 |
| zhimaMerchantZmgoTemplateQuery | 芝麻 GO 模板查询 |
| zhimaCreditPeZmgoPreorderCreate | 芝麻GO签约预创单 |


#### 芝麻工作证

芝麻工作证是一套具有职业信用特色的营销解决方案的产品，旨在为商家提高对职业人群身份验证识别效率的同时，为用户提供快速一键通行的使用体验，详情请参见芝麻工作证产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| zhimaCustomerJobworthAuthenticationQuery | 职得身份认证查询接口 |
| zhimaCreditPayafteruseCreditagreementSign | 信用服务开通/授权 |


#### 芝麻先享

芝麻先享是一款结合芝麻信用与支付能力的先享服务，后付款的服务类产品，旨在为商家提升商业效率的同时，为用户创造因为信用，所以简单的便捷生活方式，详情请参见芝麻先享产品介绍。
| API 名称 | 使用文档 |
| --- | --- |
| zhimaCreditPayafteruseCreditagreementSign | 信用服务开通/授权 |
| zhimaCreditPayafteruseCreditbizorderOrder | 芝麻先享信用服务下单（免用户确认场景） |
| alipayTradePay | 统一收单交易支付接口 |
| zhimaCreditPayafteruseCreditbizorderQuery | 信用服务订单查询 |
| zhimaCreditPayafteruseCreditagreementQuery | 查询服务开通/授权信息 |
| alipayTradeQuery | 统一收单交易查询 |
| zhimaCreditPayafteruseCreditbizorderCreate | 芝麻先享信用服务下单（用户确认场景） |
| alipayTradeRefund | 统一收单交易退款接口 |
| zhimaCreditPayafteruseCreditbizorderFinish | 结束信用服务订单 |
| alipayTradeAppPay | app支付接口 2.0 |
| alipayTradeOrderPay | 统一收单交易订单支付接口 |
​
