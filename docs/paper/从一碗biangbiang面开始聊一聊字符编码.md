# 从一碗𰻝𰻝面（biáng biáng miàn）开始聊一聊字符编码

> 摘要：字符编码是计算机的基础，ISO/IEC 10646 通用字符集是全球化信息交换最重要的国际标准。本文简要介绍了汉字编码的历史、汉字的编码规则和未编码汉字的描述方法。并以▛▚▞▟▙▚▞▜为例介绍如何使用私人使用区自定义字符、自创字体实现个性化文本的信息交换需求。最后以国际化域名为例引出了编码视觉安全问题并列举了一些推荐的应对建议。

## 序言
使用如下字符替换了部分敏感词。完整版PDF请联系作者索取。

|字符|原始文字|
|-|-|
|▛▞▙▚▞▜|某地点|
|▛▚▞▟|公司中文名|
|▙▚▞▜|公司特有标识名称|
|▙▚▚▜|公司英文名|
|▙▞▞▜|公司英文名（重音符）|
|▛▞▞▜|公司英文名（西里尔文字）|

## 汉字和编码历史
▛▞▙▚▞▜楼下有一家陕西面馆，上书（biáng biáng miàn）[^1]面。了解陕西美食文化的或许都听说过这个鼎鼎有名的笔画最多、结构最复杂的汉字，然而在2020年以前这个字无法在电脑上录入及显示。即使是两年后的今天它依然未被广泛使用的字体收录——它并不是常用汉字（该字位于G区，第三表意文字平面，Tertiary Ideographic Plane，TIP[^2]）——因此一般字体往往无法正常显示[^3]。

> 𰻝 `U+30EDD` 𰻞 `U+30EDE`


前文所述的𰻝字使用历史较久，将其编码还算解决历史遗留问题、补全字符集，那么近几年有没有新汉字亮相呢？2017年中国科学院、国家语言文字工作委员会、全国科学技术名词审定委员会召开的联合发布会为几个新元素正式命名分别为：鿭、镆、鿬、鿫，其中除镆之外都是新造汉字[^4]。

中国的汉字最早可以追溯到6000多年前，从小篆开始逐渐定型、稳定，直至今天。汉字在发展的过程中出现了大量汉字、异体字。自从计算机发明以后，传入中国之后汉字的输入问题一直阻碍中国计算机的发展及普及，从1978年上海电工仪器研究所部工程师支秉彝创造了一种“见字识码”法[^5]开始直至1984年王永民发明“五笔字型”输入法[^6]才逐渐解决汉字录入的困难使得汉字输入技术真正达到普及化、实用化——这是一种真正达到成熟阶段的汉字编码方案。在计算机逐渐普及的过程中，国家汉字编码标准也在不断发展，从1980年的GB/T 2312-1980、到1995年的汉字内码扩展规范（GBK）1.0版、又到2005年的GB 18030-2005、今年刚发布的GB 18030-2022，中国汉字编码不断更新。

汉字的历史有数千年，计算机的发展史只有几十年。即使经过几十年计算机科学家、汉语言学家的不懈努力今天仍然有历史汉字——包括大量未被发现的汉字——甚至随时可能新增的汉字——未被编码，无法通过计算机录入和显示。
## 新汉字诞生前后
随着全球化时代浪潮席卷而来，采用国际标准ISO/IEC 10646[^7]逐渐成为世界范围内信息技术产品开发的主流，它必然将逐渐取代现有的汉字编码字符集标准（中国大陆对应的标准是GB 13000，同时与产业标准The Unicode® Standard等效）。ISO/IEC 10646国际标准隶属于ISO/IEC JTC 1/SC2（国际标准化组织和国际电工委员会共同成立的第一联合技术委员会下属的第二分技术委员会），专门负责研制编码字符集（Coded Character Set）的国际标准。接下来以ISO/IEC 10646标准为例说明编码一个汉字需要哪些步骤。SC2下属有且只有一个工作组WG2，WG2成立了专门的汉字编码国际工作组IRG[^8]（Ideographic Rapporteur Group），凡是与汉字相关的编码提案一般都先提交至IRG[^9]。提案的途径多种多样，包括国家提案、下属工作组提案、联络员提案、个人或团体提案。汉字的加字活动分为三种，分别为横向扩展（Horizontal Extension）、纵向扩展（Vertical Extension）和表意文字变体数据库（IVD，Ideographic Variation Database）注册，通常理解的新字（如上文中的几个新元素符号）即为纵向扩展，分为工作集（Working Set）和急用汉字（Urgently Needed Character）两种，分别是不同的提交流程[^10]。有了新字需求，或者发现了尚未编码的汉字后即可编写提案了，提案内容包括汉字及其书面证据的详细信息。提案提交至IRG后，经过多方专家的讨论、国家机构的正式投票后便可添加至字符集，成功编码了[^11]。

