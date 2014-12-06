---
layout: post
title:  "Swift and KVC"
date:   2014-12-06 22:13:00
categories: swift
---
##1. Introduction

##2. ObjC way 
 
##3. Swift way  
 {% highlight swift %}
 let test1 = collecionOdTestData.reduce([]){$0 + $1.sections}
				.reduce([]){$0 + $1.items}
				.reduce([]){$0 + $1.dots}
				.map({$0.articleID})
 {% endhighlight %}

##4. Bencmark  

##5. Conclusion  

