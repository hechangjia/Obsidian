---
title: "WebDAV - 维基百科，自由的百科全书"
source: "https://zh.wikipedia.org/wiki/WebDAV"
author:
  - "[[维基媒体项目贡献者]]"
published: 2010-11-05
created: 2025-02-20
description:
tags:
  - "clippings"
---
<table><caption>WebDAV</caption><tbody><tr><td colspan="2"><a href="https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE">网络传输协议</a></td></tr><tr><th scope="row"><a href="https://zh.wikipedia.org/wiki/OSI%E6%A8%A1%E5%9E%8B">OSI层级</a></th><td><a href="https://zh.wikipedia.org/wiki/%E5%BA%94%E7%94%A8%E5%B1%82">应用层</a></td></tr><tr><th scope="row"><a href="https://zh.wikipedia.org/wiki/%E9%80%A3%E6%8E%A5%E5%9F%A0">端口</a></th><td>80、443</td></tr><tr><th scope="row"><a href="https://zh.wikipedia.org/wiki/Request_for_Comments">RFC</a></th><td><a href="https://zh.wikipedia.org/wiki/RFC">RFC</a>&nbsp;<a href="https://datatracker.ietf.org/doc/html/rfc2518">2518</a>、<a href="https://zh.wikipedia.org/wiki/RFC">RFC</a>&nbsp;<a href="https://datatracker.ietf.org/doc/html/rfc4918">4918</a></td></tr><tr><th scope="row">网站</th><td><span><a href="http://www.webdav.org/">www<wbr>.webdav<wbr>.org</a></span></td></tr></tbody></table>

