# 简介

<p align="center"><img width="650" src="../images/excelize.svg" alt="Excelize logo"></p>

<p align="center">
    <a href="https://travis-ci.org/360EntSecGroup-Skylar/excelize"><img src="https://travis-ci.org/360EntSecGroup-Skylar/excelize.svg?branch=master" alt="Build Status"></a>
    <a href="https://codecov.io/gh/360EntSecGroup-Skylar/excelize"><img src="https://codecov.io/gh/360EntSecGroup-Skylar/excelize/branch/master/graph/badge.svg" alt="Code Coverage"></a>
    <a href="https://goreportcard.com/report/github.com/360EntSecGroup-Skylar/excelize"><img src="https://goreportcard.com/badge/github.com/360EntSecGroup-Skylar/excelize" alt="Go Report Card"></a>
    <a href="https://pkg.go.dev/github.com/360EntSecGroup-Skylar/excelize/v2?tab=doc"><img src="https://img.shields.io/badge/go.dev-reference-007d9c?logo=go&logoColor=white" alt="go.dev"></a>
    <a href="https://opensource.org/licenses/BSD-3-Clause"><img src="https://img.shields.io/badge/license-bsd-orange.svg" alt="Licenses"></a>
    <a href="https://www.paypal.me/xuri"><img src="https://img.shields.io/badge/Donate-PayPal-green.svg" alt="Donate"></a>
</p>

Excelize 是 Go 语言编写的一个用来操作 Office Excel 文档类库，基于 ECMA-376 Office OpenXML 标准。可以使用它来读取、写入 XLSX 文件。相比较其他的开源类库，Excelize 支持写入原本带有图片(表)的文档，还支持向 Excel 中插入图片，并且在保存后不会丢失图表样式，可以应用在各种报表系统中。

