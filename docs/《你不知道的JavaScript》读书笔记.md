## 第1部分：作用域和闭包

### 作用域是什么？

#### 编译原理

这本讲解JavaScript的书首先讲的却是编译原理，一开始看起来让人费解，但实际上从后面内容我们可以发现，JavaScript的很多特性都与编译原理有着极大的关系。我们通常称JavaScript是动态解释执行语言，因为它不是提前编译的，而是根据执行时的情况来对代码进行处理。

在传统编译语言的流程中，代码的执行通常分成三个步骤：

1. 分词/词法分析（Tokenizing/Lexing）

将语句分解成词法单元（Token）,例如 `var a = 2;` 会被分解成: var、a、=、2、;。需要注意的是分词和词法分析有少许的区别，

>如果词法单元生成器在判断a是一个独立的词法单元还是其他词法单元的一部分时，调用的是有状态的解析规则，那么这个过程就被称为词法分析。

理解不了这一句中的 **有状态的解析规则**

2. 解析、语法分析（Parsing）

将词法单元流转换成树形结构的的过程。这个树被称为“抽象语法树”（Abstract Syntax Tree,AST）.

3. 代码生成

将AST转换成可执行代码的过程。简单来说就是把 `var a = 2;` 的AST转化为一组机器指令，用来创建一个叫做a的变量（包括分配内存），并将一个值储存在a中。

与传统编译语言的编译器相比，JavaScript引擎要更复杂，最明显的区别就体现在编译时间上，JavaScript引擎没有时间进行优化，编译过程不是在构建之前，通常发生在代码执行前的几微秒内。在作用域的背后，JavaScript引擎使用了各种方法（比如JIT延迟编译甚至实施重编译）来保证性能。
