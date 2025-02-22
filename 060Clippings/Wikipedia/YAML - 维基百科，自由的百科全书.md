---
title: "YAML - 维基百科，自由的百科全书"
date: "2025-02-22T20:06:19+08:00"
author:
  - "[[维基媒体项目贡献者]]"
tags:
  - "clippings"
category: "yaml 教程"
rating: "8"
published: 2008-09-29
description:
source: "https://zh.wikipedia.org/wiki/YAML"
---
<table><caption>YAML</caption><tbody><tr><td colspan="2"><span><a href="https://zh.wikipedia.org/wiki/File:Official_YAML_Logo.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Official_YAML_Logo.svg/140px-Official_YAML_Logo.svg.png" width="140" height="129"></a></span></td></tr><tr><th scope="row"><a href="https://zh.wikipedia.org/wiki/%E6%89%A9%E5%B1%95%E5%90%8D">扩展名</a></th><td><p>.yaml, .yml</p></td></tr><tr><th scope="row"><a href="https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%AA%92%E4%BD%93%E7%B1%BB%E5%9E%8B"><span>互联网</span><span>媒体类型</span></a></th><td><p><code>application/yaml</code><sup><a href="https://zh.wikipedia.org/wiki/#cite_note-rfc9512-1"><span>[</span>1<span>]</span></a></sup></p></td></tr><tr><th scope="row">首次发布</th><td>2001年5月11日<span>，​23年前</span><span>​（<span>2001-05-11</span>）</span></td></tr><tr><th scope="row"><a href="https://zh.wikipedia.org/wiki/%E8%BD%AF%E4%BB%B6%E7%89%88%E6%9C%AC%E5%91%A8%E6%9C%9F">最新版本</a></th><td><p>1.2 (Revision 1.2.2)<br>2021年10月1日<span>，​3年前</span><span>​（<span>2021-10-01</span>）</span></p></td></tr><tr><th scope="row">格式类型</th><td>数据交换</td></tr><tr><th scope="row"><span>免费格式？</span></th><td>是</td></tr><tr><th scope="row">网站</th><td><span><a href="http://yaml.org/">yaml<wbr>.org</a></span></td></tr></tbody></table>

