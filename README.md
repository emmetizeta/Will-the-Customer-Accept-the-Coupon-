# Will a Customer Accept the Coupon?
**Alessandro Morato**

**BH-PCMLAI, January 2024**


## Preliminary Data Cleaning
A preliminary data cleaning has been carried out, to correct NaN values present, eliminate
useless data (e.g. column Car) and structure the dataset to make the analysis easier.

## Part 1: Bars
### *Frequency at Bars*

Acceptance rate of the whole bar-coupon dataset is 41%. I found that drivers already used to
bars (at least 1 time per month) are much more likely to accept coupons: indeed the rate
increases considerably.

Acceptance rate of those who went to a bar 3 or fewer times a month: 37.1%

Acceptance rate of those who went to a bar >3 times a month: 76.9%

This is also well evident by the plots, where bars "greater than 8" and "4-8" have higher
accepted percentages than the others. It is also interesting to observe that said categories
(gt8, 4-8) have a lower number of distributed coupons: this makes sense, since these
persons are already good customers, so it is better to focus on persons who currently do not
come often to bars (<= 3 times per month).

### *Frequency and Age*

Acceptance rate of drivers who go to a bar more than once a month and are over the age of
25: 69.5%

Acceptance rate of others: 33.5%

The percentages suggest the first group is more likely to accept a coupon.
Regarding the age, the analysis shows how there is a difference between under and over
25y (48% vs 38%): the population older than 25y has a lower acceptance rate and this could
explain the lower percentage compared to point. However, if I compare the acceptance rates
reported above with the ones only depending on the frequency (>1 per month, 69% and
29%), they are not quite different. This suggests to me that age and frequency are not very
correlated.

### *Considering Other Characteristics*
Acceptance rate of drivers who go to bars more than once a month and had passengers that
were not a kid and had occupations other than farming, fishing, or forestry: 71.3%

Acceptance rate of others: 29.6%

Acceptance rate of drivers who go to bars more than once a month and are under the age of
30: 72.2%

Acceptance rate of others: 34.6%

Acceptance rate of drivers who go to cheap restaurants more than 4 times a month and
income is less than 50K: 45.3%

Acceptance rate of others: 40.1%

Regarding the combinations "frequency >1 AND passenger NO Kids AND job in farming" vs
"frequency >1 AND passenger NO Kids AND marital status Widow" they have the same
acceptance rate because the population with "frequency >1" hasn't anyone in farming or
widow: this means we are considering the same group twice. Therefore, drivers often at bars
are unlikely in farming and widows. Another insight is related to the kids onboard: if drivers
with a frequency >1 have an acceptance rate of 69%, the ones without kids onboard have an
acceptance rate of 71.3%. This means that no-kids onboard could slightly increase the
acceptance rate: this makes sense, since a bar isn't a place for kids... In general drivers
alone are ones receiving more coupons for bars, and the ones more responsive are the ones
driving with friends.

Regarding the group of drivers going to cheap restaurants AND with an income <50k, the
acceptance rate is 45%. Looking at the distribution of coupons as a function of income, the
most covered classes are the low incomes (<62.5k) and the high incomes(>100k): therefore
the population here is a good insight into a wide portion of drivers. Regarding the frequency
at cheap restaurants, this actually affects the number of distributed bar coupons: the biggest
targets are drivers going to cheap restaurants 1-8 times per month (1-3 highest group). The
population here investigated (>4 per month) is not the biggest one, but it isn't negligible
though. Regarding both income and frequency at cheap restaurants, both covered
categories (income <50k, frequency >4 per month) show an average acceptance percentage
of 40-45% each: the combined one is very close.

## Part 2: Coffee Houses

Before deciding which type of coupon I want to investigate, I recovered the initial plot of
coupons distributed to the drivers: this allowed me to see how they are distributed. The most
common coupon is the one for "Coffe Houses" (nearly 4k coupons distributed). The plot is
very clear in reporting an acceptance rate close to 50%.