在成功编码加入ISO/IEC 10646标准之前，那些未被编码的汉字应该如何描述呢？如果有需要信息化的汉字或者字符又应该如何处理？

不同于西方的文字系统由字母线性组合成单词、再由单词连缀成句子，汉字本身是由众多构字部件组成（偏旁部首）平面组合而成的。遗憾的是计算机是由西方发明的，规则与标准也以西方的习惯为原型制定，汉字的信息化只能被迫适应西方标准。然而汉字数量庞大，由于汉字的灵活性和开放性汉字的使用者常常选择自造汉字——例如大量的日本汉字、朝鲜汉字、越南汉字，不可能一个字符集就收集所有的汉字，现行的字集往往是不完整的。因此为了方便准确、完整地描述汉字（或CKJV 中日韩越）字符和为尚未在ISO/IEC 10646或Unicode中编码的稀有字符提供替代编码形式，在1998年提出的表意文字描述符[^12]（IDC，Ideographic Description Characters）于1999年被SC2正式批准添加至Unicode 3.0版本。

表格 1表意文字描述符示例

|IDC|描述|示例|
|-|-|-|
|⿰|左右结构|`U+4ED6` 他 = ⿰亻也|
|⿱|上下结构|`U+594B` 奋 = ⿱大田|
|⿲|左中右结构|`U+8857` 街 = ⿲彳圭亍|
|⿳|上中下结构|`U+4EAB` 享 = ⿳亠口子|
|⿴|全包围结构|`U+56DE` 回 = ⿴囗口|
|⿵|上半包围结构|`U+95EE` 问 = ⿵门口|
|⿶|下半包围结构|`U+51F6` 凶 = ⿶凵㐅|
|⿷|左半包围结构|`U+531E` 匞 = ⿷匚工|
|⿸|向右下包围结构|`U+5385` 厅 = ⿸厂丁|
|⿹|向左下包围结构|`U+53EF` 可 = ⿹丁口|
|⿺|向右上包围结构|`U+54AB` 咫 = ⿺尺只|
|⿻|嵌套结构|`U+5669` 噩 = ⿻王㗊|

以上文提到的117号元素新字“鿬”为例，使用IDC可写作“⿰石田”。如果要描述的汉字构字部件不止两个则可以继续嵌套书写，IDC如同数学运算表达式中的算数运算符，构字部件如同数字和未知数。以上文提到的“𰻝”字为例，使用IDC可写作：

`⿺辶⿳穴⿲月⿱⿲幺言幺⿲长马长刂心`[^13]

这种描述一个汉字的表达式就叫做表意文字描述序列（IDS，Ideographic Description Sequence），由IDC、汉字、部首、笔画、私用区字符等组成的前缀表达式（也称为[波兰表达式](前中后缀表达式.md)）构造成IDS表达式[^14]。IDC没有优先级顺序、IDS也没有固定的拆分和描述某个汉字字符的标准，只要你认为足以表达清楚即可。  
 

