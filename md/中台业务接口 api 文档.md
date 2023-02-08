> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [wiki.517cdn.com](https://wiki.517cdn.com/index.php/AXN%E5%8F%B7%E7%A0%81%E9%9A%90%E7%A7%81%E4%BF%9D%E6%8A%A4/product/%E9%9A%90%E7%A7%81%E5%8F%B7%E4%B8%9A%E5%8A%A1%E4%B8%AD%E5%8F%B0%E5%8A%9F%E8%83%BD/product/%E4%B8%AD%E5%8F%B0%E4%B8%9A%E5%8A%A1%E6%8E%A5%E5%8F%A3api%E6%96%87%E6%A1%A3)

> AXN 号码隐私保护 / 隐私号业务中台功能 / 中台业务接口 api 文档

**此条目已最近一个月被更新过，可以放心饮用。**  
最近一次编辑是由 Wangshuyu 在 2023/1/29 10:55:56 完成的。

  

号码规则▼
-----

*   16,17,19 开头的是虚号
*   13,14,15,18 开头的是实号
*   11,12 开头的是政府公共号码

接口地址▼
-----

*   家里: http://webapi-thethirdpart2020.517jiali.cn/
*   正式: http://webapi-thethirdpart2020.517api.cn/

RMQ 接入▼⇊
--------

### (MQ108) 马里小号 XB 解绑回调▼

<table class="wikitable" wiki_title_2="title_4" wiki_title_3="title_5"><tbody><tr><th>名称</th><th>说明</th><th>申请内容 (示例)</th></tr><tr><td>队列名称</td><td>队列英文名称</td><td>service_exchange1_privatenumberXNB</td></tr><tr><td>队列描述</td><td>队列描述内容</td><td>隐私号 X 解绑 B(马里消费)</td></tr><tr><td>业务类型</td><td>业务类别, 根据业务选择</td><td>8: 服务_交换 1</td></tr><tr><td>生产方</td><td>生产方开发者</td><td>马里</td></tr><tr><td>消费方</td><td>消费方开发者</td><td>马里</td></tr><tr><td>业务对接人</td><td>业务负责开发者</td><td>马里</td></tr><tr><td>推送并发数</td><td>并发推送站点的数量</td><td>10</td></tr><tr><td>请求方式</td><td>消费站点访问方式</td><td>POST</td></tr><tr><td>推送超时时间</td><td>Post 请求超时时间</td><td>默认 120 秒</td></tr><tr><td>业务负责人</td><td>项目经理</td><td>王树羽</td></tr><tr><td>接口地址</td><td></td><td>家里地址: http://webapi-thethirdpart2020.517jiali.cn/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/UnBindClientNumber<p>线上地址: http://webapi-thethirdpart2020.517api.cn/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/UnBindClientNumber</p></td></tr><tr><td>发送消息格式</td><td>生产消息的格式</td><td><pre class="hljs json">{
	"platId": 3,
	"telA": "1347011****",
	"telX": "17111526089",
	"telB": "1370005****",
	"subId": "1000039976446302"
}</pre></td></tr><tr><td>申请日期</td><td>提交任务的日期</td><td>2021.8.27</td></tr></tbody></table>

中台 api 业务接口▼⇊
-------------

### 1. 绑号▼

