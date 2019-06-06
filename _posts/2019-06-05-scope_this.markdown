---
layout: post
title:      "Scope This"
date:       2019-06-06 01:39:01 +0000
permalink:  scope_this
---


One of the most difficult aspects of methods and variables in Ruby is scope.  Since most of the errors when beginning to learn Ruby will be scope related, it is an essential concept to understand.  I like to think of scope as accessibility.  Which variables and methods are accessible at a specific spot in the code?  As I continue to progress, I find that having a solid understanding of my current scope is essential to good and efficient coding.  This ultimately begs the question of why programmers put any restrictions on scope.  There is a global scope so why wouldn't we just make everything available in all parts of our code?  The most obvious issue with global scope is variable naming.  When working on large scale applications, it is highly likely that different programers will use the same variable names with different assignments.  Doing so, would break one side of the code.  There is also the issue of app security.  Beyond increasing the likelihood of breaking the application, it is not prudent to provide all programmers access to all methods and all variables.
