## Dynamic Software Interview

"I love technical interviews" said no programmer ever.
Heated debates about what is the best way to filter programmers have seemingly endless nature. Should we hit a guy with 3-hour whiteboarding session? Should we interrogate a web-dev about his knowledge of red-black trees? Or should we just take a set of CVs and randomly choose a candidate? Those are questions without answers.


One thing entirely clear - we need a way to get best possible developers from the available resource pool.

One particular detail of tech interviews always struck me most - it's detached from real-life tasks. Closets you can get to real-life experience during the interview is a test task. But they have rather static nature. You are given fully observable task with clear guidelines and restrictions. And some set amount of time to implement it.

And the issue is that in real project most probably you want have any of that. Task description will be limited. Time frame will be highly volatile. Scope creep will be constant. Your Monday perfect piece of code turns to a little spaghetti monster till the end of the week. And in 2 weeks it will eat you alive.

Time is an essential part of software project evolution. Code-base entropy always tries to get out of control. And the ability to handle that dynamics is an essential part of every programmer skill set as far as i'm concerned.

In a perfect world you would like to stick a new guy for a couple of month in your project to see how good is he. But in reality that is often not possible. Hiring a good guy for a job is a problem. Firing bad guy - even bigger one.

My idea is to simulate real-world conditions during tech interview phase with Dynamic Software Interview methodology.

Idea is to compress average sprint of you project in about 4 hours worth of task. Split this task in 2 to 3 parts. And give them one by one to the candidate.

For instance:

1. Ask a candidate to create a generic project for Java-based RESTFull service.
2. Ask a candidate to implement REST API that return a 5 days weather forecast for a specific city.
3. Ask a candidate to change that API so it returns 1 day weather forecast for 10 cities.

Trick is to feed those tasks one by one. So the candidate is forced to change his codebase according to the new requirements. Almost like in real life. If a candidate is frustrated by such task - it means it is right one)

Downside of such approach is that it might take longer to implement then conventional all-in test task. So it's important to keep them short.

Some other examples of dynamic interview tasks

#### Shopping list
1. create a shopping list with item name, price and quantity
2. take the shopping list and break it into 3 categories - meat, fruits vegetables

#### Image gallery
1. Create horizontal image gallery
2. Turn it to the vertical one

#### Black Jack
1. Design a Black Jack game with set of rules A
2. Change it to the set of rules B

#### Image Editor
1. Implement editor that can turn images BW
2. Implement feature at editor that make it sepia

#### Login Page
1. Implement login page with uname as an email + verification
2. Add to it zip and phone numbers + verification
3. Or use fucked-up verification rules for email - so candidate can’t rely on standard solutions any more

We need to check if person can use OOP effectively during normal dev process. In order to do that we’ll simulate change of requirements that has to be mitigated by application of OOP and design patterns.
If a candidate use Strategy pattern to implement Black Jack Set A and Set B rules - he receives a highest mark for instance.

Emphasize necessity to use git properly. Instruct person to write proper commit messages and use tags to mark completion of the subtask.
Mention that his project structure also will be examined. So candidate should pay attention to it. - Call it task 0

Prepare a test backend to be used by candidate - one way to do that is to mock responses.
For backend candidates - use mock client (postman for instance)

#### Segmentation by candidate’s level
If tasks will be generic enough to accommodate candidates with different levels of professional experience - that will save a lot of effort
Also it will give ability to compare candidates of different level. And justify why person is not qualified for this position.

#### Common set of metrics for the tasks
Will allow to compare different candidates by same scale. Even form different tech fields.
Metrics such as ???????????????????????

#### Boilerplate code
Per - task should be decided whether or not candidate should receive boilerplate code to begin with.
On one hand side some tasks might require too much time for auxiliary code to be put in place.
On the other hand if candidate will receive pre-populated project - it will give him a lot of hints how to finish the task.
