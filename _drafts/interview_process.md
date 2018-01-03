## Dynamic Software Interview

"I love technical interviews" said no programmer ever.
Heated debates about what is the best way to filter programmers have seemingly endless nature. Should we hit a guy with 3-hour whiteboarding session? Should we interrogate a web-dev about his knowledge of red-black trees? Or should we just take a set of CVs and randomly choose a candidate? Those are questions without answers.


One thing entirely clear - we need a way to get best possible developers from the available resource pool.

One particular detail of tech interviews always struck me most - it's detached from real-life tasks. Closets you can get to real-life experience during the interview is a test task. But they have rather static nature. You are given fully observable task with clear guidelines and restrictions. And some set amount of time to implement it.

And the issue is that in the real project most probably you won't have any of that. Task description will be limited. The time frame will be highly volatile. Scope creep will be constant. Your Monday perfect piece of code turns into a little spaghetti monster till the end of the week. And in 2 weeks it will eat you alive.

Time is an essential part of software project evolution. Code-base entropy always tries to get out of control. And the ability to handle those dynamics is an essential part of every programmer skill set as far as I'm concerned.

In a perfect world, you would like to stick a new guy for a couple of month in your project to see how good is he. But in reality that is often not possible. Hiring a good guy for a job is a problem. Firing bad guy - even bigger one.

My idea is to simulate real-world conditions during tech interview phase with Dynamic Software Interview methodology.

The idea is to compress average sprint of your project in about 4 hours worth of task. Split this task into 2 to 3 parts. And give them one by one to the candidate.

#### For instance:

1. Ask a candidate to create a generic project for Java-based RESTFull service.
2. Ask a candidate to implement REST API that returns a five days weather forecast for a specific city.
3. Ask a candidate to change that API, so it returns one-day weather forecast for ten cities.

The trick is to feed those tasks one by one. So the candidate is forced to change his codebase according to the new requirements. Almost like in real life. If a candidate is frustrated by such task - it means it is right one)

The downside of such approach is that it might take longer to implement than conventional all-in test task. So it's important to keep them short.

Some other examples of dynamic interview tasks

#### Shopping list
1. create a shopping list with item name, price, and quantity
2. take the shopping list and break it into three categories - meat, fruits vegetables

#### Image gallery
1. Create horizontal image gallery
2. Turn it to the vertical one

#### Image Editor
1. Implement editor that can turn images BW
2. Implement feature at editor that make it sepia

#### Login Page
1. Implement login page with username as an email + verification
2. Add to it zip and phone numbers + verification

We need to check if a person can use OOP effectively during the normal development process. To do that we’ll simulate the change of requirements that have to be mitigated by application of OOP and design patterns.


During the initial briefing, we need to emphasize the necessity to use git properly. Instruct the person to write proper commit messages and use tags to mark the completion of the subtask.
Mention that his project structure also will be examined. So candidate should pay attention to it. - You can call it task 0

Prepare a test backend to be used by candidate - one way to do that is to use a mock server with mock responses.
For backend candidates - use mock client (postman for instance)

#### Segmentation by candidate’s level
If tasks are generic enough to accommodate candidates with different levels of professional experience - that will save a lot of effort
Also, it will give the ability to compare candidates of the different level. And justify why the person is not qualified for this position.

#### Boilerplate code
Per - task should be decided whether or not the candidate should receive the boilerplate code, to begin with.
On one hand side, some tasks might require too much time for auxiliary code to be put in place.
On the other hand, if the candidate will receive pre-populated project - it will give him a lot of hints how to finish the task.

#### Conclusion
The dynamic interview process can help to better understand abilities of a particular candidate. On the flip side, they require quite a lot of effort to prepare and conduct an interview