*   2020-04-26 16:00:00 增加绑号锁，防止一个号码被多人获取。

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_7"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/BindAxNumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>类型</th><th>示例</th></tr><tr><td>userid (工号)</td><td>int</td><td>51218</td></tr><tr><td>regionid (区域 ID)</td><td>int</td><td>1</td></tr><tr><td>private_number (隐私号)</td><td>string</td><td>13125447274</td></tr><tr><td>addUser</td><td>int</td><td>74705</td></tr><tr><td>lastUser</td><td>int</td><td>74705</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "当前号码状态为[2]，无法绑定！",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "dd3ef6e7d3b04510bc58d0b9633afe5e",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 2. 解绑▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_8"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/UnBindAgentNumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>示例</th></tr><tr><td>userid (工号)</td><td>51218</td></tr><tr><td>private_number (隐私号)</td><td>13125447274</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "解绑失败-当前隐私号不存在绑定关系。",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "dd3ef6e7d3b04510bc58d0b9633afe5e",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 3. 查询隐私号列表▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_9"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/QueryAgentNumbers</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>示例</th></tr><tr><td>userid (工号)</td><td>51218</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "错误信息",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
"RequestId": "MG4aa88f2fc20743b99f366e38d3e39d61",
"ResultCode": 2000,
"ResultMsg": "SUCCESS",
"IsEncrypt": 0,
"DataCount": 1,
"PageSize": 1,
"PageIndex": 1,
"DataBody": [
{
"bindState": "已绑定",
"numberState": "正常",
"plateformid": 3,
"platform_name": "阿里云",
"userId": 74705,
"userName": "马里",
"tuserName": "张建",
"tuserId": 57117,
"pool_id": 17,
"ax_numA": "13840474056",
"ax_number": "17052471510",
"ax_subid": "1000034090655007"
}
],
"EncDataBody": ""
}</pre></td></tr></tbody></table>

### 4. 转移绑定账号▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_10"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/UpdateNumberState</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>示例</th></tr><tr><td>userid (工号)</td><td>51218</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "错误信息",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "12cb829bdd8643398170fdeea53ea4b7",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "13125436034"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 5.XB 用户绑定▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_11"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/GetCallNumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>是否必填</th><th>备注</th><th>示例</th></tr><tr><td>xbid(绑定 id)</td><td>是</td><td>没有传 0</td><td>1</td></tr><tr><td>userid (工号)</td><td>是</td><td><b>必填</b></td><td>51218</td></tr><tr><td>Mapclassid (回调使用)</td><td>是</td><td><b>必填</b></td><td>1</td></tr><tr><td>Mapid(回调使用)</td><td>是</td><td><b>必填</b></td><td>2</td></tr><tr><td>Contactmapclassid(回调使用)</td><td>是</td><td>没有传 0</td><td>3</td></tr><tr><td>Contactid(回调使用)</td><td>是</td><td>没有传 0</td><td>4</td></tr><tr><td>Mobile(用户真实号码)</td><td>是</td><td><b>必填</b></td><td>15104293448</td></tr><tr><td>expiration(绑定时长，单位: s）</td><td>否</td><td>不需要, 默认 120</td><td>0</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败,<p>DataBody 中返回传入的手机号。)</p></td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "绑定失败错误信息",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
       "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功, DataBody 中返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
"RequestId": "e30c4403e66f4181a871a0ba67b912bb",
"ResultCode": 2000,
"ResultMsg": "SUCCESS",
"IsEncrypt": 0,
"DataCount": 1,
"PageSize": 1,
"PageIndex": 1,
"DataBody": [
{
"phone": "16559504908",
"callbackId": xbid
}
],
"EncDataBody": ""
}</pre></td></tr></tbody></table>

