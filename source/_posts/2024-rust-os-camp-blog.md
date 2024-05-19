---
title: 2024 Rust OS 学习报告 
date: 2024-05-10 16:40:28
categories:
    - Spring Camp 2024
    - rcore-lab
tags:
    - author:liuyanjun
    - repo:(https://github.com/LearningOS/2024s-rcore-liuyanjun)
---
#自我介绍
先自我介绍一下，我是刘艳军，在金融公司在职。基于个人兴趣参加这次Rust OS培训。我好久没看操作系统方面的东西了，之前做过一些msp430等单片机开发，linux driver移植等工作。

# 一阶段 Rust学习经验
有幸参加过2024年球季的操作系统训练营，我的 rust 断断续续的学习的，没有系统的学习。

我 到了2024.4.15才完成了rustling， rustling试题做后 10 道题还是挺难的，我花了很多时间查询资料。
# Rust 基础总结
1. Performance
2. Memory Safety
3. Type System 
4. Polymorphism
5. Extensibility
6. Build & Package management

1. Performance
Minimum Runtime
Zero cost abstraction
No Garbage Collector
2. Memory Safety with ownership and Borrowing
Ownership Rules
	a. Each value in Rust has a variable that's called its owner
	b. There can only be one owner at a time
	c. When the owner goes out of scope, the value will be dropped
	RC -> Reference Counter
Borrowing Rules
	a. At any given time, you can have either one mutable reference or any number of immutable references
	b. References must always be valid
Avoid Data race


3. Type System
Immutability & Privacy By Default

No Null Values Options

Enum Option<T> {
	None,
	Some(T),
}

Mod Environment {

	Struct Person {
		
	} 
}

Explicit Error Handling

Recoverable error, unrecoverable error
Panic!()

Enum Result<T, E>{
	Ok(T),
	Err€,
}

Function

Pattern Matching

Closures

let adder :|i32, i32| -> i32;



Type - enum, struct

4. Polymorphism with Generics & Traits

Polymorphism - The ability to substitute multiple objects for each other if they share certain characteristics
No classical Inheritance


Trait
Trait object
Box<dyn Item>

5. Extensibility With Macros
Meta programming

6. Building & Package Management

Cargo - Build Tool, Package Manager

Cargo new
Cargo run
Cargo test
Cargo publish

Crates.io

#二阶段rCore OS Learning总结
2024.4.30 - 2024.5.8


# Risc-V 寄存器
寄存器	别名	全称	说明
X0	zero	零寄存器	可做源寄存器(rs)或目标寄存器(rd)
X1	ra	链接寄存器	保存函数返回地址
X2	sp	栈指针寄存器	指向栈的地址
X3	gp	全局寄存器	用于链接器松弛优化
X4	tp	线程寄存器	常用于在OS中保存指向进程控制块(task_struct)数据结构的指针
X5 ~ X7
X28 ~ X31	t0 ~ t6	临时寄存器	
X8	s0/fp	帧指针寄存器	用于函数调用，被调用函数需保存数据
X9	s1		用于函数调用 ，被调用函数需要保存的数据
X10 ~ X17	a0 ~ a7		用于函数调用，传递参数和返回值
X18 ~ X27	s2 ~ s11		用于函数调用 ，被调用函数需要保存的数据


