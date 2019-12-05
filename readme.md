# US Flights Data Exploration
## by Jesús Mira Aldao


## Dataset

This document explores the data related with the aeronautical sector in the USA along 25 years. The data have been gathered from the site http://stat-computing.org/dataexpo/2009/the-data.html. In this page we can download information related with the flights made in the US territory since 1987 to 2008. This data englobes information like Distance, Time Schedules, Delays, etc. 


## Summary of Findings

### Univariate Analisis

* Most of the variables of time  and the distances are right-skewed. And some of them seem log-normal ditributed like the Distance, the CRSEsquedulled and the ElapsedTimeEsqueduled.

* The Departure Delay and the Weather Delay have some periodical peaks every five minutes.

* In the case of weather delay there is also a some flat like distribution between the five and the ten minutes, then decrease until the fifteen minutes where again there is a peak, but in this case isolated.

* The NAS delay has like two sawteeth. One starting in cero, it decrease gradually until fifteen minutes where it has a peak an then decrease gradually again.

* The security delay has a great peak in seven or eight minutes and then decreas gradually wiht the exception of the fifteen minutes where it has an isolated peak.

* And finally, the late aricraft delay increase gradually the number of cases until 15 minutes where it has a great step to decrease gradually after it.

### Bivariate Analisis

#### Scatter plot between ActualElapsedTime and CRSElapsedTime: 

* Most of the the flights follow a linear patter described by x = y, but we can see clearly that for an schedulled time smaller than 400 minutes the spread of the actual elapsed time is clearly bigger. It seems that the delays are bigger in this range of time, but this can be because the dataset doesn't have some many information about the delays for the longer trips, not because they don't actually have so much delay. We can't know that.

* We can see also some outliers. Schedulled delays negative? It is strange. And there are some long flights that seem to have a limit in the schedulled time around 400 minutes (I saw this in the original file, in this sample it is not so clear).

#### Scatter plot between ArrDelay and DepDelay:

* These two variables describe a linear relationship one to one in the upper side. And for small delays we could draw a line y=a+x describing an upper limit for the samples. Is like the ArrDelay were always smaller than DepDelay more a constant. When the delays are not enormous, less than 500 minutes, the behaviour is normal, I mean that the Arrival Delay tends to be greater than the Departure Delay. But for the biggest delays the two values tend to be equal. We saw before that the main difference between the two delays was their relation with NASDelay. This could indicate that NASDelay is not usually the cause of the delays of several hours.

#### Scatter plot between ActualElapsedTime and DepDelay:

* This twoo variables tend to have a log-normal distribution and if we change the scale of the two axis to logaritmic we can see that there is no relatinship between them.

#### Scatter plot between NASDelay and TaxiOut and TaxiIn:

* In this picture is showed that when TaxiOut is small there are other causes that influence in NASDelay but for big values of TaxiOut this seems to be the principal influence on it. With TaxiIn it happens something similar, but TaxiIn usually has smaller values than TaxiOut and the relation is not so evident.


#### Scatter plot between ArrDelay and NASDelay:

* We can see a linear relationship one to one for big values of NASDelay. It is similar to the relationship between DepDelay and NASDelay but not so clear in this case.


#### Scatter plot between ArrDelay and the sum of NASDelay, CarrierDelay, WeatherDelay, LateAircraftDelay.

* There is a perfect linar relationship.


#### Scatter plot between ArrDelay and the sum of NASDelay, CarrierDelay, WeatherDelay, LateAircraftDelay minus TaxiIn and TaxiOut.

* There is an almost perfect linar relationship. TaxiIn and TaxiOut seems to be included in NASDelay. All the causes include in NASDelay are also included in ArrDelay, but not in DepDelay, because TaxiIn and TaxiOut are not included in DepDelay.

#### Violin plot between Distance(Log scale) and Region:

* Hawaii has two main different nodules. This is logical because they have two different types of traffic. The inner traffic between the islands and the flights to the continent, much more larger. 
* Alaska has a shape elonged and quite uniform. It not exist a clear preference between short and log flights over 200 miles.
* Between the three areas in the continent there are also some differences. The west region has the greater proportion of long flights, maybe influenced by the flights to Hawaii, but it has a clear increment in the first quartile.
* The center and east regions are very simiral, but the East Region has small amount of flights in the upper side. ¿It Could be influenced by the proximity to Puerto Rico? Surealy they are long flights to the west coast.

#### Box plots between ArrDelay, DepDelay, LateAircraftDelay, CarrierDelay NasDelay, WeatherDelay, SecurityDelay, TaxiIn, TaxiOut per Region:

* In these plots is showed that Alaska has the biggest problems in terms of `TotalDelay`, but this problems are caused basicly by the `LateAircraftDelay` and the `SecurityDelay`, although the Security Delays are very small.
* Anyway, despite the cold weather Alaska don't have especial problems with this type of delay. The worst in this case is the East Region maybe the hurricans season is more important in this aspect.
* In all the other causes the East Region and the Center Region seems to have the worst behaviour.
* Te East Region is also the worst in reference to the `NAS Delay`, `TaxiIn` and `TaxiOut` delays. But we saw that there is certain correlation between `TaxiIn` and `TaxiOut` and `NAS Delay`, so it seems logical.
* Hawaii is the region with smaller delays in general.

#### Box plots between ArrDelay, DepDelay, LateAircraftDelay, CarrierDelay NasDelay, WeatherDelay, SecurityDelay, TaxiIn, TaxiOut per DayOfWeek:

* In these graphics, Thursday and Friday, seems to be the days with more delays followed by Mondays and Sundays, but there is not a cause that clearly stand out from others.

#### Box plots between ArrDelay, DepDelay, LateAircraftDelay, CarrierDelay NasDelay, WeatherDelay, SecurityDelay, TaxiIn, TaxiOut per Month:

* In these pictures we can see that the worst month in terms of delays is December. It has the bigger median, quartiles, etc. All the main causes of delay are bigger in this month: the Weather Delay, the Carrier Delay and the NAS Delay.
* The next worst months are June, July, August, Janury and February.
* The best month in terms of delay was April.

### Multivariate analysis:

#### Categorical plot between the percentage of flights by day and month for each region:

* We can conclude that Alaska has a different behavior than the other regions. They travel a lot more in summer than in winter, this may explay why they don't have especial problems with the weather delay. On the     other hand its traffic is almost the same along the week, while in the other regions we found that is bigger Friday and Saturday in Hawaii and smaller the Saturday in the rest.

#### Categorical plot between ArrDelay, DepDelay, LateAircraftDelay, CarrierDelay NasDelay, WeatherDelay, SecurityDelay, TaxiIn, TaxiOut per DayOfWeek for each Region

* Alaska is the region with a greater delay mainly because of the Aircraft Delay. They have also a much bigger Security Delay comparatively with other regions, but this is very small and don't has a great impact in the total. Anyway the difference in the Security delay with other regions is remarkable.

* Hawaii si the region with less delay, but if we focus in the Departure and Arrival Delays we can see a strange pattern. We have seen before that they usually have negative departures and arrival delays, but here we observe tha this are more negative on mondays and then go increasing along the week to remain positive on the weekend. It is strange but probably has a reason. Maybe some policy of the companys that operate there. I don't know.

* In general some delays tend to increase along the week. Except some Monday effect that makes that these day usally have higher delays and the weekend where the delays fall again. We can see this for example in the Carrier Delay. In Hawaii and in Alaska there isn't an effect Monday. In this regions Mondays usually have the lowest or the second lowest delay of the week.

#### Categorical plot between ArrDelay, DepDelay, LateAircraftDelay, CarrierDelay NasDelay, WeatherDelay, SecurityDelay, TaxiIn, TaxiOut per Month for each Region


 * Regarding to the month of the year we can see that the region that have a biggest variation of traffic between months is Alaska. The percentage of traffic is really gigger in the summer months. In the other regions this fifference between months is not so big, although Hawaii has also a considerably increment of traffic in July and August.

 * December is a bad month to travel in all the regions. Janueary, February and March are also bad except in Hawaii.

 * Finally June, July and August are also bad months, expecially in the East Coast and in Alaska. In this region must be very important that they have a great amount of traffic these months. In the case of the East Region all the causes of delay suffer an increment these months but we can remark the increment in the Wheather delays because of the Hurricans Season.

#### Analysis of the Total Delay(sum of LateAircraftDelay, CarrierDelay NasDelay, WeatherDelay and SecurityDelay) vs the direction of the flight:

* It seems that the total delay is bigger if we travel to the West than if we travel to the East. This difference does not exists in the North and South directions. 

#### Analysis of the routes with more than 15 flights per day and with a mean speed slower than 250 km/h.

We have found for the year 2008 96 routes describing three possible paths:

* One of this options could be a line from San Francisco to Los Angeles and Phoenix. 
* Other option could be from Boston to New York, Atlanta and Miami.
* And to link the both coast we could make a corridor beteen the New York area, Chicago, Denver and Los Angeles.



## Key Insights for Presentation

* In the presentation we are interested in the different behaviour of the delays in funciton of the of the region. We have analized these differences along the days of the week and the months.

* We also want to emphasize the different delays between the flights to the West and the flights to the East. And that there is no remarkable differences between the Norrth and the South.

* We are going to end showing the results for the routes with more than 15 flights and with mean speed slower than 250 km/h.