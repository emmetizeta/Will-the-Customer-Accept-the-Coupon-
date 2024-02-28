# Will a Customer Accept the Coupon?
**Alessandro Morato**

**BH-PCMLAI, January 2024**
## Preliminary Data Cleaning
<div align="justify">
An initial data cleaning was carried out.

Some features presented NA values:
* "Car" with 99% of values missing. Being basically empty, it was removed. All persons interviewed were considered "drivers".
* "Bar", "CoffeeHouse", "CarryAway", "RestaurantLessThan20", "Restaurant20To50" with around 1% of values missing. In this case the missing information was quite small and the vast majority of rows still contained meaningful information: therefore I decided to keep all the rows and to replace the missing values in each field with the mostly recurrent ones in the other rows.

The feature "toCoupon_GEQ15min" only presented value 1, meaning that all the coupons are farther than 5min. Therefore I designed a dedicated function to reclassify the time distance as "5-15min", "15-25min" and ">25min".

## General observations
Different types of coupon were available, for: bars, coffee houses, take-aways and restaurants (less expensive under $20, or more expensive over $20). The general mean acceptance rate is **57%**. While the coupons are mainly for bars, the most accepted ones are for take-aways.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/d0f6f501-7841-4e9a-a1fa-e64ee2c99150)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/c713a43b-f6d5-41ed-81c0-fde8dadd0aa2)>
</p>

## Part 1: Coupons for Bars
### *How frequency influences acceptance rate*

Acceptance rate of the whole bar-coupon group is **41%**. I found that drivers already used to
bars (at least 1 time per month) are much more likely to accept coupons: indeed the rate
increases considerably.

>*Acceptance rate of those who went to a bar 3 or fewer times a month: **37.1%***
>
>*Acceptance rate of those who went to a bar >3 times a month: **76.9%***

This is also well evident by the following plots, where bars "Greater than 8" (gt8) and "4-8" have higher
accepted percentages than the others. It is also interesting to observe that said categories
(gt8, 4-8) have a lower number of distributed coupons: this makes sense, since these
persons are already good customers, so it is better to focus on persons who currently do not
come often to bars (<= 3 times per month). Considering the general acceptance rate (41%), even an average frequency of 1 per month gives a considerable improvement: frequency seems a key feature.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/d353519d-0787-43b1-880a-629fb788678b)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/625dd6e4-3efb-46ca-ae64-9a55457f3bbb)>
</p>

### *How frequency and age influence acceptance rate*

>*Acceptance rate of drivers who go to a bar more than once a month AND are over the age of
25: **69.5%***
>
>*Acceptance rate of others: **33.5%***

The percentages suggest the first group is more likely to accept a coupon. This is resonable:
the previous paragraph reveals how drivers already familiar with bars are more likely to accept coupons.
Regarding acceptance rate related to the age, the analysis shows how there is a difference between groups under and over
25y (48% vs 38%): the population older than 25y has a slight lower acceptance rate. However, if I compare the acceptance rates reported above with the ones only depending on the frequency (>1 per month, 69% and
29%), they are not quite different. This suggests to me that age and frequency could be not very
correlated.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/eff0c45c-4b2f-40d4-954c-e71fea9a11cd)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/4df1d359-7738-49b7-b6a5-d5b6e21be885)>
</p>

### *Considering other characteristics of drivers*
>*Acceptance rate of drivers who go to bars more than once a month AND had passengers that
were not a kid AND had occupations other than farming, fishing, or forestry: **71.3%***
>
>*Acceptance rate of others: **29.6%***

>*Acceptance rate of drivers who go to bars more than once a month AND are under the age of
30: **72.2%***
>
>*Acceptance rate of others: **34.6%***

>*Acceptance rate of drivers who go to cheap restaurants more than 4 times a month and
income is less than 50K: **45.3%***
>
>*Acceptance rate of others: **40.1%***

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

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/8614808e-cfbd-4ab7-91ff-25f87a04b131)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/aa5a2db1-eb42-4f9c-b00f-50a279c83248)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/39fc3925-4010-4e0b-9735-9616a5c94103)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/934cd2ef-88c0-44fd-912b-fe2edca28704)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/d1f28cf0-f005-4b96-98a0-0c91d1f20a30)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/0f761cea-e9d9-42f5-aa5f-7b6f5c86ede8)>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/b3b83afc-8a56-4505-aab5-0afeda72a899)>
</p>

## Part 2: Coffee Houses

Before deciding which type of coupon I want to investigate, I recovered the initial plot of
coupons distributed to the drivers: this allowed me to see how they are distributed. The most
common coupon is the one for "Coffe Houses" (nearly 4k coupons distributed). The plot is
very clear in reporting an acceptance rate close to 50%.

As observed in the previous dataset, being already a customer increases the acceptance
rate: a frequency of >1 per month provides an acceptance rate of 66%.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/8144277e-ff7b-4107-85c0-a8a87c083137>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/85cdc052-cb92-48c1-a7b2-96b43e501697>
</p>

### *The influence of frequency*

Since I observed that frequency at Coffee Houses highly affects the acceptance rate, I tried
to link the following considerations to this feature.

Regarding the “age”, as observed in the "Bar" analysis, this doesn't have a huge impact on
the analysis: there is a slightly higher acceptance ratio for drivers <30y over older drivers. By
looking at the younger group there is an improvement of 3% (from 50% to 53%) and the
same improvement can be observed limiting the analysis to the group more used to Coffee
Houses, >1 per month (from 66% to 69%).

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/1cf31716-34e1-473e-aa23-ead463dbdbdc>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/753dac66-01e7-460c-8a5f-61d701dc194d>
</p>

### *People's education*

