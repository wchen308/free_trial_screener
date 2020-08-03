# Udacity Free Trial Screener Experiment

## Experiment Overview: Free Trial Screener
At the time of this experiment, Udacity courses currently have two options on the course overview page: "start free trial", and "access course materials". If the student clicks "start free trial", they will be asked to enter their credit card information, and then they will be enrolled in a free trial for the paid version of the course. After 14 days, they will automatically be charged unless they cancel first. If the student clicks "access course materials", they will be able to view the videos and take the quizzes for free, but they will not receive coaching support or a verified certificate, and they will not submit their final project for feedback.

In the experiment, Udacity tested a change where if the student clicked "start free trial", they were asked how much time they had available to devote to the course. If the student indicated 5 or more hours per week, they would be taken through the checkout process as usual. If they indicated fewer than 5 hours per week, a message would appear indicating that Udacity courses usually require a greater time commitment for successful completion, and suggesting that the student might like to access the course materials for free. At this point, the student would have the option to continue enrolling in the free trial, or access the course materials for free instead. This screenshot shows what the experiment looks like.
![Experiment Screenshot](img/experiment_screenshot.png)

The hypothesis was that this might set clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time—without significantly reducing the number of students to continue past the free trial and eventually complete the course. If this hypothesis held true, Udacity could improve the overall student experience and improve coaches' capacity to support students who are likely to complete the course.

The unit of diversion is a cookie, although if the student enrolls in the free trial, they are tracked by user-id from that point forward. The same user-id cannot enroll in the free trial twice. For users that do not enroll, their user-id is not tracked in the experiment, even if they were signed in when they visited the course overview page.

## Metric Choice
### Invariant Metric
The unit of diversion of this experiment is a cookie, hence number of cookies should remain the same between control and experimental group. Also, the tendancy to start free trial should remain the same between 2 groups, so that we can quantify the effect of free trial screener. Hence, number of clicks of 'Start free trial' button should be an invariant metric too. Consequently, click through probability, which is a ratio between the above 2 metrics are also an invariant metric.

Here are the 3 invariant metrics in this experiment:

**Number of cookies**: number of unique cookies to view the course overview page

**Number of clicks**: number of unique cookies to click the "Start free trial" button

**Click Through Probability**: number of unique cookies to click the "Start free trial" button divided by number of unique cookies to view the course overview page

### Evaluation Metric
Here is a funnel of a user behavior in this case:
1. click into course overview webpage (Pageviews)
2. click 'start free trial' button (Clicks)
3. control group: no free trial screener vs experimental group: a free trial screener
4. enroll and start free trial (Enrollments)
5. leave or remain in this course in free trial and pay (Payments)

In short, 2 effects are expected from a free trial screener:
1. **churn rate** during free trial due to not enough time is expected to <font color = red>reduce</font> with a free trial screener
2. **Retention rate** during free trial is expected to <font color = red>increase</font> with a free trial screener, since the number of people in step 4 is expected to reduce and number of people that remain in this course is expected to remain unchanged.

Hence, churn rate can be quantified as conversion from step 2 to step 4 and step 5. Retention rate can be quantified as conversion from step 4 to step 5.


Here are the 3 evaluation metrics that are used in this experiment:

**Gross conversion**: number of user-ids to complete checkout and enroll in the free trial divided by number of unique cookies to click the "Start free trial" button.(dmin= 0.01)

**Net conversion**: number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by the number of unique cookies to click the "Start free trial" button.(dmin= 0.0075)

**Retention**: number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by number of user-ids to complete checkout.(dmin= 0.01)
