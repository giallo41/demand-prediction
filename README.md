# demand-prediction

------------------------------

### Contents of data

```
supply.csv
demand.csv
```

### Data preprocessing

1) supply.csv
- time frame :
  - timeslot available : 2018-01-08 ~ 2018-09-19
  - Operation Weekday : Mon, Tue(start from July-3), Wed, Fri, Sat
  - Time slot
```
  : Mon - MS(~11) / ES(18~)   
  : Tue - MS(~11)
  : Wed - MS(~11) / ES(18~)
  : Fri - MS(~11)
  : Sat - MS(09~14)

```
  - Some Exception :
    - 2018-5-11 open the time 16:00, 16:30, 17:00, 17:30 at some gird location
    - 2018-6-11 & 2018-03-26
    - no available area ratio at time of ( 15:00, 15:30 )=> Exclude

  - 'calculated_datetime' has later than day+'timeslot_from' => Exclude

<b>(1) From supply.csv -> find the time_delta between slot and calculated time

<b>(2) Exclude the data that has ( - ) time delta

<b>(3) Plot the distribution of timedelta

<b>(4) Hypothesis - that the available_area_ratio is the main contribute to predict the demand
  - calculate the min , max, mean, count , first(value), last(value)
  - I assume the last time calculated value of avail_area_ratio has strongly related to demand of unit grid

<b> (5) make the training data using 5 main factor (min, max, mean, first, last )

<b> (6) sum-up the 5-factors during the time shift
