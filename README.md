# Hotel Bookings Exploratory Data Analysis

## Objective
We are provided with a hotel bookings dataset. 

Out main objective is perform EDA on the given dataset and draw useful conclusions about general trends in hotel bookings and how factors governing hotel bookings interact with each other.

## Dataset
We are given a hotel bookings dataset. This dataset contains booking information for a city hotel and a resort hotel. It contains the following features.

```
- hotel: Name of hotel ( City or Resort)
- is_canceled: Whether the booking is canceled or not (0 for no canceled and 1 for canceled)
- lead_time: time (in days) between booking transaction and actual arrival.
- arrival_date_year: Year of arrival
- arrival_date_month: month of arrival
- arrival_date_week_number: week number of arrival date.
- arrival_date_day_of_month: Day of month of arrival date
- stays_in_weekend_nights: No. of weekend nights spent in a hotel
- stays_in_week_nights: No. of weeknights spent in a hotel
- adults: No. of adults in single booking record.
- children: No. of children in single booking record.
- babies: No. of babies in single booking record. 
- meal: Type of meal chosen 
- country: Country of origin of customers (as mentioned by them)
- market_segment: What segment via booking was made and for what purpose.
- distribution_channel: Via which medium booking was made.
- is_repeated_guest: Whether the customer has made any booking before(0 for No and 1 for 
                     Yes)
- previous_cancellations: No. of previous canceled bookings.
- previous_bookings_not_canceled: No. of previous non-canceled bookings.
- reserved_room_type: Room type reserved by a customer.
- assigned_room_type: Room type assigned to the customer.
- booking_changes: No. of booking changes done by customers
- deposit_type: Type of deposit at the time of making a booking (No deposit/ Refundable/ No refund)
- agent: Id of agent for booking
- company: Id of the company making a booking
- days_in_waiting_list: No. of days on waiting list.
- customer_type: Type of customer(Transient, Group, etc.)
- adr: Average Daily rate.
- required_car_parking_spaces: No. of car parking asked in booking
- total_of_special_requests: total no. of special request.
- reservation_status: Whether a customer has checked out or canceled,or not showed 
- reservation_status_date: Date of making reservation status.
```

- Total number of rows in data: 119390
- Total number of columns: 32
## Data Cleaning 

### (1) Removing Duplicate rows
All duplicate rows were dropped.

### (2) Handling null values
- Null values in columns `agent` were replaced by 0.
- Null values in column `country` were replaced by 'others'.
- Null values in column `children` were dropped as there are only four row with null values in children.
  

### (3) Converting columns to appropriate data types

- Changed data type of `children`, `company`, `agent` to int type.
- Changed data type of `reservation_status_date` to date type.

### (4) Removing outliers

- One outlier was found in the `adr` column. Simply dropped it.

### (5) Creating new columns
- Created new column `total_stay` by adding `stays_in_weekend_nights`+`stays_in_week_nights`.
- Created new column `total_people` by adding `adults`+`children`+`babies`.
- Created new column `arrival_date` by adding `arrival_date_year`+`arrival_date_month`+`arrival_date_day_of_month`.
- Created new column `arrival_day` of `arrival_date` .

## Exploratory Data Analysis

Performed EDA and tried answering the following questions:

```
 Q1) Which agent has booked most hotel and generate more revenue ?
 Q2) Relation between Revenue and total of special requests?
 Q3) Which meal type is the  most preferred meal of customers?
 Q4)  Which type of Hotel is mostly booked ?
 Q5)  Median lead time of each Hotel ?
 Q6) What are number of days of stay in each hotel ?
 Q7) Which group has stayed the most often at each type of hotel?
 Q8) Which category visit most in specific months?
 Q9) What are the average revenue collection in each month ?
 Q10) What are the date which are mostly visited ?
 Q11)  What are the days of the week mostly visited ?
 Q12)  Arrival day vs total stay ?
 Q13)  Which market segment attract more customer ?
 Q14)  Market Segment according to Hotel type ?
 Q15)  Market Segment revenue according to Hotel type ?
 Q16)  Which type of room is mostly demanded ?
 Q17)  Which type of room is mostly reserved ?
 Q18) Which type of room give highest revenue ?
 Q19) What are the percentage of customer assigned ,the reserved room ?
 Q20) Not assigned demanded room effects the revenue or not ?
 Q21) Does not assigned the same room effects cancellation ?
 Q22) Do lead time and days in waiting list affect cancellation ?
 Q23) What are the most visited country?
 Q24) Which country gives best deals and high revnue ?

```