代码 1 表意文字描述序列语法
```
IDS := Ideographic | Radical | CJK_Stroke | Private Use | ？
	| IDS_BinaryOperator IDS IDS
	| IDS_TrinaryOperator IDS IDS IDS
CJK_Stroke := ㇀ | ㇁ | ㇂ | ㇃ | ㇄ | ... | ㇢ | ㇣
IDS_BinaryOperator := ⿰ | ⿱ | ⿴ | ⿵ | ⿶ | ⿷ | ⿸ | ⿹ | ⿺ | ⿻
IDS_TrinaryOperator:= ⿲ | ⿳
```
## 自定义字符
除了使用IDC描述汉字以外，还可以通过私人使用区[^15]（PUA，Private Use Area）来编码，PUA范围内的码值含义不由字符编码标准指定，其使用和解释可以由用户自行决定。Unicode中有三个编码范围可供使用，基本多文种平面[^16]（BMP，Basic Multilingual Plane）中U+E000..U+F8FF的范围内共包含6400个私人使用字符，再加上15、16区域（U+F0000..U+FFFFD 和 U+100000..U+10FFFD）内共有137468个私人使用字符。未编码的汉字也可临时分配至PUA以供使用，如国家标准GB 18030-2005就在PUA区域映射了数十个汉字。本文接下来以▛▚▞▟标识为例介绍如何使用PUA[^17]，尝试将其字符化处理，把它编码至PUA的U+E005码位，再配合开放式字体[^18]（OTF，OpenType Fonts）技术将其以文本形式录入并显示在本文中。

 第一步，本文约定将U+E005码位定义为▛▚▞▟标识，以UTF-8编码为EE 80 80，二进制为`11101110` `10000000` `10000101`占用3个字节。

 第二步，使用任意支持OpenType格式的字体设计软件[^19]为U+E005码位创建▛▚▞▟▙▚▞▜[^20]字形 ，得到▙▚▚▜ LOGO-Regular.OTF字体文件。

 第三步，安装字体文件，在Word中键入E005，选中后按下ALT+X快捷键[^21]以Unicode字符编码形式转换为字符，再更改字体为刚才安装的▙▚▚▜ LOGO字体便能显示出▛▚▞▟标识字符。

>  `U+E005`

已编码的字符和字体是如何合作如何显示到屏幕上的呢？用户通过拼音、五笔等方式敲击的字符称为外码[^22]，通过输入法编辑器（IME，Input Method Editors）将外码转换为计算机内码，比如上文中为▛▚▞▟标识定义的U+E005的二进制编码，根据指定或默认的字模库（也称为字库）找到内码对应的字形、位宽等信息，再将通过字形信息和字号计算出要绘制的像素点阵信息发送至显示器的缓冲存储器中，显示器的控制器再将像素信息顺次读出显示至屏幕的每一个像素点中，之后计算机前的用户就看到了这个字符。这就是从编码至录入直到显示字符的完整过程。

每个字符都有其特定的字形，即人类可以书写、识别的自然文字符号。由于各种原因[^23]，看起来相同的符号却可能有多个不同的编码。

表格 2字形相同或相似但是编码不同

|字符1|说明1|字符2|说明2|
|-|-|-|-|
|⼭ `U+2F2D`|汉字部首|山 `U+5C71`|中日韩越统一汉字|
|凉 `U+F979`|中日韩越兼容汉字|凉 `U+51C9`|中日韩越统一汉字|
|㬵 `U+3B35`|中日韩越统一汉字扩展A|胶 `U+80F6`|中日韩越统一汉字|
|㖈 `U+3588`|中日韩越统一汉字扩展A|䎛 `U+439B`|中日韩越统一汉字扩展A|
|А `U+0410`|基本俄语字母|A `U+0041`|基本拉丁字母|
|Α `U+0391`|希腊字母|||
|0 `U+0030`|数字0|O `U+004F`|基本拉丁字母|