"Education" looks related to this analysis. The more targeted drivers are the ones with
advanced instruction diplomas: this makes sense to me, since Coffee Houses seem a nice
place to study or to meet cohorts. Or just the right place for sophisticated hipsters... Restricting the analysis to drivers already used to Coffee Houses further highlights the tendency and also increases the accepted ratios (all well above >50%).

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/545f8ae3-b554-4d33-8446-77b6743edbb9>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/fb7c239a-7841-4b3f-90e3-c79eea77938f>
</p>

### *People's income*

"Income" provides an insight similar to the one observed for Bars: low incomes and very high
incomes (>100k) are the most targeted by coupon distribution. Regarding the acceptance
rate, it looks like that low incomes (<62.5k) are more likely to accept coffee coupons: said
low incomes indeed have an acceptance rate of 55% vs 49% of higher incomes. Frequency
affects the percentages as a bias, drifting the values to 71% vs 65%.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/80028f83-62fa-4629-a338-79fd875c4bf8>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/a0cb0445-01ca-47aa-837f-d5982607df46>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/b4bd7345-21f2-499a-8f32-60369a5e0790>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/396ae40d-7d2c-4d2d-a842-db831d673694>
</p>

### *People's occupation*

"Occupation" covers a wide range of jobs. It is interesting to see which ones are very unlikely
to either receive a coupon or accept it. There is a general tendency to increase the
acceptance ratio by restricting the analysis to the habitual customers (minimum acceptance
rate from 40% to 60%). One consideration: one of the most targeted groups is "Students"
and this agrees with the considerations done regarding "Education".

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/51e039d1-e8f7-46aa-9ae3-ca0412d04759>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/88c1204d-f3d8-4307-b83d-8c73b397099f>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/eb609684-2ba1-4358-a126-b15594a38d5b>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/43fa5aa2-c2d4-473d-8bc8-fbbc572f37c7>
</p>

### *Passengers onboard: does this make any difference?*

Regarding the onboard passengers, there is a clear tendency in distributing coupons to
alone drivers: this makes sense to me, because everyone is more willing to stop for a coffee
when with others. Involving only habitual customers, the trend of distributed numbers doesn't
change much but the acceptance ratios are very pushed: drivers with a frequency of >1 per
month with Friend(s) or Partner have an acceptance rate close to 80%. This seems like a
very interesting parameter.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/5a211ca9-f553-4c2b-afed-97fd672fcd31>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/6e5fc57e-cc6b-4122-b991-14de78a33ce9>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/3add43b6-b3de-43c8-a1f9-499da5ff5224>
</p>

### *How far (in minutes) is the Coffee Shop?*

Very few coffee coupons are distributed for places further than 25 minutes.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/a37cf3e4-e9c3-4d43-81a9-0622d2c9c6c6>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/b652f62d-5e7f-4f1d-b294-10d36f859ecc>
</p>

### *Time, weather, temperature Matter*

Coffee coupons are distributed throughout the whole day, with much less frequency at 10PM: this
is not a very appealing time for a coffee. Regarding whether and temperature, there is a clear
peak in distributed coupons during sunny and warm days.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/e6699cb0-b8d6-4caf-b355-9873b731ea36>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/0c28e1b4-0e76-433d-a20c-46bdf12e5ad0>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/bebd191a-7a09-4384-86d6-157157cb2882>
</p>

### *Where is the driver going to? And... when, with whom?*

I tried to relate the destination of the trip to the "passenger(s)" and the "time" of the trip.

***a. Destination vs Passenger(s)***
- There is a clear tendency to accept coupons with any passenger, if the trip is to a
no-urgent place. As already observed, "Friends" and "Partner" in particular increase the
acceptance rate.

- "Work" as destination is for solo drivers only (44% acceptance)

- "Home" as destination is for drivers alone (35% accepted) or with the partner (55%
accepted)


***b. Destination vs Time***
* When traveling to no-urgent place, I wasn't surprised to see that no coupons are
distributed early in the morning (7AM). The most popular accepted time is 10AM (64%
accepted)

* When traveling to work the only time covered is of course early morning (7AM), 45%
accepted.

* When traveling to Home, the only times are late afternoon or evening (6PM, 10PM), they
do not look very appealing.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/b5bb33a6-85a6-4fef-91a8-a1c63c891e03>
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/d4491aef-111f-4665-958f-8e68d17dd52c>
</p>

### *Do Gender and Marital Status count?*

Relating gender and marital status, it is evident that males are more open to accepting coupons,
in particular Single and Divorced ones.

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/c702e48e-90a6-4fec-a93e-f2983664f2ed>
</p>

### *Are customers of other commercial activities potential good Coffee Shop customers?*

Looking at the habits with other shops, i see that there are many accepted coffee coupons
among drivers going:
- less 1 per month at good restaurants
- going 1-3 times per month to cheap restaurants
- less 3 times per month to bars
- 1-8 times per month to Carry Aways

<p align="center">
<img src=https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/assets/101027884/c54946fa-4493-4db7-92a9-364a523cf161>
</p>

### *Final thoughts regarding the Coffee Shops: The Best Customer*

To conclude, I tried to identify some potential "TOP" groups very likely to accept a coffee coupon.
For instance, one group with a very high acceptance rate is:

>*drivers with a coffee house frequency more than 1 per month AND income <50k AND Friends as
passengers AND job in Tech → Acceptance rate: 95% (acceptance rate of drivers not included is
49%).*

The analysis revealed that the insights gained could provide valuable indications to maximize the
return of the coupons sent.

## Reference
This analysis, the graphs and all the numeric values reported have been provided by the Jupyter worksheet here reported 
[LINK](https://github.com/emmetizeta/Will-the-Customer-Accept-the-Coupon-/blob/main/prompt.ipynb)
</div>
