# Team 6 Mist 4610 Group Project 2 

## Team Name: 
71552 Group 6 

## Team Members:

1. Jesse Williams: [@jesnw](https://github.com/jeswn)
2. Tania Saputera: [@tas45087](https://github.com/tas45087)
3. Kate Nelms: [@ksn56497](https://github.com/ksn56497)
4. John Omolon: [@JohnOmolon](https://github.com/JohnOmolon)
5. Johan Jerry: [@johanjerry](https://github.com/johanjerry)

## Dataset Description

### Our Dataset and Why:
The dataset our team selected is from the U.S. Department of Transportation, which provides information on non-stop domestic flight segments such as departures and scheduled flights. Our team selected this dataset because it allows us identify major travel hubs in the USA by analyzing flight patterns, and evaluate differences between scheduled and actual flight activity. With this data we can make an meaningful impact on USA airports operationally, economicly, and socially by understanding travel demand and efficiency across regions in the USA.

### Description:
The dataset is provided by the U.S. Department of Transportation and is available through the Snowflake Data Marketplace under the listing US Department of Transportation Data. It contains information on U.S. domestic flight operations.

The dataset consists of seven main tables: Aircraft Carrier Index, Aircraft Index, Airport Index, USDOT Attributes, USDOT Attributes Point-in-Time History, USDOT Timeseries, and USDOT Timeseries Point-in-Time History. The Timeseries tables contain millions of records, capturing flight activity over time.

Key columns include DATE (date, data type: DATE), ORIGIN_AIRPORT_ID (airport identifier, data type: INTEGER), VARIABLE (metric type such as departures scheduled or performed, data type: STRING), and VALUE (numeric measurement, data type: NUMBER). 

### Two Analytical Questions:
How do seasonal changes affect flight reliability in the U.S., based on the difference between scheduled departures, actual departures, cancellations, and extra flights?
This question uses columns such as DATE, VARIABLE, and VALUE, along with ORIGIN_AIRPORT_ID for joining purposes. The DATE column uses a datetime function to group data into seasons, while VARIABLE and VALUE are used to calculate total scheduled and actual departures. This query is non-trivial because it applies datetime transformations, conditional aggregation with CASE WHEN statements, and adds measures such as cancellations and extra flights within a single query. It is meaningful operationally because it helps airlines understand seasonal disruptions to improve scheduling and traffic, economically because it shows periods of inefficiency and potential revenue loss, and socially because it provides insight into the reliability of air travel across different times of the year. 

Which airports exceed the average number of departing flights and serve as primary travel hubs in the U.S.?

This question uses columns such as ORIGIN_AIRPORT_ID, AIRPORT_NAME, VARIABLE, and VALUE. The VARIABLE column is used to filter for departures, while VALUE is aggregated to calculate total flights per airport, and the join with the airport table provides readable airport names. This query is non-trivial because it combines aggregation, grouping, a subquery to calculate the average number of departures, and a HAVING clause to filter results above that average. It is meaningful operationally because it identifies major hubs where airlines allocate resources efficiently, economically because it reveals where travel demand and revenue are highest, and socially because it shows how air travel connectivity is distributed across regions in the United States. 


## Questions and Justification
###Query 1:

Question:
How do seasonal changes affect flight reliability in the U.S., based on the difference between scheduled departures, actual departures, cancellations, and extra flights? 

Justification:
This query analyzes how flight activity differs across the seasons (Winter, Spring, Summer, Fall) by comparing the total scheduled flights to actual flights flown, while calculating cancellations and extra flights. Operationally, it is meaningful because it helps airlines and airports understand how patterns change with the seasons to improve scheduling accuracy and better prepare for disruptions such as weather delays and holidays. Economically, it identifies periods of high and low efficiency, showing when airlines may lose revenue due to cancellations or gain revenue from increased demand during peak seasons. Socially, our query displays how reliable air travel is throughout the year (especially during busy travel seasons like holidays) and potential impacts for a passengers ability to travel. The query uses the US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES table (including DATE, VARIABLE, VALUE, and ORIGIN_AIRPORT_ID) and the AIRPORT_INDEX table (AIRPORT_ID). 