## 编码视觉安全
但是相同或相似的字形会影响用户的阅读和使用，两个外观看起来非常相似的字符极其难以区分，极易造成误解和欺骗（同形异意攻击，Homoglyph Attack），给入侵和攻击带来可趁之机。接下来本文以国际化域名编码为切入点简要介绍编码的视觉安全及应对策略[^24]。互联网起源于美国，与之相关的技术和标准都是在英语环境下制定的，比如域名只支持ASCII编码的字符。但是人们更希望看到自己的语言和文字书写的域名，比如在中文语言环境下“▛▚▞▟.公司”看起来比“▙▚▚▜life.com”要更易于传播和理解。于是2003年提出了国际化域名方案[^25]（IDNA，Internationalized Domain Name in Applications），将域名中包含的非ASCII字符转换为ASCII。比如 ▙▚▚▜life.com 和 ▙▚▚▜1ife.com、▙▚▚▜Iife.com、▙▞▞▜life.com，在某些字体下和屏幕尺寸下非常难以区分差别，误导用户访问到错误的网站。以上的几个例子中分别使用了数字“1”、拉丁字母“I”、含重音符的字母“ë”替代了域名部分字符的欺骗方式称为单脚本欺骗，使用字体区分、提高用户警惕的情况下有可能避免此类问题。但是下方的表格3的跨脚本欺骗示例中，俄语字母和拉丁字母“e”完全一致，出现此类问题的有拉丁字母、西里尔字母和希腊字母，甚至可以用西里尔文构造一个域名“scope.com”，除顶级域名外和拉丁文完全一致，这些欺骗称为全脚本欺骗，导致的问题称为全脚本混淆。这类问题意味着非常特殊的挑战，因为这几类字母系统间共享的字母数量非常多。

表格 3混合脚本欺骗示例

|域名|UTF-16|Punycode|说明|
|-|-|-|-|
|▙▚▚▜life.com|007A **0065 0065** 006B 0072 006C 0069 0066 0065 002E 0063 006F 006D|▙▚▚▜life.com|
|▛▞▞▜life.com|007A **0435 0435** 006B 0072 006C 0069 0066 0065 002E 0063 006F 006D|[xn--zkrlife-7gga.com](xn--zkrlife-7gga.com)|使用俄语字母е U+0435替代了拉丁字母e U+0065|

除此之外，因字体渲染问题不易区分差异、不易察觉的重音符、字体恶意渲染、语法欺骗等原因也会导致视觉欺骗。
以下是一些尽可能防止欺骗的应对建议：
对于终端用户：
-	尽可能使用最新版本的浏览器、邮件客户端等软件
-	注册域名时避免采用可能导致混淆的字符
-	打印时注意检查
-	注意检查打印出的文件和屏幕上显示的不同