**YAML**（）是一个可读性高，用来表达数据[序列化](https://zh.wikipedia.org/wiki/%E5%BA%8F%E5%88%97%E5%8C%96 "序列化")的格式。YAML参考了其他多种语言，包括：[C语言](https://zh.wikipedia.org/wiki/C%E8%AA%9E%E8%A8%80 "C语言")、[Python](https://zh.wikipedia.org/wiki/Python "Python")、[Perl](https://zh.wikipedia.org/wiki/Perl "Perl")，并从[XML](https://zh.wikipedia.org/wiki/XML "XML")、电子邮件的数据格式（[RFC 2822](https://datatracker.ietf.org/doc/html/rfc2822)[^2]）中获得灵感。Clark Evans在2001年首次发表了这种语言[^3]，另外Ingy döt Net与Oren Ben-Kiki也是这语言的共同设计者[^4]。目前已经有数种编程语言或脚本语言支持（或者说解析）这种语言。

YAML是"YAML Ain't a Markup Language"（YAML不是一种[标记语言](https://zh.wikipedia.org/wiki/%E6%A0%87%E8%AE%B0%E8%AF%AD%E8%A8%80 "标记语言")）的[递归缩写](https://zh.wikipedia.org/wiki/%E9%81%9E%E8%BF%B4%E7%B8%AE%E5%AF%AB "递归缩写")。在开发的这种语言时，YAML的意思其实是："Yet Another Markup Language"（仍是一种[标记语言](https://zh.wikipedia.org/wiki/%E6%A0%87%E8%AE%B0%E8%AF%AD%E8%A8%80 "标记语言")）[^yaml_spec_2001_08_01-5]，但为了强调这种语言以数据为中心，而不是以标记语言为重点，而用反向缩略语重命名。

YAML的语法和其他高级语言类似，并且可以简单表达清单、散列表，标量等数据形态。[^vartype000-6]它使用空白符号缩进和大量依赖外观的特色，特别适合用来表达或编辑数据结构、各种配置文件、倾印调试内容、文件大纲（例如：许多电子邮件标题格式和YAML非常接近）。尽管它比较适合用来表达层次结构式（hierarchical model）的数据结构，不过也有精致的语法可以表示关系性（relational model）的数据。[^relationalnote000-7]由于YAML使用空白字符和分行来分隔数据，使得它特别适合用[grep](https://zh.wikipedia.org/wiki/Grep "Grep")／[Python](https://zh.wikipedia.org/wiki/Python "Python")／[Perl](https://zh.wikipedia.org/wiki/Perl "Perl")／[Ruby](https://zh.wikipedia.org/wiki/Ruby "Ruby")操作。其让人最容易上手的特色是巧妙避开各种封闭符号，如：引号、各种括号等，这些符号在嵌套结构时会变得复杂而难以辨认。

数据结构可以用类似大纲的缩进方式呈现

```
---
receipt:     Oz-Ware Purchase Invoice
date:        2012-08-06
customer:
    given:   Dorothy
    family:  Gale
   
items:
    - part_no:   A4786
      descrip:   Water Bucket (Filled)
      price:     1.47
      quantity:  4

    - part_no:   E1628
      descrip:   High Heeled "Ruby" Slippers
      size:      8
      price:     133.7
      quantity:  1

bill-to:  &id001
    street: | 
            123 Tornado Alley
            Suite 16
    city:   East Centerville
    state:  KS

ship-to:  *id001   

specialDelivery:  >
    Follow the Yellow Brick
    Road to the Emerald City.
    Pay no attention to the
    man behind the curtain.
...
```

注意在YAML中，字符串不一定要用双引号标示。另外，在缩进中空白字符的数目并不是非常重要，只要相同层次结构的元素左侧对齐就可以了（不过不能使用TAB字符）。这个文件的顶层由七个键值组成：其中一个键值"items"，是两个元素构成的[数组](https://zh.wikipedia.org/wiki/%E9%99%A3%E5%88%97 "数组")（或称[清单](https://zh.wikipedia.org/wiki/%E6%B8%85%E5%96%AE "清单")），这清单中的两个元素同时也是包含了四个键值的散列表。文件中重复的部分用这个方法处理：使用锚点（**&**）和引用（**\***）标签将"bill-to"散列表的内容复制到"ship-to"散列表。也可以在文件中加入选择性的空行，以增加可读性。在一个文件中，可同时包含多个文件，并用"`**---**`"分隔。选择性的符号"`**...**`"可以用来表示文件结尾（在利用流的通信中，这非常有用，可以在不关闭流的情况下，发送结束信号）。

YAML提供缩进／区块以及内置（inline）两种格式，来表示清单和[散列表](https://zh.wikipedia.org/wiki/%E9%9B%9C%E6%B9%8A%E8%A1%A8 "散列表")。以下展示几种YAML的基本组件。

习惯上清单比较常用区块格式（block format）表示，也就是用短杠+空白字符作为起始。

```
 --- # 最喜愛的電影
 - Casablanca
 - North by Northwest
 - Notorious
```

另外还有一种内置格式（inline format）可以选择──用方括号围住，并用逗号+空白区隔（类似[JSON](https://zh.wikipedia.org/wiki/JSON "JSON")的语法）。[^8]

```
 --- # 購物清單 
 [milk, pumpkin pie, eggs, juice]
```

键值和数据由冒号及空白字符分开。区块形式（常使用于YAML数据文档中）使用缩进和换行符分隔**key: value**对。内置形式（常使用于YAML数据流中）在大括号中使用逗号+空白字符分隔**key: value**对。

```
 --- # 區塊形式
   name: John Smith
   age: 33
 --- # 內置形式
 {name: John Smith, age: 33}
```

再次强调，字符串不需要包在引号之内。

有两种语法可以书写多行文字（multi-line strings），一种为保留换行（使用`|`字符），另一种为折叠换行（使用`>`字符）。两种语法在其特殊字符之后都必须接着换行。

##### 保留换行(Newlines preserved)

```
data: |                                     # 譯者注：這是一首著名的五行民謠(limerick)
   There once was a man from Darjeeling     # 這裡曾有一個人來自大吉嶺
   Who got on a bus bound for Ealing        # 他搭上一班往伊靈的公車
       It said on the door                  # 門上這麼說的
       "Please don't spit on the floor"     # "請勿在地上吐痰"
   So he carefully spat on the ceiling      # 所以他小心翼翼的吐在天花板上
```

根据默认，每行开头的缩进（以首行为基准）和行末空白会被去除，而不同的缩进会保留差异。

##### Chomping Final Line Break

使用保留换行时，作为最后一行结尾的换行(\\n)会包含在文本之内，若希望使用此缩进方式，但不想要含有最后的换行，可以使用Chomping Final Line Break。

```
data: |-                                     # 譯者注：這是一首著名的五行民謠(limerick)
   There once was a man from Darjeeling     # 這裡曾有一個人來自大吉嶺
   Who got on a bus bound for Ealing        # 他搭上一班往伊靈的公車
       It said on the door                  # 門上這麼說的
       "Please don't spit on the floor"     # "請勿在地上吐痰"
   So he carefully spat on the ceiling      # 所以他小心翼翼的吐在天花板上
```

##### 折叠换行(Newlines folded)

```
data: >
   Wrapped text         # 摺疊的文字
   will be folded       # 將會被收
   into a single        # 進單一一個
   paragraph            # 段落
   
   Blank lines denote   # 空白的行代表
   paragraph breaks     # 段落之間的區隔
```

和保留换行不同的是，只有空白行才视为换行，原本的换行字符会被转换成空白字符，而行首缩进会被去除。

```
- {name: John Smith, age: 33}
- name: Mary Smith
  age: 27
```

```
men: [John Smith, Bill Jones]
women:
  - Mary Smith
  - Susan Williams
```

这部分算是一个后续的讨论，在比较各种数数据列语言时，YAML最常被提到的特色有两个：关系树和数据形态。

为了维持文件的简洁，并避免数据输入的错误，YAML提供了节点参考（\*）和散列合并（<<）参考到其他节点标签的锚点标记（&）。参考会将树状结构加入锚点标记的内容，并可以在所有数据结构中运作（可以参考上面"ship-to"的示例）合并只有散列表可以使用，可以将键值自锚点标记复制到指定的散列表中。

当数据被instantiate合并和参考会被分析器自动展开。

```
#眼部雷射手術之標準程序
---
- step:  &id001                  # 定義錨點標籤 &id001
    instrument:      Lasik 2000
    pulseEnergy:     5.4
    pulseDuration:   12
    repetition:      1000
    spotSize:        1mm

- step:
     <<: *id001                  # 合併鍵值：使用在錨點標籤定義的內容
     spotSize:       2mm         # 覆寫"spotSize"鍵值

- step:
     <<: *id001                  # 合併鍵值：使用在錨點標籤定義的內容
     pulseEnergy:    500.0       # 覆寫鍵值
     alert: >                    # 加入其他鍵值
           warn patient of 
           audible pop
```

由于自动判定数据形态的功能，严格类型（也就是用户有宣告的数据形态）很难在大部分的YAML文件中看到。数据类型可以被区分成三大类：原码（core），定义（defined），用户定义（user-defined）。原码可以自动被解析器分析（例如：浮点数，整数，字符串，清单，映射，...）。有一些高级的数据形态──例如比特数据──在YAML中有被“定义”，但不是每一种解析器都有支持。最后，YAML支持用户自定的区域变量，包括：自定义的类别，结构或基本类型（例如：四倍精度的浮点数）。

YAML的自动判定数据形态是哪一种实体。但有时用户会想要将数据强制转型成自定的某种类型。最常见的状况是字符串，有时候可能看起来像数字或布尔值，这种时候可以使用双引号，或是使用严格类型标签。

```
---
a: 123                     # 整數
b: "123"                   # 字串（使用雙引號）
c: 123.0                   # 浮點數
d: !!float 123             # 浮點數，使用!!表達的嚴格型態
e: !!str 123               # 字串，使用嚴格型態
f: !!str Yes               # 字串，使用嚴格型態
g: Yes                     # 布林值"真"（yaml1.1）或字串"Yes"（yaml1.2）
h: Yes we have No bananas  # 字串（包含"Yes"和"No"）
```

除了一般的数据形态之外，用户也可以使用一些较为高级的类型，但不保证可被每种解析器分析。使用时和强制转型类似，要在形态名称之前加上两个惊叹号（!!）。有几种重要的形态在本篇没有讨论，包括[集合](https://zh.wikipedia.org/wiki/%E9%9B%86%E5%90%88 "集合")（sets），有序映照（ordered maps），[时间戳记](https://zh.wikipedia.org/wiki/%E6%99%82%E9%96%93%E6%88%B3%E8%A8%98 "时间戳记")（timestamps）以及十六进制数据（hexadecimal）。下面这个示例则是比特数据（binary）

```
---
picture: !!binary |
 R0lGODdhDQAIAIAAAAAAANn
 Z2SwAAAAADQAIAAACF4SDGQ
 ar3xxbJ9p0qa7R0YxwzaFME
 1IAADs=
```

许多YAML的实现允许用户自定义数据形态。在将一个对象序列化时，这个方法还颇方便的。某些区域数据形态可能不存在默认的数据形态中，不过这种类型在特定的YAML应用程序中是有定义的。这种区域数据形态用惊叹号（ **`!`** ）表示。

```
---
myObject:  !myClass { name: Joe, age: 15}
```

在yaml.org[^9]（英文）可以找到轻巧而好用的小抄[^10]（亦是用YAML表示）及格式说明[^11]。下面的内容，是关于基本组件的摘要。

- YAML使用可打印的[Unicode](https://zh.wikipedia.org/wiki/Unicode "Unicode")字符，可使用[UTF-8](https://zh.wikipedia.org/wiki/UTF-8 "UTF-8")或[UTF-16](https://zh.wikipedia.org/wiki/UTF-16 "UTF-16")。
- 使用空白字符为文件缩进来表示结构；不过不能使用跳格字符(TAB)。
- 注解由井字号（ **#** ）开始，可以出现在一行中的任何位置，而且范围只有一行（也就是一般所谓的单行注解）
- 每个清单成员以单行表示，并用短杠+空白（ **-**   ）起始。或使用[方括号](https://zh.wikipedia.org/wiki/%E6%8B%AC%E8%99%9F "括号")（ **\[ \]** ），并用[逗号](https://zh.wikipedia.org/wiki/%E9%80%97%E8%99%9F "逗号")+空白（ **,**   ）分开成员。
- 每个散列表的成员用冒号+空白（ **:**   ）分开键值和内容。或使用大括号（ **{   }** ），并用逗号+空白（ **,**   ）分开。
- 散列表的键值可以用[问号](https://zh.wikipedia.org/wiki/%E5%95%8F%E8%99%9F "问号") ( **?** )起始，用来明确的表示多个词汇组成的键值。
- 字符串平常并不使用引号，但必要的时候可以用[双引号](https://zh.wikipedia.org/wiki/%E5%8F%8C%E5%BC%95%E5%8F%B7 "双引号") ( **"** )或[单引号](https://zh.wikipedia.org/wiki/%E5%8D%95%E5%BC%95%E5%8F%B7 "单引号") ( **'** )框住。
- 使用双引号表示字符串时，可用倒斜线（ **\\** ）开始的转义字符（这跟[C语言](https://zh.wikipedia.org/wiki/C%E8%AA%9E%E8%A8%80 "C语言")类似）表示特殊字符。
- 区块的字符串用缩进和修饰符（非必要）来和其他数据分隔，有新行保留（preserve）（使用符号 **|** ）或新行折叠（flod）（使用符号 **>** ）两种方式。
- 在单一文件中，可用连续三个[连字号](https://zh.wikipedia.org/wiki/%E8%BF%9E%E5%AD%97%E5%8F%B7 "连字号")（**\---**）区分多个文件。
- 另外，还有选择性的连续三个点号（ **...** ）用来表示文件结尾。
- 重复的内容可使从参考标记[星号](https://zh.wikipedia.org/wiki/%E6%98%9F%E8%99%9F "星号") ( **\*** )复制到锚点标记（ **&** ）。
- 指定格式可以使用两个[惊叹号](https://zh.wikipedia.org/wiki/%E6%83%8A%E5%8F%B9%E5%8F%B7 "惊叹号") ( **!!** )，后面接上名称。
- 文件中的单一文件可以使用**[指导指令](https://zh.wikipedia.org/wiki/%E7%B7%A8%E8%AD%AF%E7%A8%8B%E5%BC%8F%E5%AE%9A%E5%90%91 "编译程序定向")**，使用方法是[百分比符号](https://zh.wikipedia.org/w/index.php?title=%E7%99%BE%E5%88%86%E6%AF%94%E7%AC%A6%E8%99%9F&action=edit&redlink=1 "百分比符号（页面不存在）")( **%** )。有两个[指导指令](https://zh.wikipedia.org/wiki/%E7%B7%A8%E8%AD%AF%E7%A8%8B%E5%BC%8F%E5%AE%9A%E5%90%91 "编译程序定向")在YAML1.1版中被定义：
- %YAML 指导指令，用来识别文件的YAML版本。
- %TAG 指导指令，被用在URI的前缀标记。这个方法在标记节点的类型时相当有用。

YAML在使用逗号及冒号时，后面都必须接一个空白字符，所以可以在字符串或数值中自由加入分隔符号（例如：5**,**280或http**:**//www.wikipedia.org）而不需要使用引号。

另外还有两个特殊符号在YAML中被[保留](https://zh.wikipedia.org/wiki/%E4%BF%9D%E7%95%99%E5%AD%97 "保留字")，有可能在未来的版本被使用--（ **@** ）和（ **\`** ）。

虽然YAML是参考[JSON](https://zh.wikipedia.org/wiki/JSON "JSON")，[XML](https://zh.wikipedia.org/wiki/XML "XML")和[SDL](https://zh.wikipedia.org/wiki/SDL "SDL")等语言，不过跟这些语言比起来，YAML仍有自己的特色。

JSON的语法是YAML1.2版的子集[^12],，同时非常*接近*[^13] YAML1.0与1.1版的子集，因此大部分的JSON文件都可以被YAML的分析器剖析。[^14]这是因为JSON的语法结构和YAML的内置格式相同。虽然大范围的分层也可以使用类似JSON的内置格式，不过YAML标准并不建议这样使用，除非这样编写能让文件可读性增加。YAML的许多扩展在JSON是找不到的，如：高级数据形态、关系锚点、字符串不需要双引号、映射数据形态会存储键值的顺序。

XML和SDL标签概念，在YAML中是找不到的。*对于数据结构序列*（尽管这是有争议的），标签属性的特色就是可以将数据及复杂数据附加信息分离，并将各种原生数据结构（如：散列表、数组）用同一种语言表示。YAML则以数据的可扩展性作为替代。（包括为了模拟对象的类别类型）在YAML本身的规范中，并没有类似XML的语言定义文件刚要（language-defined document schema descriptors）──例如验证自己本身的结构是否正确的文件。不过，[YAML纲要描述语言](https://zh.wikipedia.org/w/index.php?title=YAML%E7%B6%B1%E8%A6%81%E6%8F%8F%E8%BF%B0%E8%AA%9E%E8%A8%80&action=edit&redlink=1 "YAML纲要描述语言（页面不存在）")（YAML schema descriptor language）是存在[^15]的。另外还有[YAXML](https://zh.wikipedia.org/w/index.php?title=YAXML&action=edit&redlink=1 "YAXML（页面不存在）")──用XML描述YAML的结构──可以让[XML Schema](https://zh.wikipedia.org/wiki/XML_Schema "XML Schema")与[XSLT](https://zh.wikipedia.org/wiki/XSLT "XSLT")转换程序应用在YAML之上。况且，在一般使用的情况下，YAML丰富的定义类型之语法已经提供了足够的方式，来辨认YAML文件是否正确。

由于YAML的运作主要依赖大纲式的缩进来决定结构，这有效解决了[界定符冲突](https://zh.wikipedia.org/w/index.php?title=%E7%95%8C%E5%AE%9A%E7%AC%A6%E8%A1%9D%E7%AA%81&action=edit&redlink=1 "界定符冲突（页面不存在）")（Delimiter collision）的问题。YAML的数据形态不依赖引号之特点，使的YAML文件可以利用区块，轻易的插入各种其他类型文件，如：XML、SDL、JSON，甚至插入另一篇YAML。

```
---
example: >
        HTML goes into YAML without modification
message: |

        <blockquote style="font: italic 12pt Times">
        <p>"Three is always greater than two,
           even for large values of two"</p>
        <p>--Author Unknown</p>
        </blockquote>
```

相反的，要将YAML置入XML或SDL中时，需要将所有空白字符和位势符号（potential sigils，如：**<**,**\>**和**&**）转换成实体语法；要将YAML置入JSON中，需要用引号框住，并转换内部的所有引号。

跟SDL、JSON等，每个子结点只能有单一一个父节点的层次结构式模型不同，YAML提供了一个简单的关系体制，可以从树状结构的其他地方，重复相同的数据，而不必显示那些冗余的结构。这点和XML中的IDRef类似[^16]YAML分析器在将YAML转换成对象时，会自动将那些参考资料的结构展开，所以程序在使用时并不会查觉到哪些数据是解码自这种结构。XML则不会将这种结构展开。这种表示法可以增加程序的可读性，并且，在那种‘大部分参数维持和上次相同，只有少数改变’的配置文件及通信协议中，可以减少数据输入错误。一个例子是：‘送货地点’和‘购买地点’在发票的纪录中几乎都是相同的数据。

YAML是“行导向的”，因此，就算想由现有程序的混乱输出，转换成YAML格式，并保留大部分的原始文件之外观，也非常简单。因为他不需要平衡封闭的标签、括弧及引号，可以从很简单的利用程序，从报表产生YAML。同样，空格分隔可让使用行导向的命令如：grep、Awk、perl、ruby，和Python，来应急性的过滤YAML文件时更加方便。

特别是与标记语言不同的，连续的YAML区块导向往往是格式良好的YAML文件本身。这使得很容易撰写那种“在开始提取的具体记录之前，不需要'读取全部文件内容'”的解析器（通常需要平衡起始和关闭标签、查找引号和转义字符）。当处理一个单一静态的，整个存在存储器中的数据结构将很大，或为提取一个项目来重建的整个结构，代价相当昂贵的记录档，这种特性是相当方便的。

值得讨论的是，尽管它的缩进方式似乎复杂化了深度很大的嵌套层次， YAML将缩进视为一个单一的空白，这可能会获取比其他标记语言更好的压缩比。此外，极深的缩进可以完全避免的是： (1)使用“内置格式”（即简称类JSON格式）而无缩进；或 (2)使用关系锚点展开层次结构以形成一个摊平的格式，使得YAML解析器能透明地重组成完整的数据结构。

YAML是纯粹用来表达数据的语言，所以内部不会存[代码注射](https://zh.wikipedia.org/wiki/%E4%BB%A3%E7%A2%BC%E6%B3%A8%E5%B0%84 "代码注射")的可执行命令。[^17]这代表分析器会相当（至少）安全的解析文件，而不用担心潜在与执行命令相关的安全漏洞。举例来说，[JSON](https://zh.wikipedia.org/wiki/JSON "JSON")是[JavaScript](https://zh.wikipedia.org/wiki/JavaScript "JavaScript")的子集，因此可能有人想使用JavaScript本身的分析器直接eval，不过这样一来就造成许多[代码注射](https://zh.wikipedia.org/wiki/%E4%BB%A3%E7%A2%BC%E6%B3%A8%E5%B0%84 "代码注射")的漏洞。虽然在所有数据序列语言中，安全解析本质上是可能的，但可执行性却正是这样一个恶名昭彰的缺陷；而YAML缺乏相关的命令语言，可能是一个相对安全的利益。

XML[^xml_1.0-18][^xml_1.1-19]和YAML规范[^yaml_spec-20]提供非常不同的*逻辑*模型来进行数据结点的展现、处理及存储。

简单的YAML文件（例如：简单的键值对）不需要完整的[YAML分析器](https://codifyformatter.org/yaml-parser-online) （[页面存档备份](https://web.archive.org/web/20250126144948/https)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")），便可以被[正则表达式](https://zh.wikipedia.org/wiki/%E6%AD%A3%E5%89%87%E8%A1%A8%E9%81%94%E5%BC%8F "正则表达式")解析。许多常用的编程语言──纯用某个语言，让函数库具有可携性──都有的YAML的产生器和分析器。当性能比较重要时，也有许多和C语言绑定的函数库可使用。

- libYAML[^21] 2007-06时，这个YAML的函数库渐趋稳定，并被YAML格式作者推荐[^22]。
- SYCK[^23] 这个实现支持大部分1.0版的格式，并且被广泛的使用。它使用高阶[解释型语言](https://zh.wikipedia.org/wiki/%E8%A7%A3%E9%87%8A%E5%9E%8B%E8%AF%AD%E8%A8%80 "解释型语言")进行优化。在2005之后，这个项目已经不再更新，不过仍可使用。

下面几种编程语言都有与YAML相关的函数库:

- [C++](https://zh.wikipedia.org/wiki/C%2B%2B "C++")
- 用C++将libYaml包装[^24]
- [Go](https://zh.wikipedia.org/wiki/Go "Go")
- go-yaml[^25] 借鉴 C 库 libyaml 设计的 Go 语言移植。
- [Haskell](https://zh.wikipedia.org/wiki/Haskell "Haskell")
- Haskell Reference wrappers[^26]
- [Java](https://zh.wikipedia.org/wiki/Java "Java")
- jvyaml[^27] 以Syck为基础设计。
- JYaml[^28] 纯Java的实现。
- [JavaScript](https://zh.wikipedia.org/wiki/JavaScript "JavaScript")
- 原生的JavaScript即可产生YAML，但不能解析。
- YAML JavaScript[^29] 同时支持产生和解析。
- [Objective-C](https://zh.wikipedia.org/wiki/Objective-C "Objective-C")
- Cocoa-Syck[^30]
- [OCaml](https://zh.wikipedia.org/wiki/OCaml "OCaml")
- OCaml-Syck[^31]
- [Lua](https://zh.wikipedia.org/wiki/Lua "Lua")
- Lua-Syck[^32]
- [Perl](https://zh.wikipedia.org/wiki/Perl "Perl")
- CPAN YAML[^33] 一个通用的接口，被数个YAML解析器使用。
- YAML::Tiny[^34] YAML简化版的实现。拥有小巧轻快的优点──比完整功能的YAML实现快上许多，并用纯Perl写成。
- YAML::Syck[^35] 与SYCK函数库绑定。提供快速、功能丰富（highly featured）的YAML解析器。
- YAML::XS[^36] 与LibYaml绑定。提供1.1版更好的兼容性。
- [PHP](https://zh.wikipedia.org/wiki/PHP "PHP")
- Spyc[^37] 纯PHP的实现。
- PHP-Syck[^38]（与SYCK函数库绑定）
- sfYaml[^39] 为[symfony](https://zh.wikipedia.org/wiki/Symfony "Symfony")项目重写的Spyc, 可独立使用，可以产生和解析YAML文件。
- [Python](https://zh.wikipedia.org/wiki/Python "Python")
- PyYaml[^40] 纯Python，或可选用LibYAML的函数库。
- PySyck[^41] 与SYCK绑定。
- [Ruby](https://zh.wikipedia.org/wiki/Ruby "Ruby")（从1.8版开始，YAML解析器成为标准函数库之一。以SYCK为基础。）
- Ya2YAML[^42] 具有完全的[UTF-8](https://zh.wikipedia.org/wiki/UTF-8 "UTF-8")支持
- [R](https://zh.wikipedia.org/wiki/R%E8%AF%AD%E8%A8%80 "R语言")
- CRAN YAML[^43] 以SYCK为基础。
- [.NET](https://zh.wikipedia.org/wiki/.NET ".NET")
- .NET Parser[^44]
- YamlDotNet [^45]
- [Scala](https://zh.wikipedia.org/wiki/Scala "Scala")
- scala-yaml[^46]
- [Tcl](https://zh.wikipedia.org/wiki/Tcl "Tcl")
- 在Tcl 8.4中可用[^47]
- [XML](https://zh.wikipedia.org/wiki/XML "XML") YAXML[^48] (当前仍在设计中)

- **编辑器：**
- 建议使用能将跳格字符自动转换成空白字符的编辑器，并且使用定宽度的字体。
- 编辑器要能正确的处理UTF-8和UTF16编码（或是使用纯[ASCII](https://zh.wikipedia.org/wiki/ASCII "ASCII")编码──它同时是UTF-8的子集）.
- **字符串：**
- YAML的字符串不需使用引号，这可以增加可读性，并避免嵌套的转义字符。然而，这有时也会导致错误，例如，字符串本身是一个暧昧的字眼（像数字或布尔值）；或在短句中意外的出现YAML的结构符号（常见的例子是由惊叹号起始的句子，或是包含冒号-空白的句子："`!Caca de vaca!`"、"`Caution: lions ahead`"）。这在发布YAML文件时并不造成困扰，但在制作小型脚本和人工编辑文件时，这问题却会常常出现。比较好的方法是善用区块符号（"|" or ">"）而不要使用单行字符串，来避免这种暧昧的表示方法。
- **预期实做的特性**

其他标记语言：

- [JSON](https://zh.wikipedia.org/wiki/JSON "JSON")，可以说是YAML的子集。
- [XML](https://zh.wikipedia.org/wiki/XML "XML")
- [Simple Outline XML](https://zh.wikipedia.org/w/index.php?title=Simple_Outline_XML&action=edit&redlink=1 "Simple Outline XML（页面不存在）")
- [OGDL](https://zh.wikipedia.org/w/index.php?title=OGDL&action=edit&redlink=1 "OGDL（页面不存在）")
- [S-表达式](https://zh.wikipedia.org/wiki/S-%E8%A1%A8%E8%BE%BE%E5%BC%8F "S-表达式")
- [Plist](https://zh.wikipedia.org/wiki/Plist "Plist")，由[NEXTSTEP](https://zh.wikipedia.org/wiki/NEXTSTEP "NEXTSTEP")改写成的数据序列语言。
- [SDL](https://zh.wikipedia.org/w/index.php?title=Simple_Declarative_Language&action=edit&redlink=1 "Simple Declarative Language（页面不存在）")

[^rfc9512-1]: Polli, Roberto; Wilde, Erik; Aro, Eemeli. [YAML Media Type](https://datatracker.ietf.org/doc/rfc9512/) (报告). Internet Engineering Task Force. 2024-02-21 \[2024-02-21\]. （原始内容[存档](https://web.archive.org/web/20240221185855/https://datatracker.ietf.org/doc/rfc9512/)于2024-02-21）.

[^2]: [2822](http://www.rfc-editor.org/rfc/rfc2822.txt) （[页面存档备份](https://web.archive.org/web/20220514042645/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^3]: Evans, Clark. [YAML Draft 0.1](https://web.archive.org/web/20130907042053/http://tech.groups.yahoo.com/group/sml-dev/message/4710). Yahoo! Tech groups(雅虎技术组群): sml-dev. 2001-05-11 \[2008-08-02\]. （[原始内容](http://tech.groups.yahoo.com/group/sml-dev/message/4710)存档于2013-09-07）.

[^4]: [YAML Ain't Markup Language: About](https://web.archive.org/web/20220403004031/http://yaml.org/about.html). \[2010-06-16\]. （[原始内容](http://www.yaml.org/about.html)存档于2022-04-03）.

[^yaml_spec_2001_08_01-5]: [Yet Another Markup Language (YAML) 1.0](https://web.archive.org/web/20220306093951/https://yaml.org/spec/history/2001-08-01.html). \[2008-11-24\]. （[原始内容](http://yaml.org/spec/history/2001-08-01.html)存档于2022-03-06）.

[^vartype000-6]: 在英文原文中，将下列几组词汇交替使用：(清单"list"和数组"array"), (散列表"hash"、字典"dictionary"、映射"mapping")和(字符串"string"和标量"scalar")。在其他编程语言，这几组字的意义未必等价。中文则统一使用相同的词汇。

[^relationalnote000-7]: 层次结构式(hierarchical model)对应到树状结构时，只会有一个固定、整体性的结果。举例说明：用层次结构式来表达电影的演员名单，每个演员都只能归类到一个电影名称；或是每个电影只能归类给一位演员(虽然这样很怪)。YAML同时也允许使用关系式数据(relational model)。

[^8]: [存档副本](https://web.archive.org/web/20080914015703/http://redhanded.hobix.com/inspect/yamlIsJson.html). \[2013-05-15\]. （[原始内容](http://redhanded.hobix.com/inspect/yamlIsJson.html)存档于2008-09-14）.

[^9]: [yaml.org](http://yaml.org/) （[页面存档备份](https://web.archive.org/web/20220515165215/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^10]: [小抄](http://yaml.org/refcard.html) （[页面存档备份](https://web.archive.org/web/20220303001324/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^11]: [格式说明](http://yaml.org/spec/) （[页面存档备份](https://web.archive.org/web/20220120221209/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^12]: [YAML 1.2 Spec](http://yaml.org/spec/1.2/). \[2008-12-01\]. （原始内容[存档](https://web.archive.org/web/20080516232502/http://yaml.org/spec/1.2/)于2008-05-16）.

[^13]: 这些语法非常细微且很少出现在文件中：JSON允许扩展字符集，如：UTF32；YAML在分隔符号──如引号、等号、冒号──后方需要接空白字符，而JSON不需要；一些非标准的JSON实现允许Javascript风格的的大范围注解*/\*...\*/*。处理这种边界情形或许需要在将其当成内置格式的YAML剖析前进行简单的JSON前处理。

[^14]: [用SYCK剖析JSON](http://redhanded.hobix.com/inspect/yamlIsJson.html). \[2008-09-28\]. （原始内容[存档](https://web.archive.org/web/20080914015703/http://redhanded.hobix.com/inspect/yamlIsJson.html)于2008-09-14）.

[^15]: [存在](http://www.kuwata-lab.com/kwalify/) （[页面存档备份](https://web.archive.org/web/20210812231831/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^16]: [XML IDREF](https://web.archive.org/web/20220515043139/http://www.w3.org/TR/2000/REC-xml-20001006#idref). \[2008-09-28\]. （[原始内容](http://www.w3.org/TR/2000/REC-xml-20001006#idref)存档于2022-05-15）.

[^17]: 提案中的"yield"(迭代器)标签可以允许简单的算术运算

[^xml_1.0-18]: [Extensible Markup Language (XML) 1.0 (第四版)](http://www.w3.org/TR/REC-xml/). \[2007-11-04\]. （原始内容[存档](https://web.archive.org/web/20200110151249/http://www.w3.org/TR/REC-xml/)于2020-01-10）.

[^xml_1.1-19]: [Extensible Markup Language (XML) 1.1 (第二版)](https://web.archive.org/web/20210419133700/https://www.w3.org/TR/xml11/). \[2007-11-04\]. （[原始内容](http://www.w3.org/TR/xml11/)存档于2021-04-19）.

[^yaml_spec-20]: [YAML Ain't Markup Language (YAML) Version 1.1](https://web.archive.org/web/20220501053052/http://yaml.org/spec/current.html). \[2007-11-04\]. （[原始内容](http://yaml.org/spec/current.html)存档于2022-05-01）.

[^21]: [libYAML](http://pyyaml.org/wiki/LibYAML) （[页面存档备份](https://web.archive.org/web/20220407050602/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^22]: YAML的创造者Clark Evans推荐

[^23]: [SYCK](http://whytheluckystiff.net/syck/) （[页面存档备份](https://web.archive.org/web/20090803174140/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^24]: [用C++将libYaml包装](http://git.snoyman.com/cppweb.git?a=blob;f=src/cppmodels/yaml.hpp;h=e67377c792309a51eb5a4c9dac05ba89befd38d6;hb=HEAD)<sup class="noprint Inline-Template"><span>[<a href="https://zh.wikipedia.org/wiki/Wikipedia:%E5%A4%B1%E6%95%88%E9%93%BE%E6%8E%A5" title="Wikipedia:失效链接"><span title="自2017年11月失效">永久失效链接</span></a>]</span></sup>

[^25]: [go-yaml](https://github.com/go-yaml/yaml) （[页面存档备份](https://web.archive.org/web/20220426092622/https)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^26]: [Haskell Reference wrappers](https://web.archive.org/web/20080803050852/http://www.ben-kiki.org/oren/YamlReference/)

[^27]: [jvyaml](https://web.archive.org/web/20081121204521/http://jvyaml.dev.java.net/)

[^28]: [JYaml](https://web.archive.org/web/20081225033223/http://jyaml.sourceforge.net/)

[^29]: [YAML JavaScript](http://sourceforge.net/projects/yaml-javascript) （[页面存档备份](https://web.archive.org/web/20210313050647/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^30]: [Cocoa-Syck](https://web.archive.org/web/20070927213458/http://code.whytheluckystiff.net/syck/browser/trunk/ext/cocoa/src)

[^31]: [OCaml-Syck](http://sourceforge.net/projects/ocaml-syck/) （[页面存档备份](https://web.archive.org/web/20200630031720/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^32]: [Lua-Syck](https://web.archive.org/web/20080923161342/http://code.whytheluckystiff.net/syck/browser/trunk/ext/lua)

[^33]: [CPAN YAML](https://search.cpan.org/dist/YAML) （[页面存档备份](https://web.archive.org/web/20180604182707/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^34]: [YAML::Tiny](https://search.cpan.org/dist/YAML-Tiny/) （[页面存档备份](https://web.archive.org/web/20180520021623/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^35]: [YAML::Syck](https://search.cpan.org/dist/YAML-Syck/) （[页面存档备份](https://web.archive.org/web/20180520041607/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^36]: [YAML::XS](https://search.cpan.org/dist/YAML-LibYAML/) （[页面存档备份](https://web.archive.org/web/20180520003853/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^37]: [Spyc](https://web.archive.org/web/20081218100022/http://spyc.sourceforge.net/)

[^38]: [PHP-Syck](http://pecl.php.net/package/syck) （[页面存档备份](https://web.archive.org/web/20220206175647/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^39]: [sfYaml](https://web.archive.org/web/20080922222034/http://trac.symfony-project.org/browser/branches/1.1/lib/yaml)

[^40]: [PyYaml](http://pyyaml.org/). \[2008-09-28\]. （原始内容[存档](https://web.archive.org/web/20080917043822/http://www.pyyaml.org/wiki/PySyck)于2008-09-17）.

[^41]: [PySyck](https://pypi.org/project/PySyck/). \[2022-06-03\]. （原始内容[存档](https://web.archive.org/web/20210511011611/https://pypi.org/project/PySyck/)于2021-05-11）.

[^42]: [Ya2YAML](https://web.archive.org/web/20081012115015/http://rubyforge.org/projects/ya2yaml/)

[^43]: [CRAN YAML](http://biostat.mc.vanderbilt.edu/twiki/bin/view/Main/YamlR) （[页面存档备份](https://web.archive.org/web/20120309022757/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^44]: [YAML .NET Parser](http://yaml-net-parser.sourceforge.net/) （[页面存档备份](https://web.archive.org/web/20090324201434/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^45]: [YamlDotNet 12.0.0](https://www.nuget.org/packages/YamlDotNet/). www.nuget.org. \[2022-09-14\]. （原始内容[存档](https://web.archive.org/web/20220916033811/https://www.nuget.org/packages/YamlDotNet)于2022-09-16） （英语）.

[^46]: [scala-yaml](https://github.com/yaml/scala-yaml) （[页面存档备份](https://web.archive.org/web/20200930204556/https)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

[^47]: [在Tcl 8.4中可用](https://web.archive.org/web/20150515083439/http://tcllib.sourceforge.net/doc/yaml.html)

[^48]: [YAXML](http://yaml.org/xml.html) （[页面存档备份](https://web.archive.org/web/20201024011628/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）

- [YAML.org](http://yaml.org/) （[页面存档备份](https://web.archive.org/web/20220515165215/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [YAML Specification](http://yaml.org/spec/) （[页面存档备份](https://web.archive.org/web/20220120221209/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [YAML Cookbook--Equivalent data structures in YAML and Ruby](https://web.archive.org/web/20080509211926/http://yaml4r.sourceforge.net/cookbook/)
- [YAML in Five Minutes](http://yaml.kwiki.org/?YamlInFiveMinutes) （[页面存档备份](https://web.archive.org/web/20060618031422/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [YAML improves on XML](http://www.ibm.com/developerworks/library/x-matters23.html) （[页面存档备份](https://web.archive.org/web/20160614090817/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")） Intro to YAML in Python
- [YAML as a superset of JSON](https://web.archive.org/web/20080914015703/http://redhanded.hobix.com/inspect/yamlIsJson.html)
- [Kwalify Schema definition for YAML](http://www.kuwata-lab.com/kwalify/) （[页面存档备份](https://web.archive.org/web/20210812231831/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [Lists in 5 minutes](http://list.alwayspages.com/info/listsin5mins) （[页面存档备份](https://web.archive.org/web/20200930174656/http)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）
- [YAML Validator](https://codebeautify.org/yaml-validator) （[页面存档备份](https://web.archive.org/web/20141105141628/https)，存于[互联网档案馆](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E6%A1%A3%E6%A1%88%E9%A6%86 "互联网档案馆")）