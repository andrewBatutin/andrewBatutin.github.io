---
layout: post
title:  "Swift and KVC"
date:   2014-12-06 22:13:00
categories: swift
---
##1. Introduction
Lately my colleague _M.D._ and I has a conversation about Swift and Objective C. One of his points was Swift lacks some libraries and frameworks we've used to. One of them is KVC with it marvelous collections operators. He claimed that there is no way I can write as small and neat code to work with hairy JSON structure with Swift like he has done it with Objective C KVC mechanism. My response was instant. I've asked him to show me his JSON and what was he doing with it with KVC. And I've started to write same part of code but with Swift.  

##2. JSON structure
I won't show whole JSON structure case it's to big and clumsy. Part that we are interested in looks smthng like that
 {% highlight json %}
{  
    "jsonStructure":[  
        {  
            "topLevelCollection":[  
                {  
                    "oneStepDownCollection":[  
                        {  
                            "twoStepDownCollection":[  
                                {  
                                    "threeStepDownCollection":[  
                                        {  
                                            "articleID":1
                                        },
                                        {  
                                            "articleID":2
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
 {% endhighlight %}
So we've got that deep layered JSON arrays and our task is to get all the **articleId** values from all the elements at all the levels of the JSON structure. We don't care about an order or uniqueness of the id's. We just need to get all of them.

##3. ObjC way 
The Objective C solution we are comparing to looks like that:
{% highlight objc %}
// Collect all article ID
NSArray *allArticleId = [parsedJsonStructure valueForKeyPath:@"topLevelCollection.@unionOfArrays.oneStepDownCollection.@unionOfArrays.twoStepDownCollection.@unionOfArrays.threeStepDownCollection.articleID"];
// as a result we've got all the articles id in the parsedJsonStructure
{% endhighlight %}
As you can see we indeed has a one line of code to do the job. 
Let's see what I've came up with using Swift
 
##4. Swift way  
As far as a know Swift has a inferred type system and somewhat lacks of ObjC dynamic nature to implement KVC - like behavior. But instead Swift has some very interesting [**Functional Programming**](http://www.raywenderlich.com/82599/swift-functional-programming-tutorial) tools to work with collections. And one of them if **reduce** function. If you take a look at function declaration you'll see
 
 {% highlight swift %}
 func reduce<U>(initial: U, combine: (U, T) -> U) -> U
 {% endhighlight %}

 So if you supply to the reduce function initial value **U** and closure **(U, T) -> U** reduce function will "reduce" your collection to the one value using this closure and initial value.  
 

 And if we'll take empty array **[]** as initial value and closure to create a union of arrays and put all that to reduce function - then we'll get **@unionOfArrays** equivalent at Swift.  
 

 Union of array closure for the **topLevelCollection** I've created looks like that
 {% highlight swift %}
 parsedJsonStructure.reduce([]){$0 + $1.topLevelCollection}
 {% endhighlight %}
 **$0** - stands for the initial value  
 **$1** - stands for the element in array of **topLevelCollection**.  
 On the first iteration reduce will concatenate initial empty array **[]** with 1st element of the topLevelCollection array.  
 On the second iteration reduce will concatenate result of previous iteration with 2nd element of the topLevelCollection array.  
 And so on till the last element of the topLevelCollection.  


 Now if we'll apply reduce function to all the levels of the JSON structure till the very bottom - we can get all the article's id from it.  
 My solution looks like that  

 {% highlight swift %}
 let allArticleId = parsedJsonStructure.reduce([]){$0 + $1.topLevelCollection}
				.reduce([]){$0 + $1.oneStepDownCollection}
				.reduce([]){$0 + $1.twoStepDownCollection}
                                .reduce([]){$0 + $1.threeStepDownCollection}
				.map({$0.articleID})
 //same effect as ObjC code
 {% endhighlight %}

 **.map({$0.articleID})** used to unwrap string value of the article ID to the resulting array. Without that we'll get collection of the threeStepDownCollection elements but not the actual string values of the articleId. And I feel that there should be even more elegant solution for that. I'll be glad if you find one.

##5. Bencmark  
According to fantastic article [Let's Build Key-Value Coding by Mike Ash](https://www.mikeash.com/pyblog/friday-qa-2013-02-08-lets-build-key-value-coding.html) there are quite a lot of stuff going on behind the slim KVC facade. And I've had a hope that Swift reduce will run actually faster than ObjC version. So my colleague _M.D._ and I have decided to run a little benchmark to compare Swift vs ObjC solutions. And here what we've got.

First of all we've used **Apple iPad mini 16GB Wi-Fi + Cellular** to run our tests.  


For Swift Compiler I've used **-Ounchecked** optimisation level. For LLVM Code generation optimization **-Ofast** level. Which I suppose the fastest optimization settings possible.  
ObjC version also was compiled against release settings. So it also should be fastest one.  


We've created 10000 items at jsonStructure. So each level had 10 elements at sub-level. **topLevelCollection** had 10 **oneStepDownCollection** elements. **oneStepDownCollection** had 10 **twoStepDownCollection**. And so on till the bottom.  


And we've got same result for Swift and ObjC version
It took us **0.04** seconds to get all the 10000 articleID's values from the structure. 

On one hand I was a bit disappointed that Swift was not faster of the ObjC. But then I thought that Swift should not be faster then ObjC. Actually it should be same as ObjC. And I felt satisfied. 

##6. Conclusion  

To sum up Swift allows you to do all the same things KVC Collection Operations can. But in rather different way you've could expected. Yes you should learn some new tricks to work with data at Swift style. And they might look to complex to you comparing to ObjC KVC mechanism. One argument for increased code complexity is type safety. In case you've decided to change name of the property at JSON structure Swift compiler will kindly remind you to update the property name at reduce function too. In comparison at ObjC collections operators are represented as a strings. And there is no way you can ensure that object has a property you referring to before you actually run the code and catch runtime exception.  
So Swift lets you catch more errors at compile time. And waste less time at debugging.  
On the other hand ObjC is so good for debugging purposes you can actually want to stick to the good old runtime introspection tricks. 

And as you can see Apple has given us two ways of doing same thing with the same performance. And it's up to you what method to be used to conquer the world) I just would not recommend you to try write Swift code at ObjC style and vice versa. So don't try to implement KVC at Swift. It might not fit to the language paradigm as well as it fitted to ObjC paradigm.

##7. Resources
* [Xcode project](https://github.com/andrewBatutin/SwiftDataManip)
* [Functional programming explained with Haskell](http://learnyouahaskell.com/chapters)

##Thanks For Reading!