Mainly performed using Matplotlib and Seaborn library and the following graph and plots had been used:
  -  Bar Plot.
  -  Histogram.
   - Scatter Plot.
   - Pie Chart.
   - Line Plot.
   - Heatmap.
- Box Plot
             
###  Univariate Analysis:

Performed univariate analysis and made following conclusions:
```
 1.) Agent no. 9 has made most no. of bookings.
 2.) Most demanded room type is A and D, but better adr generating rooms H and G. Hotels should increase the no. of room types A and H to maximise revenue.
 3.) Most popular meal type is BB(Breakfast).
 4.) Around 61% bookings are for City hotel and 39% bookings are for Resort hotel, therefore City Hotel is busier than Resort hotel.
 5.) best market segment for bookings is Online TA.
 6.) July- August are the most busier and profitable months for both of hotels. 
 7.) Most of the guests came from european countries, with highest number of guests from Portugal.
 8.) Most common stay length is less than 4 days and generally people prefer City hotel for short stay, but for long stays, Resort Hotel is preferred.
 
```




### Bivariate Analysis :

We tried to answer following questions
```
 1.) Adr of city Hotel is higher than Resort Hotel
 2.) Online TA is best marketing segment to attract customer(59%).
 3.) Not getting same room do affects the adr, people who didn't got same room have paid a little lower adr. 
 4.) In Resort Hotel 21% of people are not assigned the reserved room, this means in Resort Hotel there is demand of specific rooms
 5.) Not Assigned the same room as reserved,not only decrease the revenue but it also decrease the chances of best deals.
 6.) Not assigned the same room does not effect the cancellation.
 7.) Friday has highest number of 2 day visit,which can be weekend holidays.
 8.) There is slight increase in number of customer for a week,this may be because weekly plan provides good deals.
 9.) Moslty bookings are done by couples(bookings have two adults.)
 10.) Longer lead time has no affect on cancellation of bookings
```

## Conclusion

```
(1) Agent 9 has highest no of booking and revenue ,but in term of Average Revenue Agent 250 and Agent 14 are the highest
(2) Increase in total_request lead to increase in Revenue.
(3) Most of the visitor has opted for only Morning Breakfast(BB),there are also tourist who opted for HB,SC type meal but approximately no visitor has opted for 
    Full Board(FB) type meal
(4) For Resort Hotel there is drastically increase increase in number for One Week ,this may be because there is better deal for a week in Resort Hotel.
(5) People mostly stayed for upto 4 days .Highest number of days of stay is 1. For long days people mostly prefer Resort Hotel and for short days ,City Hotel.
(6)  Most(65%) of the visitor type are couple's and after most of the visitor are Not family(25%)
(7) August and July is the most visited month of the year.This is maybe mostly summer holidays lie in July and August.
(8) Customer mostly arrive in Monday and Friday,The high number of visitor in Friday may be due to weekends
(9) Almost (59%) of people belong to online TA market segment whereas Offline TA/TO has (15.9%) market segment followed by Direct(13.5%)
(10) In term of revenue Online TA city hotel has highest revenue and also highest Average Revenue.
(11) The Average Revenue increases from Room type A to Room type H,after that it falls drastically.
(12) In city Hotel,11% are not Assigned the reserved room whereas in resort Hotel,21% are not Assigned the reserved room.
     This means in Resort Hotel there are shortage of specific room types whichare high in demand
(13) Not Assigned the same room,not only decrease the revenue but it also decrease the chances of best deals.
(14) Switzerland(CHE),Belgium(BEL) and Spain(ESP) has highest Average Revenue but the best deals are mostly from Spain and Portugal 

And many more conclusions.
```
## Challenges
```
(1) A lot of the data were duplicates.
(2) Incorrect datatype format for the data was present.
(3) It was challenging to select the best visualization techniques.
(4) The dataset contained a large number of null values.





