---
title:  "Ruby与C++交互指南"
date:   2017-07-12 9:00:00
categories: 
- 技术
- C++
tags: [Ruby]
---

Ruby与C++交互主要有以下两种方式: 

* SWIG方式
* Rice方式

GOOGLE了一下，关于它们使用的看的有点乱，无法完整做出一个demo,最后都是通过运行它们的示例再学习使用的。

<!-- More -->

# SWIG方式
SWIG方式是广泛使用的方式，它支持包括Ruby在内的十几种语言调用C++库 
## 安装
执行命令 `brew install swig`

## 使用

* 生成待调用函数

my_math.h

```cpp
#ifndef __MY_MATH_H__
#define __MY_MATH_H__

extern "C"
{
  extern int add(int a, int b);
}

#endif
```

my_math.cpp

```cpp
#include "my_math.h"

int add(int a, int b)
{
  return a + b + 1;
}
```

* 生成extconf.rb文件

```ruby
require 'mkmf'
#是example.cpp的文件名，可任意定义(最好与要公开的RUBY类一致)
create_makefile('example')
```

* 生成example.i文件

```cpp
%module example

%inline %{
 extern int add(int a, int b);
%}

```

* 生成测试程序run_me.rb

```ruby
require_relative 'Example'

a, b = 1, 1
puts "NOTICE: Result will auto increase 1"
puts "#{a} + #{b} = #{Example.add(a, b)}"
```

* 运行
```
swig -ruby example.i
ruby extconf.rb
make
ruby run_me.rb
```

# Rice方式
## 安装
执行命令 `gem install rice`

## 使用

可以先从[源码](https://github.com/jasonroelofs/rice)中的示例入手，以下只写记录与Rice不同的地方。

* 修改extconf.rb文件

```ruby
#不能使用'mkmf', 不然下面include ‘rice/Class.hpp’时会找不到rice
require 'mkmf-rice'
```

* 修改example.i为example.cpp文件

```cpp
#include "rice/Class.hpp"
#include "my_math.h"

using namespace Rice;

//函数名格式：必须是"Init_当前文件名"
extern "C" void Init_example()
{
  //Example为最终RUBY看到的类名
  Class tmp_ = define_class("Example")
    .define_method("add", &add);
}
```

* 修改测试程序run_me.rb文件

```ruby
puts "#{a} + #{b} = #{Example.new.add(a, b)}"
```

* 运行

不执行此命令 <del>`swig -ruby example.i`</del>

# 参考
* [示例下载](/samples/RubyCppTest.tar.gz)
* [在 C++ 中使用 Rice 构建 Ruby 扩展](http://www.ibm.com/developerworks/cn/opensource/os-extendruby/index.html#list1)