### 6. 更新号码状态▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_12"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/UpdateNumberState</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td>① private_number (隐私号)<p>② state (号码状态 字典: 1527)</p><table class="wikitable"><tbody><tr><th>参数</th><th>示例</th></tr><tr><td>private_number (隐私号)</td><td>13125447274</td></tr><tr><td>state (号码状态 字典: 1527)</td><td>0</td></tr></tbody></table></td></tr><tr><td>返回结果 (成功, DataBody 中返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs bash">    "RequestId": "bfa15c18b90544e082f7ad5d5548cb0c",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "True"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 7.(RMQ=173)B 号码黑名单▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_13"><tbody><tr><th>名称</th><th>说明</th><th>申请内容 (示例)</th></tr><tr><td>队列名称</td><td>队列英文名称</td><td>service_exchange1_SetBlackNumber</td></tr><tr><td>队列描述</td><td>队列描述内容</td><td>隐私号设置黑名单 (马里消费)</td></tr><tr><td>业务类型</td><td>业务类别, 根据业务选择</td><td>8: 服务_交换 1</td></tr><tr><td>生产方</td><td>生产方开发者</td><td>潘多</td></tr><tr><td>消费方</td><td>消费方开发者</td><td>马里</td></tr><tr><td>业务对接人</td><td>业务负责开发者</td><td>马里</td></tr><tr><td>推送并发数</td><td>并发推送站点的数量</td><td>10</td></tr><tr><td>请求方式</td><td>消费站点访问方式</td><td>POST</td></tr><tr><td>推送超时时间</td><td>Post 请求超时时间</td><td>默认 120 秒</td></tr><tr><td>业务负责人</td><td>项目经理</td><td>王树羽</td></tr><tr><td>接口地址</td><td></td><td>家里地址: http://webapi-thethirdpart2020.517jiali.cn/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/SetBlackNumber<p>线上地址: http://webapi-thethirdpart2020.517api.cn/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/SetBlackNumber</p></td></tr><tr><td>发送消息格式</td><td>生产消息的格式</td><td><pre class="hljs bash">{
	"platId": 平台(1-, 2-,3-阿里云),
	"private_number": "1347011****",
	"action": "(add/delete)添加/删除",
	"userid": "74705",
	"type": "(黑名单类型[字典:1535] 0-呼出 1-呼入)"
}</pre></td></tr><tr><td>申请日期</td><td>提交任务的日期</td><td>2021.8.27</td></tr></tbody></table>

### 8. 换绑 A 号码▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_14"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/ChangeBindANumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td>① userId<p>② private_number (隐私号)</p><p>③ telA</p><table class="wikitable"><tbody><tr><th>参数</th><th>示例</th></tr><tr><td>userId(工号)</td><td></td></tr><tr><td>private_number (隐私号)</td><td></td></tr><tr><td>telA(A 号码需保持与 Mis 系统一致)</td><td></td></tr></tbody></table></td></tr><tr><td>返回结果</td><td>ResultCode=2000 成功, 其他失败</td></tr></tbody></table>

### 9. 释放小号▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_15"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/ReleaseTelX</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td>① userId<p>② private_number (隐私号)</p><table class="wikitable"><tbody><tr><th>参数</th></tr><tr><td>userId(工号)</td></tr><tr><td>private_number (隐私号)</td></tr></tbody></table></td></tr><tr><td>返回结果</td><td>ResultCode=2000 成功, 其他失败</td></tr></tbody></table>

### 10. 指定 A 号码绑号▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_16"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/BindAxNumberByUserPhone</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>类型</th><th>示例</th></tr><tr><td>userid (工号)</td><td>int</td><td>51218</td></tr><tr><td>userPhone(绑定 A 号码)</td><td>string</td><td>138****4056</td></tr><tr><td>regionid (区域 ID)</td><td>int</td><td>1</td></tr><tr><td>private_number (隐私号)</td><td>string</td><td>13125447274</td></tr><tr><td>addUser</td><td>int</td><td>74705</td></tr><tr><td>lastUser</td><td>int</td><td>74705</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "当前号码状态为[2]，无法绑定！",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "dd3ef6e7d3b04510bc58d0b9633afe5e",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 11. 临时故障绑定接口▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_17"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/TemporaryBindNumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><b>如果填写参数，则处理对应的数据，否则处理全部。</b><table class="wikitable"><tbody><tr><th>参数</th><th>是否必填</th><th>类型</th><th>示例</th></tr><tr><td>userid (工号)</td><td>选填</td><td>int</td><td>51218</td></tr><tr><td>private_number (隐私号)</td><td>选填</td><td>string</td><td>13125447274</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "当前号码状态为[2]，无法绑定！",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "dd3ef6e7d3b04510bc58d0b9633afe5e",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 12. 临时故障解绑 - 只修改状态不推送阿里▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_18"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/TemporaryUnBindNumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><b>如果填写参数，则处理对应的数据，否则处理全部。</b><table class="wikitable"><tbody><tr><th>参数</th><th>是否必填</th><th>类型</th><th>示例</th></tr><tr><td>userid (工号)</td><td>选填</td><td>int</td><td>51218</td></tr><tr><td>private_number (隐私号)</td><td>选填</td><td>string</td><td>13125447274</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "当前号码状态为[2]，无法绑定！",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "dd3ef6e7d3b04510bc58d0b9633afe5e",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 13. 临时故障解绑 - 推送所有绑定状态 = 5 的数据到阿里解绑 AX。▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_19"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>地址</td><td>/mangoapi/s4011_NumberProtection_hub.Data/PrivateNumberApiController/TemporaryUnBindNumberToAli</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>类型</th><th>示例</th></tr><tr><td>userid (工号)</td><td>int</td><td>51218</td></tr><tr><td>regionid (区域 ID)</td><td>int</td><td>1</td></tr><tr><td>private_number (隐私号)</td><td>string</td><td>13125447274</td></tr><tr><td>addUser</td><td>int</td><td>74705</td></tr><tr><td>lastUser</td><td>int</td><td>74705</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "d4a0130d4d1b4b919e917b0064d7ac4f",
    "ResultCode": 5000,
    "ResultMsg": "当前号码状态为[2]，无法绑定！",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 0,
    "PageSize": 0,
    "PageIndex": 0,
    "DataBody": [
        
    ],
    "EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
    "RequestId": "dd3ef6e7d3b04510bc58d0b9633afe5e",
    "ResultCode": 2000,
    "ResultMsg": "SUCCESS",
    "DebugMsg": "",
    "IsEncrypt": 0,
    "DataCount": 1,
    "PageSize": 1,
    "PageIndex": 1,
    "DataBody": [
        "16559504909"
    ],
    "EncDataBody": ""
}</pre></td></tr></tbody></table>