对于开发人员：
-	解析数字时，检测到非预期的语言字符时提醒用户
-	配置文件中使用安全的配置文件标识符，不允许使用受限字符（例如现代语言中不使用的符号、专业领域中使用的符号、小众的符号）
-	选择字体时，如果某个字符没有可用的字形，不要简单地显示“？”问号或省略该字符
-	尽可能使用不同的字体以区分差异
-	设置可以方便看出差异的文字大小，字号过小时一些细节可能渲染时丢失
-	确保文字始终在页面及元素的可见范围之内
-	使用最后的手段字体[^26]（Last Resort Fonts）[https://github.com/unicode-org/last-resort-font](https://github.com/unicode-org/last-resort-font)，确保字体不支持某些字符时不会显示丢失造成欺骗和攻击

全文完。

[^1]: [1] 𰻞 - CJK Unified Ideograph-30EDE: U+30EDE[EB/OL]. [2022-11-09]. https://unicode-table.com/en/30EDE/.
[^2]: Roadmap to the TIP[EB/OL]. [2022-11-09]. https://www.unicode.org/roadmaps/tip/.
[^3]: 本文使用了Andrew West(魏安) 的BabelStone Han字体。BabelStone Fonts : BabelStone Han[EB/OL]. [2022-11-09]. https://www.babelstone.co.uk/Fonts/Han.html.
[^4]: 中国科学院、国家语言文字工作委员会、全国科学技术名词审定委员会联合发布113号等4个元素中文名称 - 中华人民共和国教育部政府门户网站[EB/OL]. [2022-11-09]. http://www.moe.gov.cn/s78/A19/A19_ztzl/ztzl_yywzgfbz/guifanbzjs/201705/t20170510_304234.html.
[^5]: 支秉彝, 钱锋. 浅谈“见字识码”[J]. 自然杂志, 1978(6): 350-353+367.
[^6]: 《五笔字型汉字编码方案》简介略评[J/OL]. 文字改革, 1984(3): 27-28. DOI:[10.16412/j.cnki.1001-8476.1984.03.005](https://doi.org/10.16412/j.cnki.1001-8476.1984.03.005).
[^7]: ISO/IEC 10646标准和Unicode标准保持同步 https://www.unicode.org/faq/unicode_iso.html
[^8]: Ideographic Research Group. https://appsrv.cse.cuhk.edu.hk/~irg/
[^9]: 陈壮. 中国在ISO/IEC JTC1/SC2的活动与中文编码的国际标准化[J]. 中文信息学报, 2007(4): 122-128.
[^10]: 两种加字流程分别参考IRG Principles and Procedures (IRG PnP)第三章和附录C. https://appsrv.cse.cuhk.edu.hk/~irg/irg/irg50/IRGN2310SC2N4611WG2N4979IRGPnP11.pdf
[^11]: 可参考𰻞的编码历史。如何看待 Unicode 13 收录 biang（U+30EDE）字？ - 知乎[EB/OL]. [2022-11-10]. https://www.zhihu.com/question/49830245/answer/1318940122.
[^12]: Combined CD registration and consideration ballot on WD for 10646-1/Amd. 28, Information technology - Universal Multiple-Octet Coded Character Set (UCS) - Part 1: Architecture and Basic Multilingual Plane -- AMENDMENT 28: Ideographic description characters https://www.unicode.org/L2/L1998/02n3186.pdf
[^13]: BabelStone : CJK[EB/OL]. [2022-11-10]. https://www.babelstone.co.uk/CJK/.
[^14]: The Unicode® Standard Version 15.0 – Core Specification [EB/OL]. [2022-11-12]. https://www.unicode.org/versions/Unicode15.0.0/. The Unicode® Standard 15.0:761
[^15]: FAQ - Private-Use Characters, Noncharacters, and Sentinels[EB/OL]. [2022-11-11]. https://www.unicode.org/faq/private_use.html.
[^16]: Roadmap to the BMP[EB/OL]. [2022-11-10]. https://www.unicode.org/roadmaps/bmp/.
[^17]: 在iOS系统中，Apple将U+F8FF映射为Apple的品牌标识
[^18]: OpenType fonts features Adobe Type[EB/OL]. [2022-11-11]. https://www.adobe.com/products/type/opentype.html.
[^19]: 本文中笔者使用Glyphr Studio软件设计并创建字体。Glyphr Studio - font design, online[EB/OL]. [2022-11-10]. https://www.glyphrstudio.com/.
[^20]: 根据《▙▚▚▜ ▛▚▞▟品牌视觉指导手册2.0中文版CN》之标准创建此字形
[^21]: Insert ASCII or Unicode character codes in Word[EB/OL]. [2022-11-10]. https://support.microsoft.com/en-us/office/insert-ascii-or-unicode-character-codes-in-word-e97306f7-00c1-490d-9920-c924ca443f87.
[^22]: 本文展示的例子中跳过了外码录入的过程，直接键入内码转换为特定的字符。
[^23]: 例如⼭ U+2F2D和山 U+5C71，前者是偏旁部首，后者是通用汉字；凉 U+F979是为了兼容韩国的编码及标准，凉 U+51C9是通用汉字；㖈 U+3588和䎛 U+439B是应该被认同为同一个汉字但是被错误地区分的重复编码；А U+0410、A U+0041和Α U+0391字形一致但分别属于不同的字母（Script）系统
[^24]: 更多信息可查阅Unicode安全注意事项 https://unicode.org/reports/tr36
[^25]: FÄLTSTRÖM P, HOFFMAN P E. Internationalizing Domain Names in Applications (IDNA): RFC 3490[R/OL]. Internet Engineering Task Force, 2003. https://datatracker.ietf.org/doc/rfc3490. DOI:10.17487/RFC3490.
[^26]: Unicode Character Blocks by Last Resort Glyph. http://www.unicode.org/charts/lastresort.html
