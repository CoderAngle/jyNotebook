### 什么是时间元组？

很多Python函数用一个元组装起来的9组数字处理时间:

| 序号 | 字段 | 值 |
| :--- | :--- | :--- |
| 0 | 4位数年 | 2008 |
| 1 | 月 | 1 到 12 |
| 2 | 日 | 1到31 |
| 3 | 小时 | 0到23 |
| 4 | 分钟 | 0到59 |
| 5 | 秒 | 0到61 \(60或61 是闰秒\) |
| 6 | 一周的第几日 | 0到6 \(0是周一\) |
| 7 | 一年的第几日 | 1到366 \(儒略历\) |
| 8 | 夏令时 | -1, 0, 1, -1是决定是否为夏令时的旗帜 |

上述也就是struct\_time元组。这种结构具有如下属性：

| 序号 | 属性 | 值 |
| :--- | :--- | :--- |
| 0 | tm\_year | 2008 |
| 1 | tm\_mon | 1 到 12 |
| 2 | tm\_mday | 1 到 31 |
| 3 | tm\_hour | 0 到 23 |
| 4 | tm\_min | 0 到 59 |
| 5 | tm\_sec | 0 到 61 \(60或61 是闰秒\) |
| 6 | tm\_wday | 0到6 \(0是周一\) |
| 7 | tm\_yday | 1 到 366\(儒略历\) |
| 8 | tm\_isdst | -1, 0, 1, -1是决定是否为夏令时的旗帜 |

### 常用用法

```
1.以元组方式返回本地当前时间
>>> time.localtime()
time.struct_time(tm_year=2018, tm_mon=10, tm_mday=11, tm_hour=17, tm_min=4, tm_sec=28, tm_wday=3, tm_yday=284, tm_isdst=0)

2.以元组方式返回格林威治时间
>>> time.gmtime()   
time.struct_time(tm_year=2018, tm_mon=10, tm_mday=11, tm_hour=9, tm_min=4, tm_sec=18, tm_wday=3, tm_yday=284, tm_isdst=0)

3.将元组时间转换为时间戳
>>> x = time.localtime()
>>> time.mktime(x)
1494232890.0
>>> time.mktime((2018, 9, 30, 9, 44, 31, 6, 273, 0))
1538271871.0

4.将元组时间转换为字符串格式时间
>>> x = time.localtime()
>>> time.strftime('%Y-%m-%d %H:%M:%S',x)
'2018-10-11 17:03:48'

5.将字符串格式时间转换为元组格式时间
>>> time.strptime('2017-05-08 17:03:12','%Y-%m-%d %H:%M:%S')
time.struct_time(tm_year=2017, tm_mon=5, tm_mday=8, tm_hour=17, tm_min=3, tm_sec=12, tm_wday=0, tm_yday=128, tm_isdst=-1)

6.元组格式时间转换为字符串格式时间
>>> time.asctime()
'Thu Oct 11 17:02:29 2018'
>>> x = time.localtime()
>>> time.asctime(x)
'Sun Sep 30 09:44:31 2018'
>>> time.asctime((2018, 9, 30, 9, 44, 31, 6, 273, 0))
'Sun Sep 30 09:44:31 2018'
>>> time.asctime(time.localtime(1538271871.226226))
'Sun Sep 30 09:44:31 2018'
>>>

7.时间戳转换成字符串格式时间
>>> time.ctime()
'Thu Oct 11 17:02:10 2018'
>>> time.ctime(987867475)
'Sat Apr 21 23:37:55 2001'
```

#### 格式参照:

| 字符串 | 功能 |
| :--- | :--- |
| %a | 本地（locale）简化星期名称 |
| %A | 本地完整星期名称 |
| %b | 本地简化月份名称 |
| %B | 本地完整月份名称 |
| %c | 本地相应的日期和时间表示 |
| %d | 一个月中的第几天（01 - 31） |
| %H | 一天中的第几个小时（24小时制，00 - 23） |
| %I | 第几个小时（12小时制，01 - 12） |
| %j | 一年中的第几天（001 - 366） |
| %m | 月份（01 - 12） |
| %M | 分钟数（00 - 59） |
| %p | 本地am或者pm的相应符 |
| %S | 秒（01 - 61） |
| %w | 一个星期中的第几天（0 - 6，0是星期天） |
| %W | 和%U基本相同，不同的是%W以星期一为一个星期的开始。 |
| %x | 本地相应日期 |
| %X | 本地相应时间 |
| %y | 去掉世纪的年份（00 - 99） |
| %Y | 完整的年份 |
| %Z | 时区的名字（如果不存在为空字符） |
| %% | %’字符 |
| %U | 一年中的周数。（00 - 53，周日是一个周的开始。）第一个星期天之前的所有天数都放在第0周 |

### 函数方法

Time 模块包含了以下内置函数，既有时间处理的，也有转换时间格式的：

| 序号 | 函数及描述 |
| :--- | :--- |
| 1 | time.altzone 返回格林威治西部的夏令时地区的偏移秒数。如果该地区在格林威治东部会返回负值（如西欧，包括英国）。对夏令时启用地区才能使用。 |
| 2 | time.asctime\(\[tupletime\]\) 接受时间元组并返回一个可读的形式为"Tue Dec 11 18:07:14 2008"（2008年12月11日 周二18时07分14秒）的24个字符的字符串。 |
| 3 | time.clock\( \) 用以浮点数计算的秒数返回当前的CPU时间。用来衡量不同程序的耗时，比time.time\(\)更有用。 |
| 4 | time.ctime\(\[secs\]\) 作用相当于asctime\(localtime\(secs\)\)，未给参数相当于asctime\(\) |
| 5 | time.gmtime\(\[secs\]\) 接收时间戳（1970纪元后经过的浮点秒数）并返回格林威治天文时间下的时间元组t。注：t.tm\_isdst始终为0 |
| 6 | time.localtime\(\[secs\]\) 接收时间戳（1970纪元后经过的浮点秒数）并返回当地时间下的时间元组t（t.tm\_isdst可取0或1，取决于当地当时是不是夏令时）。 |
| 7 | time.mktime\(tupletime\) 接受时间元组并返回时间戳（1970纪元后经过的浮点秒数）。 |
| 8 | time.sleep\(secs\) 推迟调用线程的运行，secs指秒数。 |
| 9 | time.strftime\(fmt\[,tupletime\]\) 接收以时间元组，并返回以可读字符串表示的当地时间，格式由fmt决定。 |
| 10 | time.strptime\(str,fmt='%a %b %d %H:%M:%S %Y'\) 根据fmt的格式把一个时间字符串解析为时间元组。 |
| 11 | time.time\( \) 返回当前时间的时间戳（1970纪元后经过的浮点秒数）。 |
| 12 | time.tzset\(\) 根据环境变量TZ重新初始化时间相关设置。 |

Time模块包含了以下2个非常重要的属性：

| 序号 | 属性及描述 |
| :--- | :--- |
| 1 | **time.timezone** 属性time.timezone是当地时区（未启动夏令时）距离格林威治的偏移秒数（&gt;0，美洲;&lt;=0大部分欧洲，亚洲，非洲）。 |
| 2 | **time.tzname** 属性time.tzname包含一对根据情况的不同而不同的字符串，分别是带夏令时的本地时区名称，和不带的。 |