- Source Code: [github.com/360EntSecGroup-Skylar/excelize](https://github.com/360EntSecGroup-Skylar/excelize)
- Issue: [github.com/360EntSecGroup-Skylar/excelize/issues](https://github.com/360EntSecGroup-Skylar/excelize/issues)
- go.dev: [pkg.go.dev/github.com/360EntSecGroup-Skylar/excelize/v2?tab=doc](https://pkg.go.dev/github.com/360EntSecGroup-Skylar/excelize/v2?tab=doc)
- 许可协议: [BSD 3-Clause](https://opensource.org/licenses/BSD-3-Clause)
- 当前版本: [v2.1.0](https://github.com/360EntSecGroup-Skylar/excelize/releases/latest)
- 文档更新: 2020年3月6日

## 项目使命

Excelize 的目标是创建并维护一个 Go 语言版本的 Excel 文档 API，以处理符合基于 Office Open XML（OOXML）标准的 xlsx 文件，借助 Excelize 您可以使用 Go 读取和写入 MS Excel 文件。

## 为什么要使用 Excelize

在一些情况下我们需要通过程序操作 Excel 文档，例如：打开读取已有 Excel 文档内容、创建新的 Excel 文档、基于已有文档（模版）生成新的 Excel 文档、向 Excel 文档中插入图片、图表和表格等元素，有时还需要跨平台实现这些操作。使用 Excelize 可以方便的满足上述需求。

## 项目荣誉

入选 2018 年开源中国码云最有价值开源项目 ([Gitee Most Valuable Project](https://gitee.com/xurime/excelize))

<p align="center"><img width="330" src="../images/gvp2018.jpg" alt="2018 年开源中国码云最有价值开源项目"></p>

## 知名用户

<a href="https://www.360.cn" title="奇虎 360 公司" target="_blank"><img width="165" src="../images/vendor/360@2x.png" alt="奇虎 360 公司"></a> <a href="https://www.baidu.com" title="百度" target="_blank"><img width="165" src="../images/vendor/baidu@2x.png" alt="百度"></a> [![合合信息](../images/vendor/ccint.com.png)](https://www.ccint.com) <a href="https://www.inke.cn" title="映客直播" target="_blank"><img width="165" src="../images/vendor/inke@2x.png" alt="映客直播"></a> <a href="https://www.meituan.com" title="美团点评" target="_blank"><img width="165" src="../images/vendor/meituan@2x.png" alt="美团点评"></a> <a href="https://www.163.com" title="网易" target="_blank"><img width="165" src="../images/vendor/netease@2x.png" alt="网易"></a> <a href="https://www.bilibili.com" title="哔哩哔哩" target="_blank"><img width="165" src="../images/vendor/bilibili@2x.png" alt="哔哩哔哩"></a> <a href="https://www.qianxin.com" title="奇安信集团" target="_blank"><img width="165" src="../images/vendor/qianxin.com@2x.png" alt="奇安信集团"></a> <a href="https://www.alibabagroup.com" title="阿里巴巴集团" target="_blank"><img width="165" src="../images/vendor/alibabagroup@2x.png" alt="阿里巴巴集团"></a> <a href="https://www.ele.me" title="饿了么" target="_blank"><img width="165" src="../images/vendor/ele.me@2x.png" alt="饿了么"></a> <a href="https://www.huifu.com" title="汇付天下" target="_blank"><img width="165" src="../images/vendor/huifu.com@2x.png" alt="汇付天下"></a> <a href="https://www.dodoca.com" title="点点客" target="_blank"><img width="165" src="../images/vendor/dodoca.com@2x.png" alt="点点客"></a> <a href="https://bytedance.com" title="字节跳动" target="_blank"><img width="165" src="../images/vendor/bytedance@2x.png" alt="字节跳动"></a> <a href="https://www.flashexpress.com" title="闪电快车" target="_blank"><img width="165" src="../images/vendor/flashexpress.com@2x.png" alt="闪电快车"></a> <a href="http://www.bigbaser.com" title="比格基地" target="_blank"><img width="165" src="../images/vendor/bigbaser.com@2x.png" alt="比格基地"></a> <a href="https://jimengio.com" title="积梦智能" target="_blank"><img width="165" src="../images/vendor/jimengio.com@2x.png" alt="积梦智能"></a>

如果您的公司或产品也在使用 Excelize，欢迎 <a href="mailto: xuri.me@gmail.com?Subject=Please add our company in Excelize Introduction page&amp;Body=Hello%2C%20this%20is%20%3Cyour%20name%3E%20from%20%3Cyour%20company%20name%3E.%0AWe%20are%20using%20Excelize%20and%20will%20be%20proud%20to%20add%20our%20company%20name%20to%20Excelize%20Introduction%20page.%0APlease%20see%20attachment%20for%20our%20logo.%20%3CBe%20sure%20to%20include%20logo%20in%20attachment%3E%0A%E4%BD%A0%E5%A5%BD%EF%BC%8C%E6%88%91%E6%98%AF%E3%80%90%E5%85%AC%E5%8F%B8%E5%90%8D%E7%A7%B0%E3%80%91%E7%9A%84%E3%80%90%E6%82%A8%E7%9A%84%E5%90%8D%E5%AD%97%E3%80%91%E3%80%82%0A%E6%88%91%E4%BB%AC%E5%85%AC%E5%8F%B8%E4%BD%BF%E7%94%A8%E4%BA%86%20Excelize%20%E5%B9%B6%E4%B8%94%E5%BE%88%E4%B9%90%E6%84%8F%E5%9C%A8%20Excelize%20%E7%9A%84%E2%80%9C%E4%BB%8B%E7%BB%8D%E2%80%9D%E9%A1%B5%E9%9D%A2%E5%8A%A0%E4%B8%8A%E6%88%91%E4%BB%AC%E5%85%AC%E5%8F%B8%E7%9A%84%20logo%E3%80%82%0A%E8%AF%B7%E5%9C%A8%E9%99%84%E4%BB%B6%E4%B8%AD%E6%9F%A5%E9%98%85%20logo%E3%80%82%E3%80%90%E8%AF%B7%E9%99%84%E4%B8%8A%20logo%20%E5%B9%B6%E5%8F%91%E9%80%81%E7%BB%99%20Excelize%E3%80%91" title="通过 E-mail 发送 Logo">发送 Logo</a> 给我们。

## 技术交流群

DingTalk Group ID: [`30047129`](https://qr.dingtalk.com/action/joingroup?code=v1,k1,2oHMIIOyvPcGezVdHJjsHwdZzzYNI6xs3Oww8uhlvCk=&_dt_no_comment=1&origin=11)
QQ Group ID: [`207895940`](https://jq.qq.com/?_wv=1027&k=5imdV9h)

<img width="400" src="./images/group@2x.png" alt="Excel 技术交流群">