**基于Web的分布式编写和版本控制**（英语：**W**eb-based **D**istributed **A**uthoring and **V**ersioning，缩写：**WebDAV**）是[超文本传输协议](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE "超文本传输协议")（HTTP）的扩展，有利于用户间协同编辑和管理存储在[万维网](https://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91 "万维网")服务器文档。WebDAV由[互联网工程任务组](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%B7%A5%E7%A8%8B%E4%BB%BB%E5%8A%A1%E7%BB%84 "互联网工程任务组")的工作组在[RFC](https://zh.wikipedia.org/wiki/RFC "RFC") [4918](https://datatracker.ietf.org/doc/html/rfc4918 "rfc:4918")中定义。

WebDAV协议为用户在[服务器](https://zh.wikipedia.org/wiki/%E6%9C%8D%E5%8A%A1%E5%99%A8 "服务器")上创建、更改和移动文档提供了一个框架。WebDAV协议最重要的功能包括作者或修改日期等属性的维护、[命名空间](https://zh.wikipedia.org/wiki/%E5%91%BD%E5%90%8D%E7%A9%BA%E9%97%B4 "命名空间")管理、集合和覆盖保护。为属性维护所提供的功能包括创建、删除和查询文件信息等；**命名空间管理**处理在服务器名称空间内复制和移动网页的能力；**集合**（Collections）处理各种资源的创建、删除和列举；**覆盖保护**处理与锁定文件相关的问题。WebDAV协议利用[TLS](https://zh.wikipedia.org/wiki/TLS "TLS")、[HTTP摘要认证](https://zh.wikipedia.org/wiki/HTTP%E6%91%98%E8%A6%81%E8%AE%A4%E8%AF%81 "HTTP摘要认证")、[XML](https://zh.wikipedia.org/wiki/XML "XML")等技术来满足这些需求。

许多现代[操作系统](https://zh.wikipedia.org/wiki/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F "操作系统")为WebDAV提供了内置的客户端支持。

WebDAV创始于1996年，当时[加州大学尔湾分校](https://zh.wikipedia.org/wiki/%E5%8A%A0%E5%B7%9E%E5%A4%A7%E5%AD%B8%E7%88%BE%E7%81%A3%E5%88%86%E6%A0%A1 "加州大学尔湾分校")博士毕业生[Jim Whitehead](https://zh.wikipedia.org/w/index.php?title=Jim_Whitehead&action=edit&redlink=1 "Jim Whitehead（页面不存在）")与[W3C](https://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91%E8%81%94%E7%9B%9F "万维网联盟")共同主办了两场会议，与感兴趣的人讨论万维网上的分布式创作问题。[^1][^2] [蒂姆·伯纳斯-李](https://zh.wikipedia.org/wiki/%E8%92%82%E5%A7%86%C2%B7%E4%BC%AF%E7%BA%B3%E6%96%AF-%E6%9D%8E "蒂姆·伯纳斯-李")对网络的最初看法是涉及阅读和写作的[介质](https://zh.wikipedia.org/wiki/%E5%84%B2%E5%AD%98%E8%A3%9D%E7%BD%AE "存储设备")。事实上，Berners Lee的第一个[Web浏览器](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%A1%B5%E6%B5%8F%E8%A7%88%E5%99%A8 "网页浏览器")（[WorldWideWeb](https://zh.wikipedia.org/wiki/WorldWideWeb "WorldWideWeb")），可以查看和编辑[网页](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%A0%81 "网页")；但是，随着网络的成长，对大多数用户来说成为了只读介质。怀特黑德和其他志同道合的人想超越这个限制。[^3]

W3C会议决定成立一个[IETF](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%B7%A5%E7%A8%8B%E4%BB%BB%E5%8A%A1%E7%BB%84 "互联网工程任务组")工作组，因为新的工作将导致对[HTTP](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE "超文本传输协议")进行扩展，而当时IETF已经开始对HTTP进行标准化。

随着协议的工作开始，很明显，同时处理分布式创作和[版本控制](https://zh.wikipedia.org/wiki/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6 "版本控制")将涉及太多的工作，并且任务将不得不分开。WebDAV小组专注于分布式创作，将版本控制留作以后研究。（[Delta-V扩展](https://zh.wikipedia.org/wiki/#%E6%93%B4%E5%85%85%E8%88%87%E8%A1%8D%E7%94%9F)后来加入了版本控制功能 – 请参阅下面的扩展与派生章节。）

在[互联网工程指导组](https://zh.wikipedia.org/w/index.php?title=%E4%BA%92%E8%81%94%E7%BD%91%E5%B7%A5%E7%A8%8B%E6%8C%87%E5%AF%BC%E7%BB%84&action=edit&redlink=1 "互联网工程指导组（页面不存在）")（IESG）接受[RFC](https://zh.wikipedia.org/wiki/RFC "RFC") [2518](https://datatracker.ietf.org/doc/html/rfc2518 "rfc:2518")的增量更新之后，WebDAV工作组在2007年3月结束了其工作。当时还没有完成的其他扩展，比如BIND方法，已经由其独立作者独立于正式工作组完成。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/WebDAV_collaborative_authoring.png/500px-WebDAV_collaborative_authoring.png)

兼容HTTP服务器中的WebDAV[协同编辑](https://zh.wikipedia.org/wiki/%E5%8D%8F%E5%90%8C%E7%BC%96%E8%BE%91 "协同编辑")

WebDAV扩展了[request](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE#%E8%AF%B7%E6%B1%82%E4%BF%A1%E6%81%AF "超文本传输协议")方法所允许的标准HTTP谓词和HTTP头。增加的谓词包括：

COPY

将资源从一个[URI](https://zh.wikipedia.org/wiki/%E7%B5%B1%E4%B8%80%E8%B3%87%E6%BA%90%E6%A8%99%E8%AA%8C%E7%AC%A6 "统一资源标志符")复制到另一个URI

LOCK

[锁定](https://zh.wikipedia.org/wiki/%E9%94%81_\(%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%A7%91%E5%AD%A6\) "锁 (计算机科学)")一个资源。WebDAV支持共享锁和互斥锁。

MKCOL

创建集合（即[目录](https://zh.wikipedia.org/wiki/%E7%9B%AE%E5%BD%95_\(%E6%96%87%E4%BB%B6%E7%B3%BB%E7%BB%9F\) "目录 (文件系统)")）

MOVE

将资源从一个[URI](https://zh.wikipedia.org/wiki/%E7%B5%B1%E4%B8%80%E8%B3%87%E6%BA%90%E6%A8%99%E8%AA%8C%E7%AC%A6 "统一资源标志符")移动到另一个URI

PROPFIND

从[Web资源](https://zh.wikipedia.org/w/index.php?title=Web%E8%B5%84%E6%BA%90&action=edit&redlink=1 "Web资源（页面不存在）")中检索以[XML](https://zh.wikipedia.org/wiki/XML "XML")格式存储的属性。它也被[重载](https://zh.wikipedia.org/wiki/%E5%87%BD%E6%95%B0%E9%87%8D%E8%BD%BD "函数重载")，以允许一个检索远程系统的集合结构（也叫目录层次结构）。

PROPPATCH

在单个[原子性动作](https://zh.wikipedia.org/w/index.php?title=%E5%8E%9F%E5%AD%90%E6%80%A7%E6%8F%90%E4%BA%A4&action=edit&redlink=1 "原子性提交（页面不存在）")中更改和删除资源的多个属性

UNLOCK

解除资源的锁定

- [Apache HTTP Server](https://zh.wikipedia.org/wiki/Apache_HTTP_Server "Apache HTTP Server")提供基于[davfs](https://zh.wikipedia.org/w/index.php?title=Davfs&action=edit&redlink=1 "Davfs（页面不存在）")和[Apache Subversion (svn)](https://zh.wikipedia.org/wiki/Subversion "Subversion")的WebDAV模块。
- [微软](https://zh.wikipedia.org/wiki/%E5%BE%AE%E8%BD%AF "微软")的[IIS](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%9A%9B%E7%B6%B2%E8%B7%AF%E8%B3%87%E8%A8%8A%E6%9C%8D%E5%8B%99 "互联网信息服务")也有WebDAV模块。
- [Nginx](https://zh.wikipedia.org/wiki/Nginx "Nginx")有非常有限的可选WebDAV模块[^4]和第三方模块[^5]
- [SabreDAV](https://zh.wikipedia.org/w/index.php?title=SabreDAV&action=edit&redlink=1 "SabreDAV（页面不存在）")是一个PHP应用程序，可以在Apache或Nginx上使用，代替它们的捆绑模块
- [Nextcloud](https://zh.wikipedia.org/wiki/Nextcloud "Nextcloud")是一个云存储PHP应用程序，它提供了完整的WebDAV支持[^6]
- [lighttpd](https://zh.wikipedia.org/wiki/Lighttpd "Lighttpd")有一个可选的WebDAV模块[^7]

- [Git](https://zh.wikipedia.org/wiki/Git "Git")支持写入HTTP远端，尽管需要特殊服务器支持的HTTP的“智能”Git协议已经成为WebDAV的首选协议
- [Linux](https://zh.wikipedia.org/wiki/Linux "Linux")通过[GVfs](https://zh.wikipedia.org/wiki/GVfs "GVfs")（包括[GNOME文件](https://zh.wikipedia.org/wiki/Nautilus%E6%AA%94%E6%A1%88%E7%80%8F%E8%A6%BD%E5%99%A8 "Nautilus文件浏览器")）或通过[KIO](https://zh.wikipedia.org/wiki/KIO "KIO")（包括[Konqueror](https://zh.wikipedia.org/wiki/Konqueror "Konqueror")和[Dolphin](https://zh.wikipedia.org/wiki/Dolphin_\(%E8%BB%9F%E9%AB%94\) "Dolphin (软件)")）支持WebDAV
- [macOS](https://zh.wikipedia.org/wiki/MacOS "MacOS")对[CalDAV](https://zh.wikipedia.org/w/index.php?title=CalDAV&action=edit&redlink=1 "CalDAV（页面不存在）")和[CardDAV](https://zh.wikipedia.org/wiki/CardDAV "CardDAV")有原生支持，其设计基于WebDAV
- [Microsoft Windows](https://zh.wikipedia.org/wiki/Microsoft_Windows "Microsoft Windows")，其[Explorer](https://zh.wikipedia.org/wiki/%E6%AA%94%E6%A1%88%E7%B8%BD%E7%AE%A1 "资源管理器")有原生支持
- [Microsoft Office](https://zh.wikipedia.org/wiki/Microsoft_Office "Microsoft Office")

针对版本控制，Web版本控制与配置管理工作小组下的Delta-V协议增加了资源修订追踪功能，并发表于[RFC](https://zh.wikipedia.org/wiki/RFC "RFC") [3253](https://datatracker.ietf.org/doc/html/rfc3253 "rfc:3253")中。

在搜索和定位方面，WebDAV Search specification接手DAV Searching and Locating（DASL）工作小组的工作，并于2008年11月以[RFC](https://zh.wikipedia.org/wiki/RFC "RFC") [5323](https://datatracker.ietf.org/doc/html/rfc5323 "rfc:5323")发布。[^8]

针对日历，[CalDAV](https://zh.wikipedia.org/w/index.php?title=CalDAV&action=edit&redlink=1 "CalDAV（页面不存在）")是一种允许透过WebDAV访问日历的通信协议。CalDAV将日历事件模拟为iCalendar格式的HTTP资源，并将包含事件的日历以WebDAV集合模拟。

对于组群软件而言，GroupDAV是WebDAV的变体，允许客户端/服务器[组群软件](https://zh.wikipedia.org/wiki/%E7%BE%A4%E7%B5%84%E8%BB%9F%E9%AB%94 "组群软件")系统存储和获取对象，例如日历和通讯录项目，而非网页。

针对MS Exchange的互操作性，WebDAV可用于读取/更新/删除信箱或公用文件夹中的项目。适用于Exchange的WebDAV已由微软扩展至可处理消息资料。Exchange Server 2000、2003和2007版本支持WebDAV。但是Exchange 2010已停止支持WebDAV[^9]，改用Exchange Web Services（EWS），这是一种以[SOAP](https://zh.wikipedia.org/wiki/SOAP "SOAP")/[XML](https://zh.wikipedia.org/wiki/XML "XML")为基础的[API](https://zh.wikipedia.org/wiki/API "API")。

- [内容管理](https://zh.wikipedia.org/wiki/%E5%85%A7%E5%AE%B9%E7%AE%A1%E7%90%86 "内容管理")
- [WebDAV软件比较](https://zh.wikipedia.org/wiki/WebDAV%E8%BD%AF%E4%BB%B6%E6%AF%94%E8%BE%83 "WebDAV软件比较")
- [集群文件系统](https://zh.wikipedia.org/wiki/%E9%9B%86%E7%BE%A4%E6%96%87%E4%BB%B6%E7%B3%BB%E7%BB%9F "集群文件系统")
- [CardDAV](https://zh.wikipedia.org/wiki/CardDAV "CardDAV")
- [数据可移植性](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%8F%AF%E7%A7%BB%E6%A4%8D%E6%80%A7 "数据可移植性")

[^1]: [Proposed agenda for San Mateo Meeting](http://lists.w3.org/Archives/Public/w3c-dist-auth/1996AprJun/0002.html). 1996 \[2018-02-03\]. （原始内容[存档](https://web.archive.org/web/20201029060418/https://lists.w3.org/Archives/Public/w3c-dist-auth/1996AprJun/0002.html)于2020-10-29）.

[^2]: [Brief mtg. summary](http://lists.w3.org/Archives/Public/w3c-dist-auth/1996JulSep/0095.html). 1996 \[2018-02-03\]. （原始内容[存档](https://web.archive.org/web/20160527134700/http://lists.w3.org/Archives/Public/w3c-dist-auth/1996JulSep/0095.html)于2016-05-27）.

[^3]: [Re: Updated agenda](http://lists.w3.org/Archives/Public/w3c-dist-auth/1996JulSep/0001.html). \[2018-02-03\]. （原始内容[存档](https://web.archive.org/web/20160527134652/http://lists.w3.org/Archives/Public/w3c-dist-auth/1996JulSep/0001.html)于2016-05-27）.

[^4]: [Module ngx\_http\_dav\_module](http://nginx.org/en/docs/http/ngx_http_dav_module.html). nginx website. \[15 July 2016\]. （原始内容[存档](https://web.archive.org/web/20201006184153/http://nginx.org/en/docs/http/ngx_http_dav_module.html)于2020-10-06）.

[^5]: [Module nginx-dav-ext-module](https://github.com/arut/nginx-dav-ext-module/). github.com. \[2 August 2016\]. （原始内容[存档](https://web.archive.org/web/20201031112559/https://github.com/arut/nginx-dav-ext-module)于2020-10-31）.

[^6]: [Nextcloud 11 User Manual](https://docs.nextcloud.com/server/11/user_manual/files/access_webdav.html). nextcloud.com. \[19 September 2017\]. （原始内容[存档](https://web.archive.org/web/20170521154143/https://docs.nextcloud.com/server/11/user_manual/files/access_webdav.html)于2017-05-21）.

[^7]: [lighttpd mod webdav](http://redmine.lighttpd.net/projects/1/wiki/Docs_ModWebDAV). （原始内容[存档](https://web.archive.org/web/20200927074625/https://redmine.lighttpd.net/projects/1/wiki/Docs_ModWebDAV)于2020-09-27）.

[^8]: Reschke, J. F.; Reddy, S.; Davis, J.; Babich, A. [Web Distributed Authoring and Versioning (WebDAV) SEARCH](https://www.greenbytes.de/tech/webdav/draft-reschke-webdav-search-latest.html). www.greenbytes.de. 2008-11 \[2024-08-21\]. （原始内容[存档](https://web.archive.org/web/20241130090337/https://www.greenbytes.de/tech/webdav/draft-reschke-webdav-search-latest.html)于2024-11-30） （英语）.

[^9]: Archiveddocs. [Discontinued Features: Exchange 2010 Help](https://learn.microsoft.com/en-us/previous-versions/office/exchange-server-2010/aa998911\(v=exchg.141\)?redirectedfrom=MSDN). learn.microsoft.com. 2014-07-23 \[2024-08-21\]. （原始内容[存档](https://web.archive.org/web/20240821082528/https://learn.microsoft.com/en-us/previous-versions/office/exchange-server-2010/aa998911\(v=exchg.141\)?redirectedfrom=MSDN)于2024-08-21） （美国英语）.

- [WebDAV Resources](https://web.archive.org/web/20120626092812/http://webdav.org/)
- [Davfs2 project](http://savannah.nongnu.org/projects/davfs2) （[页面存档备份](https://web.archive.org/web/20201111221014/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [Fusedav project](http://0pointer.de/lennart/projects/fusedav)（[页面存档备份](https://web.archive.org/web/20090203160814/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [WebDAV Apache modules](https://httpd.apache.org/docs/2.4/mod/mod_dav.html) （[页面存档备份](https://web.archive.org/web/20210118230021/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [WebDAV Drive Mapping Tool](https://www.drivehq.com/help/features/webdav.aspx)