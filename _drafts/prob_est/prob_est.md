# Fast Estimation or Probabilistic Estimation Value

## Intro

Fast estimations like fast food - cheap, crappy, greasy, but a necessary attribute of the everyday life.

Have you ever been in a position where you were tasked with creating an estimation for a software project you'd never heard before within 3 hours time frame?
I was. It was tons of fun (sarcastic neurotic laugh)

In this article, I try to describe approach you can use if you ever find yourself in such desperate hot-bed position


## What projects are we talking about?

Just to be clear - I'm not describing 100% reliable certified way to estimate any software project at no time.
I'm talking about 0.5 - 1-year project length estimation.
And I'm actually talking only about an early draft of the estimate. Something you can put on a table for your sales guy fast. And not to lose sleep after that:)

## Estimation Requirements

[Uncle Bob](https://sites.google.com/site/unclebobconsultingllc/)  has an excellent video about [Effective Estimation](https://www.youtube.com/watch?v=eisuQefYw_o). And he highlighted three main qualities of the good estimate

It must be:

- honest
- precise
- accurate

### Honest

How can you measure that? Honest - what does it even mean?


My rule of thumb - honest estimate is the one you personally willing to implement being under some mild medical condition.
Imagine you have to commit to your own estimates while you have your season flu.
If you are still willing to do that - then it must be an honest estimate.

### Precise

Precise - it means that if you were tasked to estimate three similar projects we should get three alike estimation data. If one CMS for a medium-size retail company will take one man/year to implement, then another CMS for similar size company should not take five man/years or 3 dog/weeks to do.

Make sure your numbers are non-contradictory and don't raise the questions on your sanity or professionalism. About Screen can not take longer to implement than the front page of your app. Simple RESTFull service should not take longer to do then AI-based self-tuning self-espresso-making analytic service.

Any eyebrows-lifting numbers at your estimate can undermine trust to your work. And without a trust to the estimate they worth nothing.

Also, it's quite useful to do the reality check before you show your estimate to somebody else. If you were asked to make a toilet-locator app, it should not take three years to do that.

### Accuracy & Real World Conditions

The estimate should be accurate. Which means the gap between estimated effort and actual effort should be minimal. If you say that the project should take three month - it's highly desirable that it actually will be ready within three weeks period.

And accuracy is a really [tough cookie](http://coub.com/view/vc4p1). Mostly because estimation process is:

- Time constrained
  - You do not have a lot of time to make the estimate. Especially if we're talking about pre-sales activities. The salesman needs everything and now. No exceptions.
- Information constrained
  - You do not have full info to make the estimate. Sometimes you have just a paragraph worth of text. Sometimes just a napkin with your boss drunk handwriting on it. [GoogleIT(@)](http://www.justfuckinggoogleit.com/) can help. But mostly you will be in the severe information-deprived environment.

And to get more info you need more time. Which you don't have.

In addition

![alt text](/Users/abatutin/Dropbox/SR_web/ch1.jpg "Time vs Accuracy")

  - estimation accuracy grows logarithmically
  - estimation time effort increases exponentially

Which means that even with a substantial time effort estimate still will have some degree of an error. And it can be quite big.

## Probabilistic Nature off the Estimate

That brings us to the probabilistic nature of the estimate.

You can hardly express the time effort required to do the software project with one number and be honest, precise and accurate about it.

The estimate is a probabilistic value.

The honest, precise, and accurate way to present estimate is to say: it will take about 6 weeks with 95% success chance. Or it will take about 4 weeks but with only 65% chance of success.

Or we can present estimate as a range value assuming 95% chance of success by default. So: most likely it will take from 5 to 7 weeks.

## Units

Before we go forwards let's define some units used to measure the estimate.

Quite often staff-hour/day/month metric is used. It says how many hours/days/months will take one man to do the job.

There are a couple of issues I find with that. First of all, not everybody is a man. Second, it always was a bit misleading for me. I always tend to imagine 1 staff-day like straight 8 hours coding sprint. Which is obviously unrealistic. Programmers don't code 100% of their time. Planning, meetings, coffee, frustrations - it all steals our precious workday time.

So for this article, I'm going to use Average Working Day (AWD) unit of measurement.

Think about 1 AWD as the amount of work 1 average developer can accomplish during 1 day that consists of 5 hours of coding and 3 hours of talking to strangers in a closed room.

Also, we usually don't work alone but in the team. And there is an age old issue of scaling the estimation according to the team size. See "9 Women Can’t Make a Baby in a Month" and [Brook's law](https://en.wikipedia.org/wiki/Brooks%27s_law) for details. But we'll omit those details for the sake of simplicity and will just assume that 2 humanoid creatures can accomplish 2 AWD in 1 day, 4 - at 0.5 days, etc...

## Estimate range calculation

Now let's discuss how exactly can we calculate probabilistic estimate value.

### [3-point Estimation](https://en.wikipedia.org/wiki/Three-point_estimation)

The idea is simple - in order to estimate a project you break it on the work item and then estimate each item with 3 figures:

- b = the best-case estimate (95% chance of missing)
- n = the nominal estimate (50% chance of missing)
- w = the worst-case estimate (5% chance of missing)

Think about best-case estimate as if Odin himself came down to the desk and forced the project with all his might and wisdom through. The best-case estimate is the smallest possible amount of time required to do the job within best possible circumstances. The item will take longer to implement with 95% chance.

The nominal estimate is the most realistic one. Pay attention to this figure. It has the most weight in upcoming calculations. This estimate should be medium-optimistic value achievable under you normal working conditions. You have 50% chance of missing this estimate.

The worst-case estimate is the one you should give for the case when everything goes wrong. Your laptop is attacked by a giant worm. Your design guy turns out to be a drug-addicted monkey. You've been called up to an army day before release. This is the worst possible figure you can give to the work item. And there is 5% chance that the item will take longer to implement than you've estimated.

Formally ```b < n < w``` should always be true. You can't have worst case estimate smaller than the nominal one. Sorry.

Let's take a look at the simple example to demonstrate the concept in action.

#### Sample project requirements:

```
The web-service should allow the user to log in to an existing account.
Buy the product from the predefined list of commodities. And review its purchase history.
```

Let us assume we have extracted 3 work items from this description.

| #        | Work Item Name     |
| -------- |:------------------:|
| 1        | User Login         |
| 2        | Purchase Commodity |
| 3        | Purchase History   |

#### Sample three-point estimate.

Let's assume we've estimated those work items in the next fashion.

| #        | Work Item Name     | b  | n  | w    |
| -------- |:------------------:|:--:|:--:|:----:|
| 1        | User Login         | 10 | 30 | 100  |
| 2        | Purchase Commodity | 15 | 40 | 150  |
| 3        | Purchase History   | 2  | 10 | 20   |

*all estimate values are in AWD*

#### [Standard Deviation](https://en.wikipedia.org/wiki/Standard_deviation) and [Weighted Mean](https://en.wikipedia.org/wiki/Weighted_arithmetic_mean) of the Estimate

Mean effort for each work item is calculated as a weighted mean  as:

```
m = (b + 4n + w)/6
```

Why do we have the factor of 4 for nominal effort? Because it's the most realistic one. And we want to emphasize it most. Why 4 but not 5 or 3 - because of [Rocket Science](https://stackoverflow.com/a/22241069).

It's just a fancy way to get average effort value prioritizing nominal estimate above others. For total project mean we just sum up work item's mean values.

And we get:

| #        | Work Item Name     | b  | n  | w    | m    |
| -------- |:------------------:|:--:|:--:|:----:|:----:|
| 1        | User Login         | 10 | 30 | 100  | 38   |
| 2        | Purchase Commodity | 15 | 40 | 150  | 54   |
| 3        | Purchase History   | 2  | 10 | 20   | 10   |
|||||Project Total Mean|102|

*all estimate values are in AWD*

Now let's calculate [standard deviation](https://en.wikipedia.org/wiki/Standard_deviation) of the work item estimate with

```
s = (w - b)/6
```

And total estimate standard deviation with

```
S = SQRT(SUM(s)^2)
```

For the Sample Project we'll have:

| #        | Work Item Name     | b  | n  | w    | m    | s  |
| -------- |:------------------:|:--:|:--:|:----:|:----:|:--:|
| 1        | User Login         | 10 | 30 | 100  | 38   |15|
| 2        | Purchase Commodity | 15 | 40 | 150  | 54   |22.5|
| 3        | Purchase History   | 2  | 10 | 20   | 10   |3|
|||||Project Total Mean|102||
|||||Project Standard Deviation||40.5|

Standard deviation says how variative your estimate values are. Higher it is - more widespread your estimates are. I would not recommend throwing this number at anyone without a degree at Math & Statistics.

These numbers we need to be able to approximate our estimation data with Beta-distribution. And thus calculate our probabilistic estimation value.

#### Beta-distribution

In order to get the probability of the estimate, I've chosen to use [Beta-distribution](https://en.wikipedia.org/wiki/Beta_distribution). Why Beta-D - because it's used within [PERT](https://en.wikipedia.org/wiki/Program_evaluation_and_review_technique).

Detailed description of how to calculate Beta-distribution based on three-point estimate you can find [here](http://www.laserlightnetworks.com/Documents/Model%20PERT%20Project%20Schedules%20with%20the%20BETA%20Distribution%20using%20EXCEL.pdf)

In general, it calculates the probability based on your mean and standard derivation values.

For the Sample Project, we'll have next cumulative beta-D

![alt text](/Users/abatutin/Dropbox/SR_web/cum.png "Cumulative Sample Project Beta-Distribution")

The way to read this chart is next: the project will take about 177 AWD to be done with 95% chance of success.

Here is a little table:

| Chance of Success| Effort (AWD) |
|:--:|:--:|
|95 %| 177|
|70 %|122|
|50 %|98|

If you compare it with the mean value (102 AWD), you'll see why you shouldn't just use mean value as your final estimate.

So here it is - your Probabilistic Estimation Value.

##### Estimation Range

If you're not comfortable with all that probability stuff then you might just give a range value using next rule:

```
The 95% confidence interval for the true project work time is approximately Project Total Mean ± 2 × Project Standard Deviation
```

We use the factor of 2 based on [68–95–99.7 rule](https://en.wikipedia.org/wiki/68%E2%80%9395%E2%80%9399.7_rule).

So for the sample project, it will be: It will take from 21 to 183 days.

Or you can drop the lower bound and just say: It will take from 102 to 183 days.

Of course, you can use ```Total Mean ± 1 × Project Standard Deviation``` formula but please note that then you're talking about 68% chance of fitting into the range.

## Sample Excel Workbook

You can find [here](sds) Excel book with sample project estimation. Use it for good:)

## Additional requirements

Make sure you've defined work items as independent as possible.

Also, it's recommended to have 20 work items or more to get the adequate result.

## Conclusion

Estimation of the software project is far from exact science. And it will never be the one. 3 point estimation methodology is not a silver bullet. But it can give you more confidence in your estimates. And your confidence can help you to grow a trust. And trust is really what holds all the estimation process together.

## P.S.

After I've done a couple of estimations, I've decided to calculate their actual accuracy. I wanted to calculate the error between estimated and actual project development effort. And I was not able to do that. Some of the estimated projects were not launched. Other transformed during the dev process so much that it was not possible to match their's duration against original work items.
And I have a strong suspicion that this is not a coincidence. Software development is a highly volatile process. Rarely the system you've planned comes up the way you imagined it at the beginning. Thus calculating the accuracy of your original estimate is virtually impossible. You might be able to figure out estimation accuracy for some work items. But hardly you can get the actual estimate accuracy for the entire project.
So how should you estimate software projects to get verifiable results? Good question. I don't know) Look [here](https://getpocket.com/a/read/1094154281) for one of the ideas. But it's still very much an open question.
