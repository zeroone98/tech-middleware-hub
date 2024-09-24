MySQL 和 PostgreSQL 提供许多相同的特性和功能 - 但是这两个关系数据库管理系统 (RDBMS) 之间存在不容忽视的关键差异。 

如果您不熟悉这些差异，这里有一个快速简便的概述：

- MySQL 是管理只读命令的首选。当需要并发时，它不是首选。
- PostgreSQL 适合用于管理读写操作、大型数据集和复杂查询。但它不适合用于只读操作。 
- MySQL 提供的功能比 PostgreSQL 少，但这使得 MySQL 更轻、更稳定、处理速度更快——尤其是在只读查询方面。
- PostgreSQL 从一开始就构建为符合[ACID 标准](https://www.techtarget.com/searchdatamanagement/definition/ACID)，并且在需要并发事务（MVCC）时是最佳的，但在只读操作方面速度较慢且不太稳定。 
- MySQL 与多种不同类型的数据存储引擎高度兼容。而 PostgreSQL 与多种不同的 NoSQL 格式高度兼容。 

在本指南中，我们简要介绍了每个数据库系统的历史和概述。我们还重点介绍了 MySQL 和 PostgreSQL 之间的关键差异和相似之处，以及哪种系统最适合不同的用例。 

## 快速参考表：MySQL 与 PostgreSQL 表

| **特点与特性**      | **MySQL**                                         | **PostgreSQL**                  |
| ------------------- | ------------------------------------------------- | ------------------------------- |
| **ORDBMS 与 RDBMS** | 关系数据库管理系统 (RDBMS)                        | 对象关系数据库管理系统 (ORDBMS) |
| **符合 ACID 标准**  | 大多数引擎都符合 ACID 标准，但 MyISAM 不支持 ACID | 全面支持                        |
| **备份与恢复**      | 提供备份和恢复功能                                | 以其高效的备份和恢复功能而闻名  |
| **跨平台**          | 是的                                              | 在基于 UNIX 的系统上最佳        |
| **扩展和插件**      | 众多可用                                          | 以可扩展性而闻名，例如 PostGIS  |
| **外键**            | 支持，但 MyISAM 不支持                            | 全力支持。                      |
| **索引技术**        | 有多种可用技术                                    | 提供 GIN 和 GiST 等高级类型     |
| **SQL 数据类型**    | 有标准类型                                        | 更加多样化，包括数组、hstore    |
| **存储过程**        | 支持                                              | 更高级的 PL/pgSQL 语言          |
| **触发器**          | 支持                                              | 灵活的多语言支持                |
| **视图**            | 支持                                              | 提供物化视图                    |



| **使用案例**     | **MySQL**                            | **PostgreSQL**                               |
| ---------------- | ------------------------------------ | -------------------------------------------- |
| **Web 应用程序** | 因其速度和可靠性而广受好评           | 越来越受欢迎，尤其适用于复杂的用例           |
| **空间数据库**   | 基本空间函数                         | PostGIS 扩展提供的高级空间功能               |
| **企业系统**     | 适用于多种企业应用程序               | 因其稳健性和可扩展性而被使用                 |
| **数据仓库**     | 用于数据仓库，但可能需要定制解决方案 | 对具有高级数据类型的数据仓库提供更强大的支持 |
| **嵌入式系统**   | 提供轻量级版本                       | 不太常见但有可能                             |

**请注意，这两个数据库都具有更多功能，本表仅涵盖其中一部分。另外，请记住，选择正确的数据库取决于项目的具体要求和特点。*

### 目录

- [基础知识：PostgreSQL 和 MySQL 的概述](javascript:;)
- [相同，相同，但不同：MySQL 和 PostgreSQL 有哪些共同点（以及它们的独特之处）？](javascript:;)
- [何时使用 MySQL 而不是 PostgreSQL 以及反之亦然？](javascript:;)
- [PostgreSQL 用户支持与 MySQL 用户支持](javascript:;)
- [PostgreSQL 速度与 MySQL 速度：哪个更快？](javascript:;)
- [PostgreSQL 和 MySQL 支持哪些编程语言？](javascript:;)
- [PostgreSQL 和 MySQL 适用于哪些操作系统？](javascript:;)
- [PostgreSQL 索引与 MySQL 索引：它们如何索引？](javascript:;)
- [PostgreSQL 和 MySQL 的编码有何不同？](javascript:;)
- [自 2020 年以来最新的 PostgreSQL 和 MySQL 开发](javascript:;)
- [文章摘要](javascript:;)



![整合](https://www.integrate.io/blog/assets/newsletter_background3-ec05df8cdb824036e4034685f5cc237aaf577410a5378014841269d1ee418457.svg)![整合](https://www.integrate.io/blog/assets/newsletter_background4-00aec3bbf26de11da4884971acb50c9b64305317bf6d992158cb091e1cd37e04.svg)

### 现代数据团队的统一堆栈

##### 获得个性化平台演示以及与解决方案工程师进行 30 分钟问答环节

获取现场演示





## 基础知识：PostgreSQL 和 MySQL 的概述

让我们从 PostgreSQL 和 MySQL 的基本概述和历史开始。如果您已经了解基础知识，请跳过本节。如果您是初学者，本节将帮助您快速入门。 

### **什么是 MySQL？**

MySQL 是世界上最常用的关系数据库管理系统 (RDBMS)。2023年，这款开源 RDBMS 在[开发人员中的使用率排名第二，以向组织提供快速、可靠、稳定、安全和可扩展的数据管理而闻名。](https://www.statista.com/statistics/794187/united-states-developer-survey-most-wanted-used-database-technologies/)

MySQL 是可扩展 Web 应用程序的首选。它是 LAMP 堆栈的标准配置。LAMP 堆栈在 Web 开发中非常流行。它是一个开源 Web 应用程序堆栈，包括 Linux、Apache HTTP Server、MySQL 和 PHP。此外，最流行的内容管理系统（包括 Drupal、Joomla 和 WordPress）都使用 MySQL。在这方面，您几乎随处可见 MySQL。

以下是 MySQL 的一些定义特征： 

- **与 PostgreSQL 相比，可扩展性和灵活性较差：**这使得 MySQL 保持轻量、高效和稳定——尤其是对于 Web 应用程序而言。 
- **强大的数据安全功能：**包括多个用于访问控制的加密选项。
- **支持多种数据类型：**包括数字、日期/时间、字符、JSON、布尔值和枚举。PostgreSQL 提供更多支持。 
- **支持多种索引：**包括 B 树、哈希、R 树和倒排索引。 
- **大容量交易：**管理大量读/写交易的能力。 
- **获得优质支持：**获得庞大而活跃的支持社区以及来自许多不同供应商的付费支持。 
- **开源：** MySQL 是免费且开源的。
- **由 Oracle 维护：** Oracle 拥有并维护 MySQL，并提供带有附加服务、专有插件、扩展和用户支持的 MySQL 高级版本。 
- **支持社区：**有一个专门的志愿者社区来帮助解决问题。
- **稳定可靠：** 用户同意，只要您保持数据库“整洁”并定期维护， [MySQL 就是一种非常稳定的 RDBMS 。](https://www.itcentralstation.com/products/mysql-stability)
- **MVCC 功能：** MySQL 提供[多版本并发控制](https://dev.mysql.com/doc/refman/8.0/en/innodb-multi-versioning.html?utm_source=xp&utm_medium=blog&utm_campaign=content)（MVCC）功能。
- **频繁更新：** MySQL 受益于频繁更新，提供新功能和安全性改进。最近一次更新是2023 年 1 月 24 日的 [8.0.32 版。](https://blogs.oracle.com/mysql/post/announcing-mysql-server-8032)
- **4.4 星评级：** MySQL 在 G2Crowd 上的 1,606 条评论中获得了[4.4 星](https://www.g2.com/products/mysql/reviews/mysql-review-1775714)评级（满分 5 星）。 

### MySQL 的历史

MySQL 的历史可以追溯到[1995 年](https://en.wikipedia.org/wiki/MySQL)。如今已成传奇的瑞典计算机科学家[Michael “Monty” Widenius](https://en.wikipedia.org/wiki/Michael_Widenius)和他的团队将 MySQL 作为一个开源平台发布。Widenius 和他的公司 (MySQL AB) 将 MySQL 打造为一个稳定、可靠且价格合理的数据库管理系统。 

2008 年，Sun Microsystems 收购了 MySQL AB 和 MySQL。2010 年，Oracle Corporation 收购了 Sun Microsystems 和 MySQL。这些收购引发了 MySQL 社区的担忧。如果新东家停止开发和维护 MySQL 会怎样？ 

为了确保高性能开源关系数据库的可用性，Michael Widenius 于 2009 年分叉 MySQL 以创建 MariaDB。MySQL 和 MariaDB 在 2023 年仍然非常受欢迎。然而，MySQL 是迄今为止在开发人员和企业中使用最广泛的。 

开发人员经常使用 MySQL 和 PHP 来创建动态网站和应用程序。由于 MySQL 能够快速高效地处理大型数据集，因此它也受到需要存储、访问和理解大量数据的公司欢迎。最后，MySQL 相对容易学习，并为大型企业提供可扩展性选项。 

如今，[Facebook](https://engineering.fb.com/data-infrastructure/mysql/)、Twitter、Netflix 和其他大型科技公司都依赖 MySQL 来运行其关键任务系统。其他使用 MySQL 的知名组织包括： 

- Facebook
- 谷歌
- Flickr
- GitHub
- 美国宇航局
- Netflix
- Spotify
- 特斯拉 
- 叽叽喳喳
- 优步
- 美国海军
- 微信
- 维基百科
- YouTube
- 捷步
- Zendesk

有关 Integrate.io 原生 MySQL 连接器的更多信息，请访问我们的[集成页面](https://www.integrate.io/integrations/mysql/)。

![缩略图](https://cdn.filestackcontent.com/auto_image//compress/cache=expiry:max/C9D22JSTeL4Of3UZWqAt)

MySQL 徽标

### 什么是 PostgreSQL？

PostgreSQL 是一个开源的对象关系数据库管理系统 (ORDBMS)。经过 30 多年的积极开发，PostgreSQL 具有“目录驱动”操作以及比其他数据库管理系统更多的功能和能力。这使得它具有高度的[可扩展性](https://www.postgresql.org/docs/9.0/extend-how.html)和可定制性，以适应最广泛的用例。 

由于[PostgreSQL](https://www.postgresql.org/)足够灵活，可以管理独特的数据库场景，因此它已成为 MySQL 无法处理的复杂、大量数据操作的首选解决方案。PostgreSQL 不仅存储有关表和列的信息。它还允许您定义数据类型、索引类型和函数语言。

以下是 PostgreSQL 的一些定义特征：

- **对象关系数据库管理系统 (ORDBMS)：**这些是结合了关系和面向对象特性的混合数据库系统。它们最适合管理结构化和复杂数据类型。
- **可定制：**它支持用户定义的函数和存储过程，并且包含比其他数据库系统更多的功能和能力。您可以通过开发插件来定制 PostgreSQL，以使其满足您的要求。PostgreSQL 还允许您合并使用其他编程语言（如 C/C++、Java 等）编写的自定义函数。
- **各种各样的数据类型：**包括整数、字符串、日期、时间戳和二进制对象。 
- **可扩展：**它以易于扩展而闻名，使其成为企业应用程序和 Web 应用程序的绝佳选择。
- **符合 ACID 标准：**这使其能够实现高度并发事务并提供 NoSQL 支持。MySQL 自 8.0 版起就提供 NoSQL 支持。
- **开源：** PostgreSQL 是免费且开源的。PostgreSQL 具有自由开源许可证，允许您以任何方式使用、修改和分发 DBMS。
- **频繁更新：**最近的稳定 PostgreSQL 更新是[2023 年 8 月的 15.4 版](https://www.postgresql.org/docs/release/15.4)。
- **MVCC 功能：** PostgreSQL 是第一个实现[多版本并发控制](https://www.postgresql.org/docs/7.1/mvcc.html)(MVCC) 功能的 DBMS，该功能允许并发事务。这允许多个用户同时对同一条记录进行更改。 
- **庞大而活跃的支持社区： PostgreSQL 拥有一个由开发人员和志愿者组成的忠诚社区。该社区通过**[PostgreSQL 全球开发小组](https://www.postgresql.org/)持续维护和更新 PostgreSQL 。此外还提供私人第三方支持服务。
- **4.4 星评级：**在 G2Crowd 上的 598 条评论中，获得[4.4 星](https://www.g2.com/products/postgresql/reviews/postgresql-review-2188535)评价（满分 5 星）。

PostgreSQL因成为当时增长最快的 DBMS 而[荣获 2020 年度数据库奖](https://db-engines.com/en/blog_post/85)。然而，PostgreSQL 和 MySQL在 2021 年和 2022 年均[被 Snowflake 击败。](https://db-engines.com/en/blog/DBMS+of+the+year)

![缩略图](https://cdn.filestackcontent.com/auto_image//compress/cache=expiry:max/5jMzlb00Q5aWiupWHhPD)

PostgreSQL 徽标

### PostgreSQL 的历史

PostgreSQL 的历史可以追溯到 20 世纪 80 年代末。如今已成传奇的计算机科学家[Michael Stonebraker和他在](https://en.wikipedia.org/wiki/Michael_Stonebraker)[加州大学伯克利分校](https://www.postgresql.org/about/)的团队于 1989 年发布了 PostgreSQL。他们以 Ingres 关系数据库系统为蓝本。

[PostgreSQL 于1989 年](https://en.wikipedia.org/wiki/PostgreSQL)发布后，由于其与事务、触发器、存储过程和视图相关的新特性和功能而迅速流行起来。如今，PostgreSQL 支持多种语言，包括 Python 和 JavaScript。它还非常注重安全性和可扩展性，使其成为大容量应用程序的理想选择。

使用 PostgreSQL 的著名组织包括： 

- 苹果
- 生物制药
- 思科
- Debian
- Etsy
- Facebook
- 富士通
- 互联网数据库
- Instagram
- 麦金塔世界
- 红帽
- Skype
- Spotify
- 太阳微系统公司
- 雅虎

Integrate.io 提供原生 PostgreSQL 连接器。请访问我们的[集成页面](https://www.integrate.io/integrations/postgresql/)了解更多信息。

**相关阅读：** [5 个用于无缝数据集成的 Postgres ETL 工具](https://www.integrate.io/blog/postgres-etl-tools/)



## 相同，相同，但不同：MySQL 和 PostgreSQL 有哪些共同点（以及它们的独特之处）？

MySQL 和 PostgreSQL 之间仍然有很大差异 — 但随着每个新版本的发布，这些数据库系统的特性和功能之间的差距正在缩小。本节中的所有要点都强调了 MySQL 和 PostgreSQL 之间的相似之处。

以下相似之处始终存在：

- **庞大且有用的社区支持：**两个数据库系统都提供庞大且有用的社区支持。当需要更高级别的支持时，私人服务提供商可以提供专业的支持包。
- **SQL（结构化查询语言）：** MySQL 和 PostgreSQL 使用 SQL（结构化查询语言），这是数据管理系统中最流行的语言。SQL 提供了一种用于查询和连接表的简单格式，并且SQL 的基础知识对于不懂技术的团队成员来说 [很容易学习。](https://www.sqlbot.co/blog/sqlzoo)

近年来，MySQL 开始提供更多可扩展性功能和其他功能，这些功能以前是 PostgreSQL 独有的。但是，MySQL 提供这些功能并不意味着它与 PostgreSQL 相同：

- **通用表表达式 (CTE)：** CTE 是一个临时结果集，用户可以在 SELECT、INSERT、UPDATE 或 DELETE 语句中引用它。
- **地理信息系统 (GIS) 和空间参考系统 (SRS)：** GIS 捕获、存储和分析空间和地理数据。SRS 定义了一个基于坐标的系统来定位空间中的位置。PostgreSQL 通过 PostGIS 扩展提供了此功能。MySQL 内置了此功能。
- **JSON 兼容性：** MySQL 现在支持 JavaScript 对象表示法 (JSON)，可用于存储和传输数据。不过，PostgreSQL 仍然是唯一支持 JSONB 的平台。JSONB 是二进制版本，可删除重复键并消除多余的空格。
- **多版本并发控制 (MVCC)：** MVCC 允许多个事务同时访问同一数据而不会发生冲突。通常，PostgreSQL 以更高效地处理 MVCC 操作而闻名。 
- **窗口函数：**这些函数可以对与当前行相关的一组表行进行计算。 

PostgreSQL 还开始提供以前只属于 MySQL 的特性和功能。同样，PostgreSQL 提供的特性并不意味着它与 MySQL 相同：

- **声明式分区：**这可以将表细分为更小、更易于管理的表，但仍将其视为一个表。PostgreSQL 10 通过简化表分区添加了此功能。MySQL 通过 CREATE TABLE 和 PARTITION BY 语法提供此功能。
- **逻辑复制：**这允许根据插入、更新和删除等事件复制数据更改。 
- **半同步复制：**此复制方法仅在至少一个从属服务器确认收到数据后才考虑提交事务。MySQL 使用此功能来支持更好的数据完整性。PostgreSQL 现在通过外部工具提供此功能。 

### 您可能不会注意到的细微差别

MySQL 和 PostgreSQL 中的许多功能***似乎\*** 相同。然而，这只是表面上的情况。当你仔细观察时，你会发现细微的差异可能会成就或破坏你的用例。

- **ACID 特性：**两者都是符合 ACID 标准的系统。但是，某些 MySQL 存储引擎（如 MyISAM）不支持 ACID。如果您需要 MySQL 符合 ACID 标准，请尝试 InnoDB。
- **备份和恢复：**两者都提供备份和恢复功能。PostgreSQL 自带的备份和恢复工具以其高效率而闻名。
- **跨平台：** MySQL 和 PostgreSQL 都是跨平台解决方案。不过，PostgreSQL 以其在基于 UNIX 的系统上的性能优化特性而闻名。
- **扩展和插件：**两者都是可扩展的，并且有大量可用的扩展和插件。但 PostgreSQL 以其可扩展性而闻名，因为它拥有广泛的附加模块，例如 PostGIS 及其空间数据功能。
- **外键：**两者都允许外键约束。但是 MySQL 中的 MyISAM 存储引擎不允许。
- **索引：** PostgreSQL 和 MySQL 都支持不同的索引技术。不过，PostgreSQL 提供了一些 MySQL 所不具备的高级索引类型（如 GIN 和 GiST）。
- **标准 SQL 数据类型：** MySQL 和 PostgreSQL 均提供标准 SQL 数据类型（如 INTEGER 和 VARCHAR）。不过，PostgreSQL 支持更广泛的数据类型，包括数组和 hstore。
- **存储过程：**两者都支持存储过程。但是，与 MySQL 的常规语法相比，PostgreSQL 通过其 PL/pgSQL 语言提供更完整的支持。PL/pgSQL 语言允许 PostgreSQL 用户在开发存储过程时更具创造性，以适应其独特的用例。
- **触发器：**两者都支持使用触发器。但同样，PostgreSQL 在触发器方面更灵活，因为它允许您使用不同的语言编写触发器。
- **视图：**在这两种数据库中都可以创建视图。但是，PostgreSQL 提供物化视图。物化视图会缓存昂贵的、计算量大的查询的结果，允许您定期刷新结果。当您需要快速数据访问时，这很有用。



## 何时使用 MySQL 而不是 PostgreSQL（反之亦然）？

作为“功能丰富”的选择，PostgreSQL 受到开发人员的大力推崇。但 MySQL 的简单性、易用性和可靠性对于某些用例来说可能更有价值。在这方面，MySQL 和 PostgreSQL 在不同领域表现出色。

### 何时使用 MySQL

在以下情况下您可能需要使用 MySQL。

**当您需要存储引擎灵活性时。MySQL**允许您从一系列存储引擎中进行选择。这使您可以灵活地集成来自各种表类型的数据。MySQL 8.0[支持以下存储引擎](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html?utm_source=xp&utm_medium=blog&utm_campaign=content)：

- 数据库引擎InnoDB
- 数据库管理系统
- 记忆
- CSV
- 档案
- 黑洞
- NDB/NDBCLUSTER
- 合并
- 联合
- 例子

**当您需要速度和可靠性时。**通过不包含某些 SQL 功能，MySQL 保持轻量级以优先考虑速度和可靠性。当涉及高度并发、只读功能时，MySQL 的速度尤其明显。这使得它成为某些商业智能目的的绝佳选择。但是，如果您需要在高负载下运行大量复杂查询，PostgreSQL 可能是更好的选择。 

**当您需要服务器优化选项时。MySQL**通过调整 sort_buffer_size、read_buffer_size、max_allowed_packet 等变量，提供了各种调整和优化 MySQL 服务器的选项。 

**当您想要最易于使用的数据库系统时。MySQL**的流行意味着很容易找到具有 MySQL 经验的数据库管理员。用户还报告说，它更容易设置，不需要像其他 DBMS 解决方案那样进行大量微调。[本教程](https://www.wikihow.com/Create-a-Database-in-MySQL)展示了初学者设置第一个 MySQL 数据库是多么容易。此外，许多前端（如 Adminer、MySQL Workbench、HeidiSQL 和 dbForge Studio）为 MySQL 添加了图形界面，提供了用户友好的体验**。**

**当您需要云就绪的 DBMS 时。MySQL**是云就绪的，许多云平台都提供 MySQL 服务，他们会收费安装和维护您的 MySQL 数据库。 

**当需要多版本并发控制 (MVCC) 和 ACID 合规性，并且您可以容忍损坏表的风险时。**当前版本的 MySQL 的默认引擎是 InnoDB。这增加了 MVCC 和 ACID 合规性。但是，由于其 MyISAM 表格式，MySQL 上的 InnoDB 仍然可能出现损坏表的问题。此外，选择其他引擎可能会导致失去 MVCC 和 ACID 合规性。

**当您的开发团队需要一个简单的解决方案时。PostgreSQL**需要更高水平的技能，并非所有开发人员都能胜任使用它的任务，或者他们只是没有足够的培训和经验。要获得更简单的解决方案，请选择 MySQL。

### 何时使用 PostgreSQL

在以下情况下您可能需要使用 PostgreSQL。

**当您需要 ORDBMS 时，而不仅仅是 RDBMS。PostgreSQL**是一种对象关系编程语言 (ORDBMS)，因此它就像 C++ 一样充当面向对象编程和关系/过程编程之间的桥梁。这允许您定义对象和表继承，从而转换为更复杂的数据结构。当您处理与严格关系模型不相符的数据时，ORDBMS 非常有用。 

**当您需要执行复杂的读写操作时。**当您在使用需要验证的数据时需要执行复杂的读写操作时，PostgreSQL 是一个绝佳的选择。但是，ORDBMS 在处理只读操作时可能会遇到速度减慢的情况。

**当您需要最佳的 NoSQL 支持和对最多样化数据类型的支持时。PostgreSQL**是 NoSQL 功能的热门选择。它原生支持[丰富的数据类型](https://www.postgresql.org/docs/8.2/datatype.html)，包括[JSON](https://www.postgresql.org/docs/10/datatype-json.html)、[hstore](https://www.postgresql.org/docs/9.0/hstore.html)和[XML](https://www.postgresql.org/docs/9.1/datatype-xml.html)。您还可以定义原始数据类型并设置自定义函数。

**当您需要管理超大型数据库时。PostgreSQL**不会限制数据库的大小。据[Adjust.com](http://adjust.com/)的一位数据库管理员称，他的公司使用 PostgreSQL 管理“[大约 4PB [PB 级\] 的数据](https://www.quora.com/What-is-the-largest-production-deployment-of-PostgreSQL-for-online-use/answer/Chris-Travers-4)”。也就是 4,000 TB！他还表示，他们的“环境每秒使用 PostgreSQL 处理（然后记录）来自外部的 10 万到 25 万个请求”。

**当您需要最佳的多版本并发控制 (MVCC) 时。MVCC**是企业选择 PostgreSQL 的最重要原因之一。MVCC 允许不同的读取器和写入器同时与 PostgreSQL 数据库交互和管理该数据库。这样就无需每次有人需要与数据交互时都使用读写锁，从而提高效率。MVCC 通过“快照隔离”实现这一点。快照表示某一时刻的数据状态。尽管最新版本的 MySQL 提供 MYVCC，但 PostgreSQL 通常最适合 MVCC。

**当您需要最高级别的 ACID 合规性时。PostgreSQL**可防止数据损坏并在事务级别保持数据的完整性。在此处详细了解[PostgreSQL 的 ACID 合规性的价值](https://people.apache.org/~jim/NewArchitect/webtech/2001/09/jepson/index.html)。 

**当您的开发团队拥有 PostgreSQL 技能时。PostgreSQL**是一种较难学习的数据库，因此请确保您的团队能够应对挑战。 

**如果您想要 REST API 支持。PostgreSQL**提供 PostgREST REST API。根据 PostgreSQL 网站，“PostgREST 是一个独立的 Web 服务器，可将您的 PostgreSQL 数据库直接转换为 RESTful API。数据库中的结构约束和权限决定了 API 端点和操作。”顺便说一句，如果您想要 MySQL 的类似功能，还有其他工具和框架可用于为 MySQL 数据库创建 RESTful API，例如[DreamFactory](https://blog.dreamfactory.com/restful-api-and-microservices-the-differences-and-how-they-work-together/?__hstc=114807128.dd4dcbdffcb1f7e71441508f66e27068.1727148603663.1727148603663.1727148603663.1&__hssc=114807128.1.1727148603663&__hsfp=2227708583)。

**相关阅读**：[Redshift 与 Postgres：主要区别](https://www.integrate.io/blog/redshift-vs-postgres/)



## PostgreSQL 用户支持与 MySQL 用户支持

谈到 PostgreSQL 与 MySQL 的用户支持，这两个数据库系统都有乐于助人的社区为用户提供支持。您还可以找到来自第三方提供商的付费支持。让我们看看它们之间的比较。 

### MySQL 用户支持

作为一个开源项目，MySQL 拥有庞大的志愿者社区，随时准备提供免费的支持和建议。寻求此类支持的最佳方式是在[MySQL](https://www.mysql.com/)网站上。

[G2Crowd 上的评论](https://www.g2.com/products/mysql/reviews#reviews)显示，MySQL 提供了很多免费的在线社区支持，这要归功于愿意解决常见问题的用户。此外，Oracle 随时提供付费支持。 

### PostgreSQL 用户支持

与 MySQL 一样，PostgreSQL 拥有庞大的志愿者社区，他们在[IRC](https://www.postgresql.org/community/irc/)和以下[邮件列表](https://www.postgresql.org/list/)上为用户提供免费建议。您还可以通过[第三方提供商](https://www.postgresql.org/support/professional_support/)购买付费支持，还可以搜索[此处的](https://www.postgresql.org/docs/)PostgreSQL 手册和书籍。 

至于 PostgreSQL 社区与 MySQL 的比较，一些[G2Crowd 评论者](https://www.g2.com/products/mysql/reviews#reviews)表示 PostgreSQL 社区论坛的响应速度不如 MySQL 论坛。话虽如此，PostgreSQL 问题可能比 MySQL 问题更复杂。这可能是有时更难获得所需 PostgreSQL 答案的原因。 

**相关阅读**：[MongoDB 与 MySQL：性能和速度的详细比较](https://www.integrate.io/blog/mongodb-vs-mysql/)



## PostgreSQL 速度与 MySQL 速度：哪个更快？

PostgreSQL 和 MySQL 都以速度快而闻名。但很难说哪个更快，因为数据库针对不同的用例进行了优化。 

经过深入测试，[Windows Skills](http://wskills.blogspot.com/2007/01/postgresql-vs-mysql-benchmark.html)说 MySQL 更快，而[Benchw](http://benchw.sourceforge.net/benchw_results_open3.html)说 PostgreSQL 更快。总的来说，PostgreSQL 在处理海量数据集、复杂查询和读写操作时更快。MySQL 在只读命令方面更快。 



## PostgreSQL 和 MySQL 支持哪些编程语言？

PostgreSQL 和 MySQL 并不总是支持相同的编程语言。下表显示了每个数据库系统支持的语言。

| **编程语言**   | **PostgreSQL**      | **MySQL** |
| -------------- | ------------------- | --------- |
| **C/C++**      | 支持                | 支持      |
| **德尔福**     | 支持                | 支持      |
| **Erlang**     | 有限支持            | 有限支持  |
| **去**         | 支持（通过 lib/pq） | 支持      |
| **Java**       | 支持                | 支持      |
| **JavaScript** | 支持                | 支持      |
| **Lisp**       | 有限支持            | 有限支持  |
| **。网**       | 支持（通过 Npgsql） | 支持      |
| **Node.js**    | 支持                | 支持      |
| **Perl**       | 支持                | 支持      |
| **PHP**        | 支持                | 支持      |
| **Python**     | 支持                | 支持      |
| **R**          | 有限支持            | 有限支持  |
| **Tcl**        | 支持                | 有限支持  |

**请注意，此表为一般概述。实际支持可能因相应语言和数据库的特定库或驱动程序而异。“有限支持”意味着成熟库可能较少，或者社区不如这些语言活跃。*



## PostgreSQL 和 MySQL 适用于哪些操作系统？

在操作系统兼容性方面，MySQL 和 PostgreSQL 都提供了最广泛的兼容性。在大多数情况下，这些数据库系统将与您的操作系统兼容，如下表所示。通常，这些系统的首选操作系统是 Linux。 

| **操作系统**                                                 | **PostgreSQL** | **MySQL**              |
| ------------------------------------------------------------ | -------------- | ---------------------- |
| **微软 Windows**                                             | 支持           | 支持                   |
| **苹果系统**                                                 | 支持           | 支持                   |
| **Linux（通用/一般）**                                       | 支持           | 支持                   |
| **Linux（Ubuntu）**                                          | 支持           | 支持                   |
| **Linux（Debian）**                                          | 支持           | 支持                   |
| **Linux（SUSE Linux 企业服务器和 OpenSuSE）**                | 支持           | 支持                   |
| **Linux（Red Hat Enterprises、CentOS、Fedora、Scientific、Oracle）** | 支持           | 支持                   |
| **Oracle Solaris**                                           | 支持           | 支持                   |
| **Fedora（注：也是Red Hat家族的一部分）**                    | 支持           | 支持                   |
| **BSD（FreeBSD、OpenBSD）**                                  | 支持           | 支持（主要是 FreeBSD） |
| **开源构建**                                                 | 支持           | 支持                   |



## PostgreSQL 索引与 MySQL 索引：它们如何索引？

索引可在处理大型数据表时加快 SQL 查询速度，从而提高数据库性能。如果不对数据库进行索引，查询对于 DBMS 来说会很慢且繁重。PostgreSQL 和 MySQL 提供不同的索引选项。

### MySQL 索引类型

MySQL 支持以下索引类型：

- 存储在 B 树上的索引，例如 INDEX、FULLTEXT、PRIMARY KEY 和 UNIQUE。
- 存储在 R 树上的索引，例如在空间数据类型上找到的索引。
- 使用 FULLTEXT 索引时的哈希索引和倒排列表。

### PostgreSQL 索引类型

PostgreSQL 支持以下索引类型：

- 哈希索引和 B 树索引。
- 部分索引仅组织表的一部分信息。
- 表达式索引是根据表达式函数（而不是列值）创建的索引。



## PostgreSQL 和 MySQL 的编码有何不同？

以下是使用 PostgreSQL 和 MySQL 编码的三个差异。

### 1. 区分大小写

MySQL 不区分大小写。编写查询时，您不需要将数据库中出现的字符串大写。PostgreSQL 区分大小写。您需要将数据库中出现的字符串完全大写，否则查询将失败。

### 2. 默认字符集和字符串

对于某些版本的 MySQL，需要将字符集和字符串转换为 UTF-8。对于 PostgreSQL，无需将字符集和字符串转换为 UTF-8。此外，PostgreSQL 不允许使用 UTF-8 语法。

### 3. IF 和 IFNULL 与 CASE 语句

在 MySQL 中，使用 IF 和 IFNULL 语句完全没问题。在 PostgreSQL 中，IF 和 IFNULL 语句不起作用。您需要改用 CASE 语句。 



## 自 2020 年以来最新的 PostgreSQL 和 MySQL 开发

MySQL 和 PostgreSQL 不断改进并发布新版本。在过去三年中，这两个数据库系统都发布了一些重要的改进，以实现：

- 提高复杂查询的性能
- 增强的安全功能
- 增强可扩展性
- 支持新数据类型和函数

### MySQL 的最新进展

MySQL 8.0的发布引入了以下新功能：

- 空间数据类型，因此 MySQL 可以存储和查询空间数据，例如点、线和多边形。
- JSON 支持，因此 MySQL 可以存储和查询 JSON 数据。
- 通过添加新的查询优化器和改进对并行查询的支持来提高性能。

MySQL 还发布了 InnoDB Cluster，为关键任务应用程序提供高可用性和可扩展性。最后，MySQL 发布了 X DevAPI，以提供与数据库交互的统一方式，无论使用何种编程语言。

### PostgreSQL 的最新发展

PostgreSQL 14 的发布引入了以下新功能：

- 逻辑复制使得 PostgreSQL 能够以高效且可扩展的方式将数据从一个数据库复制到另一个数据库。
- 表分区，因此 PostgreSQL 可以将大表分成更小、更易于管理的分区。
- 通过包括新的 JSON 数据类型和改进对 JSON 函数的支持在内的性能改进，提高了 JSON 数据的性能。
- PostgreSQL TimescaleDB的发布，这是一个支持时间序列数据的开源扩展，对金融交易和物联网应用很有用。



## 文章摘要

总之，在 PostgreSQL 和 MySQL 之间进行选择通常归结为以下问题：

- 您是否需要一个功能丰富、能够处理复杂查询和海量数据库的数据库？Postgres 凭借其可扩展性可能是您的选择。
- 您是否需要一个更简单、易于设置和管理、快速、可靠且易于理解的数据库？MySQL 是理想的选择。 

以下是 PostgreSQL 和 MySQL 之间的关键差异的最终总结：

### 数据类型支持

- PostgreSQL 拥有更广泛的内置数据类型，包括对数组、hstore、JSON 和几何类型的支持。这使得 PostgreSQL 对于需要这些数据类型的某些类型的应用程序来说更加通用。
- MySQL 的数据类型较为有限，但它为地理信息系统 (GIS) 数据提供了空间扩展。

### SQL 合规性

- PostgreSQL 以其高度的 SQL 标准合规性而闻名。它严格遵守 SQL 标准，这可以使不同平台和应用程序的行为更加可预测。
- MySQL 传统上与严格的 SQL 标准存在一些偏差，但随着新版本的推出，它已经提高了其合规性并继续弥合差距。

### 表现

- MySQL 历来受到读取密集型工作负载的青睐，这使其成为 Web 应用程序和网站的热门选择。
- PostgreSQL 的架构更适合复杂的查询和分析工作负载。它在需要高级 SQL 功能的场景中表现良好。

### 复制和高可用性

- MySQL 提供各种复制方法，包括主从复制，但其一些集群解决方案可能需要第三方工具。
- PostgreSQL 提供内置的同步复制，这使得实现高可用性和数据冗余变得更加容易。

### 全文搜索

- PostgreSQL 包含开箱即用的强大全文搜索功能，允许执行复杂的文本搜索操作。
- 虽然 MySQL 也支持全文搜索，但它可能需要额外的配置和外部引擎，如 InnoDB 或 MyISAM。

### 外键约束和触发器

- PostgreSQL 对外键约束和触发器有更高级的支持，使其成为需要复杂数据完整性和业务规则的应用程序的更好选择。
- MySQL 还支持外键约束和触发器，但从历史上看，对它们的执行不太严格。

### 许可

- PostgreSQL 和 MySQL 都是开源的，并且采用不同的许可证。PostgreSQL 通常使用 PostgreSQL 许可证，而 MySQL 过去采用 GNU 通用公共许可证 (GPL)，但现在也提供商业许可选项。

PostgreSQL 和 MySQL 都是功能强大的数据库，具有各自独特的功能和能力。在决定哪一个适合您的应用程序时，考虑所有这些因素非常重要。 