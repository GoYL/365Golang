# 《365天深入理解Golang》

## 0x01-项目说明 

这是一份自己准备用365天深入理解Golang之后送给自己的礼物。本项目记录365天内的学习收获。

本人编程零基础，只略懂一些Python。因此本项目部分章节可能很基础，请见谅。

本项目大量参考复制借鉴了其他类似项目。感谢这些作者们，感谢Gopher。

关于Go的其他资源，参考此项目：[https://github.com/0e0w/LearnGolang](https://github.com/0e0w/LearnGolang)

本项目创建于2020年9月1日，最近的一次更新日期为2020年9月17日。

项目不定期推到重来，暂时取消更新的最新提示。

~~已经更新至第一章Day013: 函数-Go语言函数~~

## 0x02-学习进度

### 第一章：Go语言基础

<details>
<summary>Day001: 基础-Go语言入门</summary>

- [x] 本节说明：介绍Go语言的历史，发展。

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它可以容易的构造简单、可靠且高效的软件。 Go是在2007年末由Robert Griesemer, Rob Pike, Ken Thompson主持开发，后来加入了Ian Lance Taylor, Russ Cox等人。最终于2009年11月开源。在2012年早些时候发布了Go 1稳定版本。现在Go的开发已经是完全开放的，并且拥有一个活跃的社区。
  - Go语言是编译型的开源的程序设计语言。编译器、库和工具的源代码可以免费获得。
  - Go语言有垃圾回收、有包系统、有一等公民函数、有词法作用域、有系统调用接口等。
  - Go语言没有构造或析构函数、没有运算符重载、没有形参默认值、没有泛型、没有异常、没有宏、没有函数注解、没有线程局部存储。Go没有类继承，甚至没有类。
  - Go语言以一种不同寻常的方式来诠释面向对象程序设计。
  - Go语言不需要在语句或声明后面是有分号结尾。

- [ ] Go语言特点：Go语言和其他语言相比的优势是什么？（待补充）

  - 并发性

- [x] Go语言官网：官网有大量的教程和代码想项目案例。是学习的首选地方。

  - https://golang.org
  - https://github.com/golang
  - https://github.com/0e0w/LearnGolang

- [x] Go语言安装：

  - [官网下载](https://golang.org/dl/)之后直接按照安装说明安装即可。作者在Ubuntu虚拟机里面开发使用Go语言。

    ```
    wget https://golang.google.cn/dl/go1.15.2.linux-amd64.tar.gz
    tar -C /usr/local -xzf go1.15.2.linux-amd64.tar.gz
    ```

- [x] Go环境变量：

  - 设置GOPATH。

    ```
    mkdir ~/.go
    echo "GOPATH=$HOME/.go" >> ~/.bashrc
    echo "export GOPATH" >> ~/.bashrc
    echo "PATH=\$PATH:\$GOPATH/bin # Add GOPATH/bin to PATH for scripting" >> ~/.bashrc
    source ~/.bashrc
    ```

- [x] Go语言编辑器：

  - [Goland](https://www.jetbrains.com/go)：JetBrains 公司的 Go 开发工具。
  - [LiteIDE](http://liteide.org)：一款开源跨平台轻量级的Go语言IDE。
  - [Atom](https://atom.io)：一款跨平台开源文本编辑器。
  
- [x] Go语言基础命令：

  - go run hello.go //编译运行hello.go

  - go bulid hello.go //将hello打包成可执行文件

  - 执行下列命令前需要配置好GOPATH路径。

    ```
    //Windows下编译Mac, Linux平台的64位可执行程序：
    CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build 001.go
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build 001.go
    ```

    ```
    //Linux下编译Mac, Windows平台的64位可执行程序：
    CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build 001.go
    CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build 001.go
    ```

    ```
    //Mac下编译Linux, Windows平台的64位可执行程序：
    CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build 001.go
    CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build 001.go
    ```

  - ```
    go get github.com/0e0w/365GoLang //使用go get之前需要安装git。
    ```

  - ```
    gofmt //格式化Go代码
    ```

  - ```
    go env //查看Go环境配置
    ```

- [x] Go语言代理：

  - Go语言大量项目托管于Github，导致国内进行构建程序时会出奇的慢。可使用下列的代理加快构建。

    ```
    https://mirrors.aliyun.com/goproxy/
    https://goproxy.io/zh/
    ```
    
    ```
    go env -w GO111MODULE=on
    go env -w GOPROXY=https://goproxy.cn,direct
    ```

- [x] Go语言未来：

  - Go语言拥有大量的优秀社区框架。
  
- Go语言的未来发展前景是光明的。
  
  </details>
<details>
<summary>Day002: 基础-Go语言例子</summary>

- [x] 本节说明：通过一个简单例子认识Go语言的基本结构。

- [x] 一个例子：Hello World！

  ```go
  // 001
  package main
  
  import (
  	"fmt"
  )
  
  func main() {
  	fmt.Println("Hello World!")
  }
  ```


  - 包声明：package main表示一个可独立执行的程序，每个 Go 应用程序都包含一个名为 main 的包。
  - 引入包：使用import圆括号进行引入包。
    - 引入标准包
    - 引入第三方包
  - 函数：使用func定义
  - 变量
  - 常量
  - 语句
  - 表达式
  - 注释
- [x] 名称：

  - 程序一般由关键字、常量、变量、运算符、类型和函数组成。 程序中可能会使用到这些分隔符：括号 ()，中括号 [] 和大括号 {}。 程序中可能会使用到这些标点符号：.、,、;、: 和 …。
  - 在变量与运算符间加入空格，程序看起来更加美观。


  - 标识符：用来命名变量、类型等程序实体。一个标识符就是一个或是多个字母( A ~ Z 和 a ~ z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。

  - 关键字：25个关键字或保留字。只能用在语法允许的地方，不能作为名称使用。

    | break    | default     | func   | interface | select |
    | -------- | ----------- | ------ | --------- | ------ |
    | case     | defer       | go     | map       | struct |
    | chan     | else        | goto   | package   | swith  |
    | const    | fallthrough | if     | range     | type   |
    | continue | for         | import | return    | var    |

   - 预定义标识符：三十几个内置的预申明的常量、类型和函数。

     - 常量：true、flase、iota、nil
     - 类型：int、int8、int16、int32、int64、uint、uint8、uint16、uint32、uint64、uintptr、float32、float64、complex128、complex64、bool、byte、rune、string、error
     - 函数：make、len、cap、new、append、copy、close、delete、complex、real、imag、panic、recover

- [x] 声明：
  
   - 声明是给一个程序实体命名，并设定其部分或全部属性。
   - 有4个主要的声明：
     - 变量（var）
     - 常量（const）
     - 类型（type）
     - 函数（func）
   
   - 函数的声明包含一个名字、一个参数列表、一个可选的返回值列表以及函数体。
   
- [x] 本节案例：

   ```go
   // 002
   package main
   
   import (
   	"fmt"
   )
   
   func main() {
   	fmt.Println("Hello World!")
   }
   ```

</details>
<details>
<summary>Day003: 基础-Go约定惯例</summary>

- [x] 本节说明：本节介绍Go语言中约定和惯例。

- [x] 可见性规则：

  - 在Go语言中，标识符必须以一个大写字母开头，这样才可以被外部包的代码所使用，这被称为导出。标识符如果以小写字母开头，则对包外是不可见的，但是他们在整个包的内部是可见并且可用的。但是包名不管在什么情况下都必须小写。
  - 在设计Go语言时，设计者们也希望确保它不是过于以ASCII为中心，这意味着需要从7位ASCII的范围来扩展标识符的空间。 所以Go语言标识符规定必须是Unicode定义的字母或数字，标识符是一个或多个Unicode字母和数字的序列， 标识符中的第一个字符必须是Unicode字母。
  - 总而言之，为了确保我们的标识符能正常导出，我们建议在开发中还是尽量使用ASCII 码来作为标识符，虽然设计者们在避免以ASCII 码为中心，但出于习惯我们还是服从于这个现实。

- [x] 命名规范：

  - 当某个函数需要被外部包调用的时候需要使用大写字母开头，并遵循 Pascal 命名法（“大驼峰式命名法”）；否则就遵循“小驼峰式命名法”，即第一个单词的首字母小写，其余单词的首字母大写。
  - 单词之间不以空格断开或连接号（-）、底线（_）连结，第一个单词首字母采用大写字母；后续单词的首字母亦用大写字母，例如：FirstName、LastName。每一个单词的首字母都采用大写字母的命名格式，被称为“Pascal命名法”，源自于Pascal语言的命名惯例，也有人称之为“大驼峰式命名法”（Upper Camel Case），为驼峰式大小写的子集。
  - Go 语言追求简洁的代码风格，并通过 gofmt 强制实现风格统一。
  
- [x] 语法惯例：

  - Go 语言也使用分号作为语句的结束，但一般会省略分号。像在标识符后面；整数、浮点、复数、Rune或字符串等字面量后面；关键字break、continue、fallthrough、或者return后面；操作符或标点符号++、--、)、]或}之后等等都可以使用分号，但是往往会省略掉，像LiteIDE编辑器会在保存.go文件时自动过滤掉这些分号，所以在Go语言开发中一般不用过多关注分号的使用。
  - 左大括号 { 不能单独一行，这是编译器的强制规定，否则你在使用 gofmt 时就会出现错误提示“ expected declaration, found '{' ”。右大括号 } 需要单独一行。
  - 在定义接口名时也有惯例，一般单方法接口由方法名称加上-er后缀来命名。

- [x] 注释：

  - 行注释：使用双斜线//开始，一般后面紧跟一个空格。行注释是Go语言中最常见的注释形式，在标准包中，一般都采用行注释，建议采用这种方式。
  - 块注释：使用 /* */，块注释不能嵌套。块注释一般用于包描述或注释成块的代码片段。

  </details>
<details>
<summary>Day004: 数据-Go语言变量</summary>

- [x] 本节说明：Go语言变量的使用。

- [x] 基本描述：

  - Go 语言变量标识符由字母、数字、下划线组成，其中首个字母不能为数字，同一字母的大小写在Go语言中代表不同标识，注意区分A 和a 是不同的标识。
  - Go语言规范中，下划线“_”也被认为是字母。

- [x] 变量声明：

  - Go语言变量有2种声明方式，var申明和短变量声明。

    ```go
    var (
        a int
        b bool
        str string
        浮点 float32    // 中文可以作为变量标识符
    )
    ```

  - 声明变量之后，变量会自动初始化。初始值对应类型的零值。当一个变量被var声明之后，系统自动赋予它该类型的零值：

    - 数字类型对应的是0
    - 布尔类型对应的是flase
    - 字符串类型对应的是""
    - 接口和引用类型对应的是nil

    ```go
    var name type = expression
    var i, j, k int
    var b, f, s, = true, 2.3, "four" 
    ```

- [x] 短变量声明：

  - 简式声明一般用在func内，要注意的是：全局变量和简式声明的变量尽量不要同名，否则很容易产生偶然的变量隐藏Accidental Variable Shadowing。

  - name := expression

    ```go
    a, b, c := 5, 7, "abc"  // 注意等号前的冒号
    ```

- [x] 变量赋值：

  - 多变量可以在同一行进行赋值，也称为并行或同时或平行赋值。

    ```go
    a, b, c = 5, 7, "abc"
    ```

  - 并行赋值也被用于当一个函数返回多个返回值时，比如这里的 val 和错误 err 是通过调用 Func1 函数同时得到：

    ```go
    val, err = Func1(var1)
    ```

- [x] 空白标识符 _ ：

  - 空白标识符 _ 也被用于抛弃值，如值 5 在：_, b = 5, 7 中被抛弃。
  - _ 实际上是一个只写变量，你不能得到它的值。这样做是因为 Go 语言中你必须使用所有被声明的变量，但有时你并不需要使用从一个函数得到的所有返回值。
  - 由于Go语言有个强制规定，在函数内一定要使用声明的变量，但未使用的全局变量是没问题的。为了避免有未使用的变量，代码将编译失败，我们可以将该未使用的变量改为 _。
  - 另外，在Go语言中，如果引入的包未使用，也不能通过编译。有时我们需要引入的包，比如需要init()，或者调试代码时我们可能去掉了某些包的功能使用，你可以添加一个下划线标记符，_，来作为这个包的名字，从而避免编译失败。下滑线标记符用于引入，但不使用。

- [x] 零值nil：

  - nil 标志符用于表示interface、函数、maps、slices、channels、error、指针等的“零值”。如果你不指定变量的类型，编译器将无法编译你的代码，因为它猜不出具体的类型。

- [ ] 本节案例：

  </details>
<details>
<summary>Day005: 数据-Go语言常量</summary>

- [x] 本节说明：Go语言常量使用。

- [x] 常量说明：

  - 常量使用关键字 const 定义，用于存储不会改变的数据。
    - 常量不能被重新赋予任何值。常量在程序运行时，不会被修改的量。
    - 常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。
    - 常量之所以为常量就是恒定不变的量，因此我们无法在程序运行过程中修改它的值；如果你在代码中试图修改常量的值则会引发编译错误。同时，在const 定义中，对常量名没有强制要求全部大写，不过我们一般都会全部字母大写，以便阅读。
  
- [x] 常量定义：

  - 常量的定义格式：const identifier [type] = value，例如：

    ```go
    const Pi = 3.14159
    ```
    
  - Go的常量定义可以限定常量类型，但不是必需的。如果定义常量时没有指定类型，那么它与字面常量一样，是无类型（untyped）常量。
    
  - 一个没有指定类型的常量被使用时，会根据其使用环境而推断出它所需要具备的类型。换句话说，未定义类型的常量会在必要时刻根据上下文来获得相关类型。
    
    ```
    显式类型定义：const b string = "abc"
    隐式类型定义：const b = "abc"
    ```
  ```
    
  - 常量也可以在单行进行多重赋值：
  
    ```go
    const a, b, c = 1, false, "str" //多重赋值
  ```

- [x] iota： 特殊常量

  - iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。

  - iota 可以被用作枚举值。第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1。

     ```go
     const (
         a = iota
         b = iota
         c = iota
     )
     ```

     第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：

     ```go
     const (
         a = iota
         b
         c
     )
     ```

     如果对b重新赋值之后，a, b, c分别为0, 8, 8，新的常量b声明后，iota 不再向下赋值，后面常量如果没有赋值，则继承上一个常量值。

     ```go
     const (
         a = iota
         b = 8
         c
     )
     ```

     使用位左移与 iota 计数配合可优雅地实现存储单位的常量枚举：

     ```go
     type ByteSize float64
     const (
         _ = iota // 通过赋值给空白标识符来忽略值
         KB ByteSize = 1<<(10*iota)
         MB
         GB
         TB
         PB
         EB
         ZB
         YB
     )
     ```

     一个例子：

     ```go
      const (
          i=1<<iota
          j=3<<iota
          k
          l
      )
     //i= 1 j= 6 k= 12 l= 24
     //iota 表示从 0 开始自动加 1，所以 i=1<<0, j=3<<1（<< 表示左移的意思）
     //即：i=1, j=6，这没问题，关键在 k 和 l，从输出结果看 k=3<<2，l=3<<3。
     ```

- [x] 本节案例：

  

  </details>
<details>
<summary>Day006: 数据-Go基本数据</summary>

- [x] 本节说明：本节介绍Go语言的一些基本数据。

- [x] 基本数据：

  - 在 Go 编程语言中，数据类型用于声明函数和变量。
  - 数据类型的出现是为了把数据分成所需内存大小不同的数据，编程的时候需要用大数据的时候才需要申请大内存，就可以充分利用内存。

- [x] 布尔型：

  - 布尔型的值只可以是常量 true 或者 false。一个简单的例子：var b bool = true。
  
- [x] 数字类型：

  - 整型 int 和浮点型 float32、float64，Go 语言支持整型和浮点型数字，并且支持复数，其中位的运算采用补码。

- [x] 字符串类型：

  - Go 语言中可以使用反引号或者双引号来定义字符串。反引号表示原生的字符串，即不进行转义。
  - 字符串就是一串固定长度的字符连接起来的字符序列。Go 的字符串是由单个字节连接起来的。Go 语言的字符串的字节使用 UTF-8 编码标识 Unicode 文本。
  - Go 语言中的string类型是一种值类型，存储的字符串是不可变的，如果要修改string内容需要将string转换为[]byte或[]rune，并且修改后的string内容是重新分配的。
  - 字符串的零值是为长度为零的字符串，即空字符串 ""。
  - 一般的比较运算符（==、!=、<、<=、>=、>）通过在内存中按字节比较来实现字符串的对比。可以通过函数 len() 来获取字符串所占的字节长度，例如：len(str)。
  - 字符串的内容（纯字节）可以通过标准索引法来获取，在中括号 [] 内写入索引，索引从 0 开始计数。
  - 字符串拼接：
    - 直接使用运算符
    - fmt.Sprintf()
    - strings.Join()
    - bytes.Buffer
    - strings.Builder

  - 标准库中有四个包对字符串处理尤为重要：bytes、strings、strconv和unicode包。

- [x] 本节案例：

  

  </details>
<details>
<summary>Day007: 数据-Go语言数组</summary>

- [x] 本节说明：本节介绍Go语言数组的相关内容。

- [x] Array介绍：

  - 数组是具有相同类型的一组已知编号并且长度固定的数据项序列。一个数组可以由零个或多个元素组成。
  - 数组类型可以是任意的原始类型例如整型、字符串或者自定义类型。
  - 数组长度必须是一个常量表达式，并且必须是一个非负整数。
  - 因为数组的长度是固定的，所以在Go语言中很少直接使用数组。
  - 数组长度也是数组类型的一部分，所以[5]int和[10]int是属于不同类型的。
  
- [x] 声明数组：

  - Go 语言数组声明需要指定元素类型及元素个数，语法格式如下：

    ```go
    var 数组变量名 [元素数量]Type
    var a [3]int             // 定义三个整数的数组
    ```
  
- [x] 初始化数组：

  - 初始化数组中 {} 中的元素个数不能大于 [] 中的数字。

- [x] 访问数组元素：

  - 数组元素可以通过索引（位置）来读取。格式为数组名后加中括号，中括号中为索引的值。

    ```go
    var team [3]string
    team[0] = "hammer"
    team[1] = "soldier"
    team[2] = "mum"
    for k, v := range team {
        fmt.Println(k, v)
    }
    ```

- [ ] 多维数组：

- [ ] 向函数传递数组：

- [x] 本节案例：

  

  </details>

<details>
<summary>Day008: 数据-Go语言切片</summary>

- [x] 本节说明：本节介绍Go语言切片(slice)的相关内容。

- [x] Slice介绍：

  - Go 语言切片是对数组的抽象。
  - 切片是对底层数组一个连续片段的引用，所以切片是一个引用类型。
  - 切片提供对该数组中编号的元素序列的访问。未初始化切片的值为nil。
  - Go 数组的长度不可改变，但切片好比动态数组，可以追加元素，在追加时可能使切片的容量增大。
  - 因为切片是引用，不需要使用额外的内存且比使用数组更有效率，所以在Go代码中切片比数组更常用。
  
- [x] 定义切片：


  - 切片有俩种定义方式

    ```go
    var 切片变量名 []type // 声明一个未指定大小的数组来定义切片
    ```

    ```go
    var slice1 []type = make([]type, len,cap)
    // 使用make()函数来创建切片
    ```

- [x] 切片重组：

  - 通过改变切片长度得到新切片的过程称之为切片重组 reslicing。
  - 在一个切片基础上重新划分一个切片时，新的切片会继续引用原有切片的数组。
  - 为了避免这个陷阱，我们需要从临时的切片中使用内置函数copy()，拷贝数据到新切片。

- [ ] 切片初始化：

- [ ] 空(nil)切片：

- [ ] 本节案例：

  
  
  </details>
<details>
<summary>Day009: 数据-Go语言集合</summary>

- [x] 本节说明：本节介绍集合Go语言集合(Map)的相关内容。

- [x] Map介绍：

  - Map 是一种无序的键值对的集合。Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值。
  - Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。不过，Map 是无序的，我们无法决定它的返回顺序，这是因为 Map 是使用 hash 表来实现的。
  - 在声明的时候不需要知道 Map 的长度，Map 是可以动态增长的。
  
- [x] 定义Map：

  - 可以使用内建函数 make 也可以使用 map 关键字来定义 Map:

    ```go
    // 声明变量，默认 map 是 nil
    var map_variable map[key_data_type]value_data_type
    
    // 使用 make 函数
    map_variable := make(map[key_data_type]value_data_type)
    
    var m map[string]int
    
    // 声明但未初始化map，此时是map的零值状态
    map1 := make(map[string]string, 5)
    
    map2 := make(map[string]string)
    
    // 创建了初始化了一个空的的map，这个时候没有任何元素
    map3 := map[string]string{}
    
    // map中有三个值
    map4 := map[string]string{"a": "1", "b": "2", "c": "3"}
    ```

- [ ] 测试待删除：

  - go run hello.go //编译运行hello.go

- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day010: 数据-Go语言结构</summary>

- [x] 本节说明：本节介绍Go语言结构体(struct)的相关内容。

- [x] struct介绍：

  - Go语言通过结构体的形式支持用户自定义类型，或者叫定制类型。
  - Go语言结构体是实现自定义类型的一种重要数据类型。
  - 结构体是复合类型（composite types），它由一系列属性组成，每个属性都有自己的类型和值的，结构体通过属性把数据聚集在一起。
  - 结构体是由一系列具有相同类型或不同类型的数据构成的数据集合。结构体中可以定义不同类型的数据。
  - 方法（Method）可以访问这些数据，就好像它们是这个独立实体的一部分。

- [x] 定义结构体：

  - 结构体定义需要使用 type 和 struct 语句。struct 语句定义一个新的数据类型，结构体中有一个或多个成员。type 语句设定了结构体的名称。结构体的格式如下：

    ```go
    type struct_variable_type struct {
       member definition
       member definition
       ...
       member definition
    }
    ```

  - 结构体是由一系列称为字段（fields）的命名元素组成，每个元素都有一个名称和一个类型。 字段名称可以显式指定（IdentifierList）或隐式指定（EmbeddedField），没有显式字段名称的字段称为匿名（内嵌）字段。在结构体中，非空字段名称必须是唯一的。

    ```go
    type identifier struct {
        field1 type1
        field2 type2
        ...
    }
    ```

  - 一个空结构体：struct {}

  - 一旦定义了结构体类型，它就能用于变量的声明。

  - 结构体是值类型，因此也可以通过 new 函数来创建。

- [x] 访问结构体成员：

  - 如果要访问结构体成员，需要使用点号 . 操作符，格式为：

    ```go
    结构体.成员名
    ```

- [ ] 结构体特性：

  - 结构体的内存布局：Go 语言中，结构体和它所包含的数据在内存中是以连续块的形式存在的，即使结构体中嵌套有其他的结构体，这在性能上带来了很大的优势。

  - 递归结构体：递归结构体类型可以通过引用自身指针来定义。这在定义链表或二叉树的节点时特别有用，此时节点包含指向临近节点的链接。

  - 可见性：通过参考应用可见性规则，如果结构体名不能导出，可使用 new 函数使用工厂方法的方法达到同样的目的。

  - 带标签的结构体：结构体中的字段除了有名字和类型外，还可以有一个可选的标签（tag）。它是一个附属于字段的字符串，可以是文档或其他的重要标记。标签的内容不可以在一般的编程中使用，只有 reflect 包能获取它。

- [ ] 本节参考：[参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_18_struct.md)
  
- [x] 本节案例：
  
  ```go
  package main
  
  import (
  	"fmt"
  )
  
  type Human struct {
  	name   string // 姓名
  	Gender string // 性别
  	Age    int    // 年龄
  	string        // 匿名字段
  }
  
  type Student struct {
  	Human     // 匿名字段
  	Room  int // 教室
  	int       // 匿名字段
  }
  
  func main() {
  	//使用new方式
  	stu := new(Student)
  	stu.Room = 102
  	stu.Human.name = "Titan"
  	stu.Gender = "男"
  	stu.Human.Age = 14
  	stu.Human.string = "Student"
  
  	fmt.Println("stu is:", stu)
  	fmt.Printf("Student.Room is: %d\n", stu.Room)
  	fmt.Printf("Student.int is: %d\n", stu.int) // 初始化时已自动给予零值：0
  	fmt.Printf("Student.Human.name is: %s\n", stu.name) //  (*stu).name
  	fmt.Printf("Student.Human.Gender is: %s\n", stu.Gender)
  	fmt.Printf("Student.Human.Age is: %d\n", stu.Age)
  	fmt.Printf("Student.Human.string is: %s\n", stu.string)
  
  	// 使用结构体字面量赋值
  	stud := Student{Room: 102, Human: Human{"Hawking", "男", 14, "Monitor"}}
  
  	fmt.Println("stud is:", stud)
  	fmt.Printf("Student.Room is: %d\n", stud.Room)
  	fmt.Printf("Student.int is: %d\n", stud.int) // 初始化时已自动给予零值：0
  	fmt.Printf("Student.Human.name is: %s\n", stud.Human.name)
  	fmt.Printf("Student.Human.Gender is: %s\n", stud.Human.Gender)
  	fmt.Printf("Student.Human.Age is: %d\n", stud.Human.Age)
  	fmt.Printf("Student.Human.string is: %s\n", stud.Human.string)
  }
  ```
  
  </details> 
<details>
<summary>Day011: 数据-Go语言指针</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day012: 数据-Go语言通道</summary>

- [x] 本节说明：本节介绍Go语言通道(channel)的相关内容。

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day013: 数据-Go语言接口</summary>

- [x] 本节说明：本节介绍Go语言接口(interface)的相关内容。

- [x] interface介绍：

  - Go语言接口定义了一组方法集合，但是这些方法集合仅仅只是被定义，它们没有在接口中实现。
  
  - Go 语言中的所有类型包括自定义类型都实现了interface{}接口，所有的类型如string、 int、 int64甚至是自定义的结构体类型都拥有interface{}空接口，这一点interface{}和Java中的Object类比较相似。
  
  - 空接口interface{}可以被当做任意类型的数值。
  
  - 接口类型的未初始化变量的值为nil。
  
    ```go
    var i interface{} = 99 // i可以是任何类型
    i = 44.09
    i = "All"  // i 可接受任意类型的赋值
    ```
  
  - 接口是一组抽象方法的集合，它必须由其他非接口类型实现，不能自我实现。Go 语言通过它可以实现很多面向对象的特性。通过如下格式定义接口：
  
    ```go
    type Namer interface {
        Method1(param_list) return_type
        Method2(param_list) return_type
        ...
    }
    ```
  
- [ ] 接口嵌入：

  - 一个接口可以包含一个或多个其他的接口，但是在接口内不能嵌入结构体，也不能嵌入接口自身，否则编译会出错。
  
- [ ] 参考链接：[参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_19_interface.md)
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day014: 函数-Go语言函数</summary>

- [x] 本节说明：本节介绍Go语言函数相关内容。

- [x] Go函数介绍：

  - 函数是基本的代码块，用于执行一个任务。
  - Go 语言最少有个 main() 函数。
  - 函数声明告诉了编译器函数的名称，返回类型，和参数。
  - Go 语言标准库提供了多种可动用的内置的函数。例如，len() 函数可以接受不同类型参数并返回该类型的长度。如果我们传入的是字符串则返回字符串的长度，如果传入的是数组，则返回数组中包含的元素个数。
  
- [x] 函数定义：

  - Go语言函数基本组成：关键字func、函数名、参数列表、返回值、函数体和返回语句。语法如下：

    ```GO
    func function_name( [parameter list] ) [return_types] {
       函数体
    }
    //func：函数由 func 开始声明
    //function_name：函数名称，函数名和参数列表一起构成了函数签名。
    //parameter list：参数列表，参数就像一个占位符，当函数被调用时，你可以将值传递给参数，这个值被称为实际参数。参数列表指定的是参数类型、顺序、及参数个数。参数是可选的，也就是说函数也可以不包含参数。
    //return_types：返回类型，函数返回一列值。return_types 是该列值的数据类型。有些功能不需要返回值，这种情况下 return_types 不是必须的。
    //函数体：函数定义的代码集合。
    ```

- [ ] 函数调用：

  - 当创建函数时，你定义了函数需要做什么，通过调用该函数来执行指定任务。

  - 调用函数，向函数传递参数，并返回值。

    ```go
    package main
    import "fmt"
    func main() {
       /* 定义局部变量 */
       var a int = 100
       var b int = 200
       var ret int
       /* 调用函数并返回最大值 */
       ret = max(a, b)
       fmt.Printf( "最大值是 : %d\n", ret )
    }
    /* 函数返回两个数的最大值 */
    func max(num1, num2 int) int {
       /* 定义局部变量 */
       var result int
       if (num1 > num2) {
          result = num1
       } else {
          result = num2
       }
       return result
    }
    ```

- [ ] 函数返回多个值：

  - 一个例子：

    ```go
    package main
    import "fmt"
    func swap(x, y string) (string, string) {
       return y, x
    }
    func main() {
       a, b := swap("Google", "Runoob")
       fmt.Println(a, b)
    }
    ```

- [ ] 函数参数：

  - 函数如果使用参数，该变量可称为函数的形参。
  - 形参就像定义在函数体内的局部变量。
  - 调用函数，可以通过两种方式来传递参数：


  - 值传递：

    - 值传递是指在调用函数时将实际参数复制一份传递到函数中，这样在函数中如果对参数进行修改，将不会影响到实际参数。
    
  - 引用传递：

    - 引用传递是指在调用函数时将实际参数的地址传递到函数中，那么在函数中对参数所进行的修改，将影响到实际参数。

- [ ] 函数用法：

  - 函数作为另外一个函数的实参：
    - 函数定义后可作为另外一个函数的实参数传入。
  - 闭包：
    - 闭包是匿名函数，可在动态编程中使用。
  - 方法：
    - 方法就是一个包含了接受者的函数

- [x] Go语言命令：

  - go run hello.go //编译运行hello.go

- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day015: 数据-Go语言的包</summary>

- [ ] 本节说明：包、模块的相互关系？

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 待整理：[参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_07_package.md)、[参考2](https://github.com/ffhelicopter/Go42/blob/master/content/42_08_project.md)
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day016: 语句-Go运算符号</summary>

- [x] 本节说明：本节介绍Go运算符相关内容。

- [x] 算术运算符：

  | 算术运算符 | 描述 | 实例               |
  | :--------- | :--- | :----------------- |
  | +          | 相加 | A + B 输出结果 30  |
  | -          | 相减 | A - B 输出结果 -10 |
  | *          | 相乘 | A * B 输出结果 200 |
  | /          | 相除 | B / A 输出结果 2   |
  | %          | 求余 | B % A 输出结果 0   |
  | ++         | 自增 | A++ 输出结果 11    |
  | --         | 自减 | A-- 输出结果 9     |

- [x] 关系运算符：

  | 运算符 |                             描述                             | 实例              |
  | :----- | :----------------------------------------------------------: | :---------------- |
  | ==    |    检查两个值是否相等，如果相等返回 True 否则返回 False。    | (A == B) 为 False |
  | !=     |  检查两个值是否不相等，如果不相等返回 True 否则返回 False。  | (A != B) 为 True  |
  | >      |  检查左边值是否大于右边值，如果是返回 True 否则返回 False。  | (A > B) 为 False  |
  | <      |  检查左边值是否小于右边值，如果是返回 True 否则返回 False。  | (A < B) 为 True   |
  | >=    | 检查左边值是否大于等于右边值，如果是返回 True 否则返回 False。 | (A >= B) 为 False |
  | <=     | 检查左边值是否小于等于右边值，如果是返回 True 否则返回 False。 | (A <= B) 为 True |
  
- [x] 逻辑运算符：

  | 运算符 |  描述  |        实例        |
  | :----: | :----: | :----------------: |
  |   &&   | 逻辑与 | (A && B) 为 False  |
  |  \|\|  | 逻辑或 | (A \|\| B) 为 True |
  |   !    | 逻辑非 | !(A && B) 为 True  |
  
- [x] 位运算符：

  位运算符对整数在内存中的二进制位进行操作。 下表列出了位运算符 &，|，和 ^ 的计算：
  
  | p    | q    | p & q | p \| q | p ^ q |
  | :---  | :--- | :---- | :----- | :---: |
  | 0    | 0    | 0     | 0      |   0   |
  | 0    | 1    | 0     | 1      |   1   |
  | 1    | 1    | 1     | 1      |   0   |
  | 1    | 0    | 0     | 1      |   1   |
  
  | 运算符 |                    描述                     |                  实例                  |
  | :----: | :-----------------------------------------: | :------------------------------------: |
  |   &    | 其功能是参与运算的两数各对应的二进位相与。  | (A & B) 结果为 12, 二进制为 0000 1100  |
  |   \|   |  其功能是参与运算的两数各对应的二进位相或   | (A \| B) 结果为 61, 二进制为 0011 1101 |
  |   ^    | 二进位相异或，两对应的二进位相异时结果为1。 | (A ^ B) 结果为 49, 二进制为 0011 0001  |
  |   <<   |                                             | A << 2 结果为 240 ，二进制为 1111 0000 |
  |   >>   |                                             |       A >> 2 结果为 15 ，二进制        |
  
- [x] 赋值运算符：

  | 运算符 |       描述       |                 实例                  |
  | :----: | :--------------: | :-----------------------------------: |
  |   =    | 简单的赋值运算符 | C = A + B 将 A + B 表达式结果赋值给 C |
  |   +=   |   相加后再赋值   |         C += A 等于 C = C + A         |
  |   -=   |   相减后再赋值   |         C -= A 等于 C = C - A         |
  |   *=   |   相乘后再赋值   |         C *= A 等于 C = C * A         |
  |   /=   |   相除后再赋值   |         C /= A 等于 C = C / A         |
  |   %=   |   求余后再赋值   |         C %= A 等于 C = C % A         |
  |  <<=   |    左移后赋值    |        C <<= 2 等于 C = C << 2        |
  |  >>=   |    右移后赋值    |        C >>= 2 等于 C = C >> 2        |
  |   &=   |   按位与后赋值   |         C &= 2 等于 C = C & 2         |
  |   ^=   |  按位异或后赋值  |         C ^= 2 等于 C = C ^ 2         |
  |  \|=   |   按位或后赋值   |        C \|= 2 等于 C = C \| 2        |
  
- [x] 其他运算符：

  | 运算符 | 描述             |            实例            |
  | :----- | :--------------- | :------------------------: |
  | &      | 返回变量存储地址 | &a; 将给出变量的实际地址。 |
  | *      | 指针变量。       |     *a; 是一个指针变量     |
  
- [x] 运算符优先级：
  
  | 优先级 |      运算符      |
  | :----: | :--------------: |
  |   5    | * / % << >> & &^ |
  |   4    |     + - \| ^     |
  |   3    | == != < <= > >=  |
  |   2    |        &&        |
  |   1    |       \|\|       |
  
- [ ] 几个特殊运算符：

  - 位清除 &^：将指定位置上的值设置为 0。将运算符左边数据相异的位保留，相同位清零 ：

- [ ] 本节案例：

  

  </details>
<details>
<summary>Day017: 语句-Go条件语句</summary>

- [x] 本节说明：本节介绍Go语言条件语句相关内容。

- [x] 条件语句介绍：

  - 条件语句需要开发者通过指定一个或多个条件，并通过测试条件是否为 true 来决定是否执行指定语句，并在条件为 false 的情况在执行另外的语句。
  
- [x] if语句：

  - if 语句由一个布尔表达式后紧跟一个或多个语句组成。

    ```go
    if 布尔表达式 {
       /* 在布尔表达式为 true 时执行 */
    }
    ```

- [x] if...else 语句：

  - if 语句后可以使用可选的else语句, else语句中的表达式在布尔表达式为 false 时执行。

    ```go
    if 布尔表达式 {
       /* 在布尔表达式为 true 时执行 */
    } else {
      /* 在布尔表达式为 false 时执行 */
    }
    ```

- [x] if 嵌套语句：

  - 你可以在 if 或 else if 语句中嵌入一个或多个 if 或 else if 语句。

    ```go
    if 布尔表达式 1 {
       /* 在布尔表达式 1 为 true 时执行 */
       if 布尔表达式 2 {
          /* 在布尔表达式 2 为 true 时执行 */
       }
    }
    ```

- [ ] switch 语句：

  - switch语句用于基于不同条件执行不同动作，每一个 case 分支都是唯一的，从上至下逐一测试，直到匹配为止。

  - switch 语句执行的过程从上至下，直到找到匹配项，匹配项后面也不需要再加 break。

  - switch 默认情况下 case 最后自带 break 语句，匹配成功后就不会执行其他 case，如果我们需要执行后面的 case，可以使用 fallthrough 。

    ```go
    switch var1 {
        case val1:
            ...
        case val2:
            ...
        default:
            ...
    }
    ```

- [x] select 语句：

  - select 是 Go 中的一个控制结构，类似于 switch 语句。每个 case 必须是一个通信操作，要么是发送要么是接收。

  - select 随机执行一个可运行的 case。如果没有 case 可运行，它将阻塞，直到有 case 可运行。一个默认的子句应该总是可运行的。

  - select没有条件表达式，一直在等待分支进入可运行状态。

    ```go
    select {
        case communication clause  :
           statement(s);      
        case communication clause  :
           statement(s);
        /* 你可以定义任意数量的 case */
        default : /* 可选 */
           statement(s);
    }
    ```

  注意：Go 没有三目运算符，所以不支持 ?: 形式的条件判断。

- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day018: 语句-Go循环语句</summary>

- [x] 本节说明：本节介绍循环语句的相关内容。

- [x] Go循环语句：

  - 在不少实际问题中有许多具有规律性的重复操作，因此在程序中就需要重复执行某些语句。

- [x] for循环：重复执行语句块

  - for 循环是一个循环控制结构，可以执行指定次数的循环。

  - Go 语言的 For 循环有 3 种形式，只有其中的一种使用分号。

    ```go
    for  初始化语句; 条件语句; 修饰语句 {}
    for init; condition; post { }
    // init： 一般为赋值表达式，给控制变量赋初值；
    // condition： 关系表达式或逻辑表达式，循环控制条件；
    // post： 一般为赋值表达式，给控制变量增量或减量。
    // 在循环中同时使用多个计数器：
    for i, j := 0, N; i < j; i, j = i+1, j-1 {}
    ```

    ```go
    for condition { }
    ```

    ```go
    for { }
    // 无限循环
    ```

  - for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。格式如下：

  - 在循环中同时使用多个计数器：

    ```go
    for key, value := range oldMap {
        newMap[key] = value
    }
    ```

  - 计算 1 到 10 的数字之和：

    ```go
    package main
    
    import "fmt"
    
    func main() {
            sum := 0
            for i := 0; i <= 10; i++ {
                    sum += i
            }
            fmt.Println(sum)
    }
    ```

  - 无限循环:

    ```go
    package main
    
    import "fmt"
    
    func main() {
            sum := 0
            for {
                sum++ // 无限循环下去
            }
            fmt.Println(sum) // 无法输出
    }
    ```

  - For-each range 循环：这种格式的循环可以对字符串、数组、切片等进行迭代输出元素。

    ```go
    package main
    import "fmt"
    
    func main() {
            strings := []string{"google", "runoob"}
            for i, s := range strings {
                    fmt.Println(i, s)
            }
            numbers := [6]int{1, 2, 3, 5}
            for i,x:= range numbers {
                    fmt.Printf("第 %d 位 x 的值 = %d\n", i,x)
            }  
    }
    ```

- [x] 循环嵌套：在循环内使用循环。

  - 使用方法：

    ```go
    for [condition |  ( init; condition; increment ) | Range]
    {
       for [condition |  ( init; condition; increment ) | Range]
       {
          statement(s);
       }
       statement(s);
    }
    ```

  - 使用循环嵌套来输出 2 到 100 间的素数：

    ```go
    package main
    import "fmt"
    func main() {
       /* 定义局部变量 */
       var i, j int
       for i=2; i < 100; i++ {
          for j=2; j <= (i/j); j++ {
             if(i%j==0) {
                break; // 如果发现因子，则不是素数
             }
          }
          if(j > (i/j)) {
             fmt.Printf("%d  是素数\n", i);
          }
       }  
    }
    ```

- [ ] 循环控制语句：

  - break 语句：

    - 用于循环语句中跳出循环，并开始执行循环之后的语句。

    - break 在 switch（开关语句）中在执行一条 case 后跳出语句的作用。

    - 在多重循环中，可以用标号 label 标出想 break 的循环。

      ```go
      break;
      ```

  - continue语句：

    - Go 语言的 continue 语句 有点像 break 语句。但是 continue 不是跳出循环，而是跳过当前循环执行下一次循环语句。

    - for 循环中，执行 continue 语句会触发 for 增量语句的执行。

    - 在多重循环中，可以用标号 label 标出想 continue 的循环。

      ```go
      continue;
      ```

  - goto 语句：

    - Go 语言的 goto 语句可以无条件地转移到过程中指定的行。

    - goto 语句通常与条件语句配合使用。可用来实现条件转移， 构成循环，跳出循环体等功能。

    - 但是，在结构化程序设计中一般不主张使用 goto 语句， 以免造成程序流程的混乱，使理解和调试程序都产生困难。

      ```go
      goto label;
      ..
      .
      label: statement;
      ```

- [x] 无限循环：
  
  - 如果循环中条件语句永远不为 false 则会进行无限循环，我们可以通过 for 循环语句中只设置一个条件表达式来执行无限循环：
  
    ```go
    package main
    import "fmt"
    
    func main() {
        for true  {
            fmt.Printf("这是无限循环。\n");
        }
    }
    ```
  
- [ ] 本节案例： 
  
  
  
  </details> 

<details>
<summary>Day000: 错误-Go错误处理</summary>

- [ ] 本节说明：

- [ ] range：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [ ] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] [参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_16_function.md)

- [ ] 本节案例：

  

  </details>
<details>
<summary>Day000: 函数-Go语言方法</summary>

- [ ] 本节说明：本节介绍Go语法内容。

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 参考链接：[参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_20_method.md)
  
- [ ] 本节案例：
  
  
  
  </details>

<details>
<summary>Day000: 函数-Go内置函数</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] [参考1](https://github.com/ffhelicopter/Go42/blob/master/content/42_15_errors.md)
  
- [ ] 本节案例：
  
  
  
  </details>

### 第二章：Go语言进阶
<details>
<summary>Day000: 基础-Go语言协程</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  

  </details>
<details>
<summary>Day000: 基础-Go语言通道</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  

  </details>
<details>
<summary>Day000: 基础-Go同步与锁</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  

  </details>
### 第三章：Go项目参考
<details>
<summary>Day000: 基础-Go语言并发</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  

  </details>
### 第四章：Go标准库包
<details>
<summary>Day000: 基础-Go语言并发</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  

  </details>
### 第五章：Go语言框架
<details>
<summary>Day000: 基础-Go语言并发</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：

  

  </details>
### 第六章：Go语言框架
<details>
<summary>Day100: 项目-Go漏洞扫描</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day101: 项目-Go域名扫描</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day200: 源码-Go语言源码</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  
  
  </details>
<details>
<summary>Day365: Go语言入门</summary>

- [ ] 本节说明：

- [x] Go语言介绍：

  - Go 是一个开源的编程语言，它能让构造简单、可靠且高效的软件变得容易。 
  
- [x] Go语言命令：

  - go run hello.go //编译运行hello.go
  
- [ ] 本节案例：
  
  
  
  </details>

## 0x03-参考资源

- https://www.runoob.com/go/go-tutorial.html