### 14. (MQID=175) 小号话务单回调推送 mq 写看电话日志▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_20"><tbody><tr><th>名称</th><th>说明</th><th>申请内容 (示例)</th></tr><tr><td>队列名称</td><td>队列英文名称</td><td>house_exchange1_GetPhoneWriteLog</td></tr><tr><td>队列描述</td><td>队列描述内容</td><td>看电话写日志</td></tr><tr><td>业务类型</td><td>业务类别, 根据业务选择</td><td>房源_交换 1</td></tr><tr><td>生产方</td><td>生产方开发者</td><td>马里</td></tr><tr><td>消费方</td><td>消费方开发者</td><td>张宜新</td></tr><tr><td>业务对接人</td><td>业务负责开发者</td><td>马里</td></tr><tr><td>推送并发数</td><td>并发推送站点的数量</td><td>1</td></tr><tr><td>请求方式</td><td>消费站点访问方式</td><td>POST</td></tr><tr><td>推送超时时间</td><td>Post 请求超时时间</td><td>默认 120 秒</td></tr><tr><td>业务负责人</td><td>项目经理</td><td>王树羽</td></tr><tr><td>接口地址</td><td></td><td>家里地址: http://misapi2020.517jiali.cn/mangoapi/b1032_DingTalkIM_2021.Data/TimeLimitMessageApiController/ReSendCardAction<p>线上地址: http://misapi2020.517api.cn/mangoapi/b1032_DingTalkIM_2021.Data/TimeLimitMessageApiController/ReSendCardAction</p></td></tr><tr><td>发送消息格式</td><td>生产消息的格式</td><td><pre class="hljs css">{
    user:员工编号,	
    houseid:房源id
}</pre></td></tr><tr><td>申请日期</td><td>提交任务的日期</td><td>2021.10.12</td></tr></tbody></table>

