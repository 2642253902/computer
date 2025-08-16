#### 目标

- 学习基础 Java 语法和语义
- 从编写 Python 过渡到编写 Java

#### 6.005 中的软件

| 无 bug      | 易于理解                   | 随时可变         |
| ---------- | ---------------------- | ------------ |
| 今日纠正，未来亦然。 | 与未来的程序员（包括未来的你）进行清晰沟通。 | 旨在适应变化，无需重写。 |

## 开始学习 Java 教程。

接下来的几节将链接到 **[Java 教程](https://docs.oracle.com/javase/tutorial/index.html)** 帮助你掌握基础知识。

你也可以查看 [入门：学习 Java](https://ocw.mit.edu/ans7870/6/6.005/s16/getting-started/java.html) 作为另一种资源。

本阅读和其他资源将频繁地引导你参考 [Java API 文档](https://docs.oracle.com/javase/8/docs/api/) 它描述了 Java 内置的所有类。

### 语言基础

阅读 **[语言基础](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)** .

你应该能够回答所有四个语言基础主题的 _问题和练习_ 页面上的问题。

- [问题：变量](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/QandE/questions_variables.html)
- [问题：运算符](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/QandE/questions_operators.html)
- [问题：表达式、语句、块](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/QandE/questions_expressions.html)
- [问题：控制流](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/QandE/questions_flow.html)

请注意，每 _问题和练习_ 页面底部都有一个链接指向解决方案。

另外，通过回答一些关于 Java 基础与 Python 基础比较的问题来检查你的理解。

### 数字和字符串

读取 **[数字和字符串](https://docs.oracle.com/javase/tutorial/java/data/index.html)** .

如果你觉得 `Number` 包装类令人困惑，不要担心。 确实如此。

你应该能够回答两页 _问题和练习_ 上的问题。

- [问题：数字](https://docs.oracle.com/javase/tutorial/java/data/QandE/numbers-questions.html)
- [问题：字符、字符串](https://docs.oracle.com/javase/tutorial/java/data/QandE/characters-questions.html)

### 类和对象

读取 **[类和对象](https://docs.oracle.com/javase/tutorial/java/javaOO/index.html)** .

你应该能够回答前两页上的问题 _问题和练习_ 页的问题。

- [问题：类](https://docs.oracle.com/javase/tutorial/java/javaOO/QandE/creating-questions.html)
- [问题：对象](https://docs.oracle.com/javase/tutorial/java/javaOO/QandE/objects-questions.html)

如果你不理解 _嵌套类_ 中的所有内容，请不用担心 _枚举类型_ 目前。 你可以在学期中后期，在课堂上看到这些结构时，再回过头去学习它们。

### 你好，世界！

阅读 **[Hello World!](https://docs.oracle.com/javase/tutorial/getStarted/application/index.html)**

你应该能够创建一个新的 `HelloWorldApp.java` 文件，输入教程页面上的代码，然后编译并运行程序以查看 `Hello World!` 在控制台上。

---

## 快照图

为了理解微妙的问题，绘制运行时发生的情况的图示将对我们有所帮助。 **快照图** 表示程序在运行时的内部状态——其栈（正在执行的方法及其局部变量）和堆（当前存在的对象）。

我们在6.005中使用快照图的原因：

- 通过图片（在课堂上和团队会议中）进行交流
- 说明原始类型与对象类型、不可变值与不可变引用、指针别名、栈与堆、抽象与具体表示等概念。
- 为了帮助解释你的团队项目设计（与团队成员和助教一起）。
- 为后续课程中更丰富的设计符号铺平道路。例如，快照图在6.170中泛化为对象模型。

尽管本课程中的图例使用了 Java 的示例，但该符号可以应用于任何现代编程语言，例如 Python、Javascript、C++、Ruby。

### 基本类型值

![primitive values in snapshot diagram](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/primitives.png)

原始值由裸常量表示。传入的箭头是指向变量或对象字段的值的引用。

### 对象值

![object values in snapshot diagram](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/objects.png)

对象值是一个标有类型的圆圈。 当我们想要展示更多细节时，我们在里面写字段名，并用箭头指向它们的值。 为了更详细的展示，字段可以包含它们的声明类型。有些人更喜欢写 `x:int` 而不是 `int x` ，但两者都可以。

### 可变值与变量重新赋值

快照图给我们提供了一种可视化变量变化与值变化之间区别的方法：

- 当你给变量或字段赋值时，你是在改变变量箭头指向的位置。你可以将其指向不同的值。
    
- 当你将值赋给可变量的内容时——例如数组或列表——你正在改变该值内部的引用。
    

#### 重新赋值与不可变值

![reassigning a variable](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/reassignment.png)

例如，如果我们有 [`String`](https://docs.oracle.com/javase/8/docs/api/?java/lang/String.html) 变量 `s` ，我们可以重新赋值为 `"a"` to `"ab"` .

```java
String s = "a";
s = s + "b";
```

`String` 是一个不可变 _类型_ 的例子，一旦创建，其值就永远不会改变。 不可变性（防止变化）是本课程的一个主要设计原则，我们将在未来的阅读中更多地讨论它。

不可变对象（其设计者意图始终表示相同值的对象）在快照图中用双边框表示，就像我们图中所示的 `String` 对象。

#### 可变值

![mutating an object](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/mutation.png)

相比之下， [`StringBuilder`](https://docs.oracle.com/javase/8/docs/api/?java/lang/StringBuilder.html) （另一个内置的 Java 类）是一个 _可变的_ 一个表示字符序列的对象，并且它有方法可以改变对象的值：

```java
StringBuilder sb = new StringBuilder("a");
sb.append("b");
```

这两个快照图看起来非常不同，这是好的：可变性和不可变性之间的区别在我们的代码中会扮演重要角色 _安全地避免错误_ .

#### 不可变引用

Java 还提供了不可变引用：一旦赋值后永不重新赋值的变量。 要使引用不可变，请使用关键字声明 `final` :

```java
final int n = 5;
```

![final reference is a double arrow](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/final-reference.png)

如果 Java 编译器不确信您的 `final` 变量在运行时只会被赋值一次，那么它将产生编译错误。 所以 `final` 为不可变引用提供静态检查。

在快照图中，一个不可变引用 `final` )用双向箭头表示。这是一个对象，其 `id` 永远不会改变（它不能被重新赋值为不同的数字），但 `age` 可以改变。

注意，我们可以有一个 _不可变引用_ 到 a _可变值_ （例如： `final StringBuilder sb` ) 即使我们指向的是同一个对象，其值也可以改变。

我们也可以有一个 _可变引用_ 指向一个 _不可变值_ (例如 `String s` ), 其中变量的值可以改变，因为它可以被重新指向不同的对象。

---

## Java 集合

《阅读 2：基础 Java》的第一节语言基础教程讨论了 [**数组**](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html) ，它们是 _固定长度_ 用于存储对象或原始值序列的容器。 Java 提供了多种更强大和灵活的工具来管理 _集合_ 对象： **Java 集合框架** .

### 列表、集合和映射

**一个 [Java `List`](https://docs.oracle.com/javase/8/docs/api/?java/util/List.html) 类似于一个 [Python 列表](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range) 。** A `List` 包含一个有序的零个或多个对象的集合，其中同一个对象可能会出现多次。 我们可以向和从 `List` 添加和移除项目。 ，它会根据内容的大小进行扩展和收缩。

示例 `List` 操作：

|Java|描述|Python|
|---|---|---|
|`int count = lst.size();`|统计元素数量|`count = len(lst)`|
|`lst.add(e);`|在末尾追加一个元素|`lst.append(e)`|
|`if (lst.isEmpty()) ...`|测试列表是否为空|`if not lst: ...`|

在快照图中，我们表示 `List` 作为具有索引字段的对象：

这个 `cities` 可能代表从波士顿到波哥大再到巴塞罗那的旅行。

**A [`Set`](https://docs.oracle.com/javase/8/docs/api/?java/util/Set.html) 是一个包含零个或多个唯一对象的无序集合。** 类似于数学 _set_ 或者 [Python set](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset) – 与之不同 `List` – 对象不能在集合中出现多次。 要么存在，要么不存在。

示例 `Set` 操作：

|Java|描述|Python|
|---|---|---|
|`s1.contains(e)`|测试集合是否包含元素|`e in s1`|
|`s1.containsAll(s2)`|测试是否 _s1 ⊇ s2_|`s1.issuperset(s2)`  <br>`s1 >= s2`|
|`s1.removeAll(s2)`|删除 _s2_ 从 _s1_|`s1.difference_update(s2)`  <br>`s1 -= s2`|

在一个快照图中，我们将 `Set` 表示为一个无名称字段的对象：

这里有一组整数，没有特定的顺序：42、1024 和 -7。

**一个 [`Map`](https://docs.oracle.com/javase/8/docs/api/?java/util/Map.html) 类似于 [Python 字典](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) 。** 在 Python 中，map 的 **键** 必须是 [可哈希的](https://docs.python.org/3/glossary.html#term-hashable) . Java 也有类似的要求，我们将在讨论 Java 对象之间如何工作等价性时进行讨论。

示例 `Map` 操作：

|Java|描述|Python|
|---|---|---|
|`map.put(key, val)`|添加映射 _key → val_|`map[key] = val`|
|`map.get(key)`|获取键的值|`map[key]`|
|`map.containsKey(key)`|测试映射是否包含键|`key in map`|
|`map.remove(key)`|删除一个映射|`del map[key]`|

在一个快照图中，我们将 `Map` 表示为一个包含键值对的对象：

这 `海龟` 地图包含 `海龟` 分配给对象 `String` 键：Bob、Buckminster 和 Buster。

### 字面量

Python 提供了方便的语法来创建列表：

```python
lst = [ "a", "b", "c" ]
```

以及映射：

```python
map = { "apple": 5, "banana": 7 }
```

**Java 不提供。** 它确实提供了数组的字面量语法：

```java
String[] arr = { "a", "b", "c" };
```

但这样就创建了一个 _数组_ ，不是 `List` . 我们可以使用一个 [提供的实用函数](https://docs.oracle.com/javase/8/docs/api/?java/util/Arrays.html) 用于创建 `List` 从数组中：

```java
Arrays.asList(new String[] { "a", "b", "c" })
```

A `List` 创建于 `Arrays.asList` 它确实有一个限制：长度是固定的。

### 泛型：声明 List、Set 和 Map 变量

与 Python 集合类型不同，使用 Java 集合我们可以限制集合中包含的对象类型。 当我们添加一个项目时，编译器可以执行 _静态检查_ 确保我们只添加适当类型的项。 然后，当我们取出一个项时，我们保证它的类型将是我们预期的。

以下是声明一些用于存储集合的变量的语法：

```java
List<String> cities;        // a List of Strings
Set<Integer> numbers;       // a Set of Integers
Map<String,Turtle> turtles; // a Map with String keys and Turtle values
```

由于泛型的工作方式，我们不能创建一个包含原始类型的集合。 例如， `Set<int>` does _not_ work. 然而，正如我们之前所见， `int` s 具有 `Integer` 包装器我们可以使用（例如： `Set<Integer> numbers` ).

为了更方便地使用这些包装器类型的集合，Java 进行了一些自动转换。 如果我们声明了 `List<Integer> sequence` ，这段代码可以正常工作：

```java
sequence.add(5);              // add 5 to the sequence
int second = sequence.get(1); // get the second element
```

### ArrayLists 和 LinkedLists：创建 List

很快我们就会看到，Java 帮助我们区分类型的 _规范_ ——它做什么？——和 _实现_ – 代码是什么？

`List` , `Set` ，和 `Map` 都是 _接口_ 它们定义了这些不同类型的工作方式，但它们不提供实现代码。 有几个优点，但一个潜在的优点是，作为这些类型的用户，我们可以在不同的情况下选择不同的实现方式。

以下是创建一些实际 `List` s:

```java
List<String> firstNames = new ArrayList<String>();
List<String> lastNames = new LinkedList<String>();
```

如果泛型类型参数在左右两侧相同，Java 可以推断出正在发生的事情并节省我们一些输入：

```java
List<String> firstNames = new ArrayList<>();
List<String> lastNames = new LinkedList<>();
```

[`ArrayList`](https://docs.oracle.com/javase/8/docs/api/?java/util/ArrayList.html) and [`LinkedList`](https://docs.oracle.com/javase/8/docs/api/?java/util/LinkedList.html) 是两种实现 `List` . 两者都提供所有操作 `List` ，并且这些操作必须按照 `List` 的文档中描述的方式工作 `List` . 在这个例子中， `firstNames` 和 `lastNames` 将以相同的方式表现；如果我们交换了使用哪一个 `ArrayList` 与。 `LinkedList` ，我们的代码就不会出问题。

不幸的是，这种选择能力也是一种负担：我们不在乎 Python 列表是如何工作的，我们为什么要关心我们的 Java 列表是 `ArrayLists` 还是 `LinkedLists` ? 由于唯一的不同在于性能，对于 6.005 _我们不_ .

当不确定时，使用 `ArrayList` .

### HashSet 和 HashMap：创建集合和映射

[`HashSet`](https://docs.oracle.com/javase/8/docs/api/?java/util/HashSet.html) 是我们默认选择的 `Set` 类型：

```java
Set<Integer> numbers = new HashSet<>();
```

Java 还提供了 [排序集合](https://docs.oracle.com/javase/8/docs/api/?java/util/SortedSet.html) 以及 [`TreeSet`](https://docs.oracle.com/javase/8/docs/api/?java/util/TreeSet.html) 实现。

以及对于 `Map` 默认选择是 [`HashMap`](https://docs.oracle.com/javase/8/docs/api/?java/util/HashMap.html) :

```java
Map<String,Turtle> turtles = new HashMap<>();
```

### 迭代

所以可能我们有：

```java
List<String> cities        = new ArrayList<>();
Set<Integer> numbers       = new HashSet<>();
Map<String,Turtle> turtles = new HashMap<>();
```

一个非常常见的任务是遍历我们的城市/数字/乌龟等。

在 Python 中：

```python
for city in cities:
    print city

for num in numbers:
    print num

for key in turtles:
    print "%s: %s" % (key, turtles[key])
```

Java 提供了类似的语法来遍历 `List` s 和 `Set` s.

这是 Java 代码：

```java
for (String city : cities) {
    System.out.println(city);
}

for (int num : numbers) {
    System.out.println(num);
}
```

我们不能以这种方式迭代 `Map` s 自身，但我们可以像在 Python 中那样迭代键：

```java
for (String key : turtles.keySet()) {
    System.out.println(key + ": " + turtles.get(key));
}
```

在底层，这种 `for` 循环使用一个 [`Iterator`](https://docs.oracle.com/javase/8/docs/api/?java/util/Iterator.html) ，我们将在课程后面看到的一种设计模式。

#### 使用索引进行迭代

如果你愿意，Java 提供了不同的 `for` 循环，我们可以使用它们来通过索引遍历列表：

```java
for (int ii = 0; ii < cities.size(); ii++) {
    System.out.println(cities.get(ii));
}
```

除非我们确实需要索引值 `ii` ，这段代码冗长，并且有更多隐藏 bug 的地方。 避免。

## Java API 文档

上一节包含一些指向属于 [Java 平台 API](https://docs.oracle.com/javase/8/docs/api/) .

API 的类文档的链接。API 代表 _应用程序编程接口_ . 如果你想要编写一个与 Facebook 交互的应用程序，Facebook 会发布 API（实际上有多个，用于不同的语言和框架），你可以针对这些 API 进行编程。 Java API 是一个包含大量通用工具的集合，可用于编写几乎所有类型的应用程序。

- [**`java.lang.String`**](https://docs.oracle.com/javase/8/docs/api/?java/lang/String.html) 是全名 `String` . 我们可以通过使用 `String` 来创建类型为 `"double quotes"` .
    
- [**`java.lang.Integer`**](https://docs.oracle.com/javase/8/docs/api/?java/lang/Integer.html) 以及其他的原始包装类。 Java 在大多数情况下会自动在原始类型和包装（或“装箱”）类型之间进行转换。
    
- [**`java.util.List`**](https://docs.oracle.com/javase/8/docs/api/?java/util/List.html) 它类似于 Python 列表，但在 Python 中，列表是语言的一部分。 在 Java 中， `List` s 是在… Java 中实现的！
    
- [**`java.util.Map`**](https://docs.oracle.com/javase/8/docs/api/?java/util/Map.html) 它类似于 Python 字典。
    
- [**`java.io.File`**](https://docs.oracle.com/javase/8/docs/api/?java/io/File.html) 表示磁盘上的一个文件。 看看 `File` 提供的方法：我们可以测试文件是否可读，删除文件，查看最后一次修改时间……
    
- [**`java.io.FileReader`**](https://docs.oracle.com/javase/8/docs/api/?java/io/FileReader.html) 可以让我们读取文本文件。
    
- [**`java.io.BufferedReader`**](https://docs.oracle.com/javase/8/docs/api/?java/io/BufferedReader.html) 可以让我们高效地读取文本，并且它还提供了一个非常有用的功能：一次读取整行。
    

让我们更仔细地查看 [`BufferedReader`](https://docs.oracle.com/javase/8/docs/api/?java/io/BufferedReader.html) . 这里有很多与我们尚未讨论的 Java 特性相关的内容！ 保持冷静，专注于下面加粗的 **粗体字** 的内容。

![](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/bufferedreader-1.png)

页面的顶部是 _类层次结构_ for `BufferedReader` 和一个列表 _已实现的接口_ . A `BufferedReader` 该对象可以使用所有这些类型（以及它自己的方法）中的所有方法。

接下来我们看到 _直接子类_ ，对于接口， _实现类_ . 这可以帮助我们发现，例如 [`HashMap`](https://docs.oracle.com/javase/8/docs/api/?java/util/HashMap.html) 是 的一个实现 [`Map`](https://docs.oracle.com/javase/8/docs/api/?java/util/Map.html) .

接下来： **类的描述** . 有时候这些描述有点晦涩难懂，但是 **这是你应该首先去的地方** 以理解一个类。

![](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/bufferedreader-2.png)

如果你想要创建一个新的 `BufferedReader` the **构造函数摘要** 是首先需要查看的地方。 在 Java 中，构造函数不是获取新对象的唯一方法，但它们是最常用的。

![](https://ocw.mit.edu/ans7870/6/6.005/s16/classes/02-basic-java/figures/bufferedreader-3.png)

接下来： **方法摘要列出了我们可以调用的所有方法** 在 `BufferedReader` 对象上。

摘要下方是每个方法和构造函数的详细描述。 **点击构造函数或方法以查看详细描述。** 这是了解方法作用的第一站。

每个详细描述包括：

- The **方法签名** : 我们可以看到返回类型、方法名和参数。 我们还看到 _异常_ . 目前，它们通常表示方法可能遇到的问题。
- 完整的 **描述** .
- **参数** : 方法参数的描述。
- 以及方法的 **返回值** .

### 规格

这些详细描述是 **规格** . 它们使我们能够使用像 `String` , `Map` , 或 `BufferedReader` _无需_ 无需阅读或理解实现它们的代码。

阅读、编写、理解和分析规格将是我们在 6.005 课程的早期阶段要进行的第一个主要任务。