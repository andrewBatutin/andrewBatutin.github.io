---
layout: post
title:  "Swift and KVC"
date:   2014-12-06 22:13:00
categories: swift
---
##1. Introduction
Lately my colleague and i has a conversation about Swift and Objective C. One of his points was Swift lacks some libraries and frameworks we've used to. One of them is KVC with it marvelous collections operators. He claimed that there is no way i can write as small and neat code to work with hairy JSON structure with Swift like he has done it with Objective C KVC mechanism. My response was instant. I've asked him to show me his JSON and what was he doing with it with KVC. And I've started to write same part of code but with Swift.  

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

 So if you supply ti the reduce function initial value **U** and closure **(U, T) -> U** reduce function will "reduce" your collection to the one value using this closure and initial value.  
 In other words if we supply reduce function with **@unionOfArrays** equivalent closure then we'll get what we need to extract all the articleId's from collections.  
 Way to achieve **@unionOfArrays** effect i come up with is next function

 {% highlight swift %}
 let allArticleId = parsedJsonStructure.reduce([]){$0 + $1.topLevelCollection}
				.reduce([]){$0 + $1.oneStepDownCollection}
				.reduce([]){$0 + $1.twoStepDownCollection}
                                .reduce([]){$0 + $1.threeStepDownCollection}
				.map({$0.articleID})
 //same effect as ObjC code
 {% endhighlight %}

##5. Bencmark  

##6. Conclusion  