### 15. (MQID=176) 小号添加员工历史手机号码▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_21"><tbody><tr><th>名称</th><th>说明</th><th>申请内容 (示例)</th></tr><tr><td>队列名称</td><td>队列英文名称</td><td>house_exchange1_SaleCallPhoneNumberPool</td></tr><tr><td>队列描述</td><td>队列描述内容</td><td>小号添加员工历史手机号码</td></tr><tr><td>业务类型</td><td>业务类别, 根据业务选择</td><td>房源_交换 1</td></tr><tr><td>生产方</td><td>生产方开发者</td><td>王佳豪</td></tr><tr><td>消费方</td><td>消费方开发者</td><td>马里</td></tr><tr><td>业务对接人</td><td>业务负责开发者</td><td>马里</td></tr><tr><td>推送并发数</td><td>并发推送站点的数量</td><td>5</td></tr><tr><td>请求方式</td><td>消费站点访问方式</td><td>POST</td></tr><tr><td>推送超时时间</td><td>Post 请求超时时间</td><td>默认 120 秒</td></tr><tr><td>业务负责人</td><td>项目经理</td><td>王树羽</td></tr><tr><td>接口地址</td><td></td><td>家里地址: 暂无<p>线上地址: 暂无</p></td></tr><tr><td>发送消息格式</td><td>生产消息的格式</td><td><pre class="hljs json">{
    "userId": "员工编号",
    "newPhone": "13812345678",
    "oldPhone": "13998765432",
    "operatorUser:": "操作人编号"
}</pre></td></tr><tr><td>申请日期</td><td>提交任务的日期</td><td>2021.10.18</td></tr></tbody></table>

### 16. 绑定小号 by 平台▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_22"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>域名</td><td>https://misapi2020.517api.cn/</td></tr><tr><td>地址</td><td>/mangoapi/b3520_User_PrivacyNumber.Data/PrivateNumber_ax/BindAxByplatform?userId=51218&amp;platformID=3</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>类型</th><th>示例</th></tr><tr><td>userId (工号)</td><td>int</td><td>51218</td></tr><tr><td>platformID (小号平台)</td><td>int</td><td>1 - 东信 2 - 玖云 3 - 阿里云</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
	"ResultCode": 5000,
	"ResultMsg": "您存在绑定的小号,不能再绑定新的小号",
	"DataBody": [
		false
	]
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
	"ResultCode": 2000,
	"ResultMsg": "小号分配成功:16522726940",
	"DataBody": [
		true
	]
}</pre></td></tr></tbody></table>

### 17. 分配临时号码▼

<table class="wikitable" wiki_title_2="title_6" wiki_title_3="title_23"><tbody><tr><th>名称</th><th>说明</th></tr><tr><td>域名</td><td>https://misapi2020.517api.cn/</td></tr><tr><td>地址</td><td>/mangoapi/b3520_User_PrivacyNumber.Data/PrivateNumber_ax/UserBindLinShiNumber</td></tr><tr><td>类型</td><td>Get</td></tr><tr><td>参数</td><td><table class="wikitable"><tbody><tr><th>参数</th><th>类型</th><th>示例</th></tr><tr><td>userId (工号)</td><td>int</td><td>51218</td></tr><tr><td>platformID (小号平台)</td><td>int</td><td>1 - 东信 2 - 玖云 3 - 阿里云</td></tr></tbody></table></td></tr><tr><td>返回结果 (失败)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
"RequestId": "UI51218X0129105506899X92845",
"ResultCode": 5000,
"ResultMsg": "内部错误[FAIL-5000-该用户[51218]已经有故障绑定,不能再注册新的小号.]",
"IsEncrypt": 0,
"DataCount": 0,
"PageSize": 0,
"PageIndex": 0,
"DataBody": [],
"EncDataBody": ""
}</pre></td></tr><tr><td>返回结果 (成功，DataBody 返回隐私号)</td><td><i class="btnCopyCodeButton"></i><pre class="hljs json">{
"RequestId": "UI51218X0129105506899X92845",
"ResultCode": 2000,
"ResultMsg": "SUCCESS",
"IsEncrypt": 0,
"DataCount": 1,
"PageSize": 1,
"PageIndex": 1,
"DataBody": [
1
],
"EncDataBody": ""
}</pre></td></tr></tbody></table>

redis 相关▼⇊
----------

### 1. 查询用户小号▼

```
//查询
var rModel = new ClassMapDataNameModel(){ ClassId = 4011, MapId = 1,DataName = "PrivateNumber_user_axs" };
var obj = RedisBusinessHelper.GetHash<HubRedisHelperModel_AXS>(rModel,CommonFrame.userid.ToString()); 

{ "xNumber": "17038012595","bindType": 0 }
```