As observed in the previous dataset, being already a customer increases the acceptance
rate: a frequency of >1 per month provides an acceptance rate of 66%.

Since I observed that frequency at Coffee Houses highly affects the acceptance rate, I tried
to link the following considerations to this feature.

Regarding the “age”, as observed in the "Bar" analysis, this doesn't have a huge impact on
the analysis: there is a slightly higher acceptance ratio for drivers <30y over older drivers. By
looking at the younger group there is an improvement of 3% (from 50% to 53%) and the
same improvement can be observed limiting the analysis to the group more used to Coffee
Houses, >1 per month (from 66% to 69%).

"Education" looks related to this analysis. The more targeted drivers are the ones with
advanced instruction diplomas: this makes sense to me, since Coffee Houses seem a nice
place to study or to meet cohorts. Restricting the analysis to drivers already used to Coffee
Houses further highlights the tendency and also increases the accepted ratios (all well above >50%).

"Income" provides an insight similar to the one observed for Bars: low incomes and very high
incomes (>100k) are the most targeted by coupon distribution. Regarding the acceptance
rate, it looks like that low incomes (<62.5k) are more likely to accept coffee coupons: said
low incomes indeed have an acceptance rate of 55% vs 49% of higher incomes. Frequency
affects the percentages as a bias, drifting the values to 71% vs 65%.

"Occupation" covers a wide range of jobs. It is interesting to see which ones are very unlikely
to either receive a coupon or accept it. There is a general tendency to increase the
acceptance ratio by restricting the analysis to the habitual customers (minimum acceptance
rate from 40% to 60%). One consideration: one of the most targeted groups is "Students"
and this agrees with the considerations done regarding "Education".

Regarding the onboard passengers, there is a clear tendency in distributing coupons to
alone drivers: this makes sense to me, because everyone is more willing to stop for a coffee
when with others. Involving only habitual customers, the trend of distributed numbers doesn't
change much but the acceptance ratios are very pushed: drivers with a frequency of >1 per
month with Friend(s) or Partner have an acceptance rate close to 80%. This seems like a
very interesting parameter.

Very few coffee coupons are distributed for places further than 25 minutes.

Coffee coupons are distributed throughout the whole day, with much less frequency at 10PM: this
is not a very appealing time for a coffee. Regarding whether and temperature, there is a clear
peak in distributed coupons during sunny and warm days.

I tried to relate the destination of the trip to the "passenger(s)" and the "time" of the trip.

### *a- Destination vs Passenger(s)*
- There is a clear tendency to accept coupons with any passenger, if the trip is to a
no-urgent place. As already observed, "Friends" and "Partner" in particular increase the
acceptance rate.

- "Work" as destination is for solo drivers only (44% acceptance)

- "Home" as destination is for drivers alone (35% accepted) or with the partner (55%
accepted)

### *b- Destination vs Time*
* When traveling to no-urgent place, I wasn't surprised to see that no coupons are
distributed early in the morning (7AM). The most popular accepted time is 10AM (64%
accepted)

* When traveling to work the only time covered is of course early morning (7AM), 45%
accepted.

* When traveling to Home, the only times are late afternoon or evening (6PM, 10PM), they
do not look very appealing.

Relating gender and marital status, it is evident that males are more open to accepting coupons,
in particular Single and Divorced ones.
Looking at the habits with other shops, i see that there are many accepted coffee coupons
among drivers going:
- less 1 per month at good restaurants
- going 1-3 times per month to cheap restaurants
- less 3 times per month to bars
- 1-8 times per month to Carry Aways

To conclude, I try to identify some potential "TOP" groups very likely to accept a coffee coupon.
For instance, one group with a very high acceptance rate is:

*drivers with a coffee house frequency more than 1 per month AND income <50k AND Friends as
passengers AND job in Tech → Acceptance rate: 95% (acceptance rate of drivers not included is
49%).*

The analysis revealed that the insights gained could provide valuable indications to maximize the
return of the coupons sent.
