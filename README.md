# GoodSourceCodes

--
作者：auxten
链接：https://www.zhihu.com/question/19880598/answer/30448002
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

碰巧读过之前大家提到的一些开源项目
网络编程：
  redis是单线程异步网络编程的范例: https://github.com/antirez/redis
  nginx是多进程网络编程的巅峰，模块化:https://github.com/nginx
  memcached虽然是C++，但是C style的，多线程网络编程的巅峰数据结构:https://github.com/memcached/memcached

数据库：SQLite，数据理论的范例。注意要去读非合并源文件版的（为了方便编译器优化，有个单文件版的）:http://www.sqlite.org/
大杂烩类型：
  Coreutils - GNU core utilities，大多数Linux系统命令的实现:https://www.gnu.org/software/coreutils/coreutils.html
  Python源代码（CPython，注意不是Cython），多少次遇到百思不得其解的问题，我都是去看看Python是怎么封装成简单可靠的接口的，比如我回答的Linux TCP connect with Select() fails at testserver，还有怎么实现一个可靠的带自定义超时的connect()，你都可以从Python源码里找到答案。
  Varnish，大名鼎鼎的Varnish缓存服务器，每个线程处理一个连接的架构。但这货的配置文件处理方面做的很优秀，想要研究DSL的同学可以看一下。 
  
找虐：
  The BIRD Internet Routing Daemon Project，宏玩得飞起:http://bird.network.cz/
  Kernel，很容易挫伤初学者积极性
  glibc、ssh，这类程序都是上个世纪的大神们的作品，从编程风格和整体架构上都属于晦涩难懂的，代码风格也是现代编程所不推荐的，建议初学者远离。

--
Source:https://my.oschina.net/zhoukuo/blog/335788#OSC_h3_2

 代码阅读——十个C开源项目
1. Webbench
Webbench是一个在linux下使用的非常简单的网站压测工具。它使用fork()模拟多个客户端同时访问我们设定的URL，测试网站在压力下工作的性能，最多可以模拟3万个并发连接去测试网站的负载能力。Webbench使用C语言编写, 代码实在太简洁，源码加起来不到600行。下载链接：http://home.tiscali.cz/~cz210552/webbench.html

2. CMockery
cmockery是google发布的用于C单元测试的一个轻量级的框架。它很小巧，对其他开源包没有依赖，对被测试代码侵入性小。cmockery的源代码行数不到3K，你阅读一下will_return和mock的源代码就一目了然了。

主要特点：
免费且开源，google提供技术支持；
轻量级的框架，使测试更加快速简单；
避免使用复杂的编译器特性，对老版本的编译器来讲，兼容性好;
并不强制要求待测代码必须依赖C99标准，这一特性对许多嵌入式系统的开发很有用
下载链接：http://code.google.com/p/cmockery/downloads/list

3. Libev
libev是一个开源的事件驱动库，基于epoll，kqueue等OS提供的基础设施。其以高效出名，它可以将IO事件，定时器，和信号统一起来，统一放在事件处理这一套框架下处理。基于Reactor模式，效率较高，并且代码精简（4.15版本8000多行），是学习事件驱动编程的很好的资源。下载链接：http://software.schmorp.de/pkg/libev.html

4. Memcached
Memcached 是一个高性能的分布式内存对象缓存系统，用于动态Web应用以减轻数据库负载。它通过在内存中缓存数据和对象来减少读取数据库的次数，从而提供动态数据库驱动网站的速度。Memcached 基于一个存储键/值对的 hashmap。Memcached-1.4.7的代码量还是可以接受的，只有10K行左右。下载地址：http://memcached.org/

5. Lua
Lua很棒，Lua是巴西人发明的，这些都令我不爽，但是还不至于脸红，最多眼红。
让我脸红的是Lua的源代码，百分之一百的ANSI C，一点都不掺杂。在任何支持ANSI C编译器的平台上都可以轻松编译通过。我试过，真是一点废话都没有。Lua的代码数量足够小，5.1.4仅仅1.5W行，去掉空白行和注释估计能到1W行。下载地址：http://www.lua.org/

6. SQLite
SQLite是一个开源的嵌入式关系数据库，实现自包容、零配置、支持事务的SQL数据库引擎。 其特点是高度便携、使用方便、结构紧凑、高效、可靠。足够小，大致3万行C代码，250K。 下载地址：http://www.sqlite.org/ 。

7. Redis
Redis是一个用ANSI C 编写的开源数据结构服务器。Redis的代码非常容易读懂，代码写的很整洁，并且代码量相对较小（4.5w行，其实也不是很小）。大部分都是单线程的，几乎不依赖其它库。下载地址：redis.io/

8. Nginx
Nginx("engine x") 是一个高性能的 HTTP 和反向代理服务器，也是一个 IMAP/POP3/SMTP 代理服务器 。Nginx 是由 Igor Sysoev 为俄罗斯访问量第二的Rambler.ru站点开发的，它已经在该站点运行超过四年多了。Igor 将源代码以类BSD许可证的形式发布。自Nginx 发布四年来，Nginx 已经因为它的稳定性、丰富的功能集、 示例配置文件和低系统资源的消耗而闻名了。

nginx的优秀除了体现在程序结构以及代码风格上，nginx的源码组织也同样简洁明了，目录结构层次结构清晰，值得我们去学习。下载地址：http://nginx.org/en/download.html。

9. UNIXv6
UNIX V6 的内核源代码包括设备驱动程序在内 约有1 万行，这个数量的源代码，初学者是能够充分理解的。有一种说法是一个人所能理解的代码量上限为1 万行，UNIX V6的内核源代码从数量上看正好在这个范围之内。看到这里，大家是不是也有“如果只有1万行的话没准儿我也能学会”的想法呢？

另一方面，最近的操作系统，例如Linux 最新版的内核源代码据说超过了1000 万行。就算不是初学者，想完全理解全部代码基本上也是不可能的。下载地址：http://minnie.tuhs.org/cgi-bin/utree.pl?file=V6

10. NETBSD
NetBSD是一个免费的，具有高度移植性的 UNIX-like 操作系统，是现行可移植平台最多的操作系统，可以在许多平台上执行，从 64bit alpha 服务器到手持设备和嵌入式设备。NetBSD计划的口号是："Of course it runs NetBSD"。它设计简洁，代码规范，拥有众多先进特性，使得它在业界和学术界广受好评。由于简洁的设计和先进的特征，使得它在生产和研究方面，都有卓越的表现，而且它也有受使用者支持的完整的源代码。许多程序都可以很容易地通过NetBSD Packages Collection获得。下载地址：http://www.netbsd.org/

 
