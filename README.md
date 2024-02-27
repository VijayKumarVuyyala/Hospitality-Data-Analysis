# Hospitality-Data-Analysis

# Atliq-hospitality-power-bi-dashboard
Welcome to the AtliQ Grands Revenue Insights project ! In this project, I have implemented data analytics using Power BI to empower AtliQ Grands with the ability to make data-driven decisions, surpass competitors in the market, and drive growth in various aspects like Market Share & Revenue.

# Live Dashboard Link
 https://lnkd.in/gkUA7CpA

# Business problem
AtliQ Grands is the proud owner of numerous opulent hotels throughout India. Yet, AtliQ Grands finds itself experiencing a decline in both market share and revenue within the luxurious/business hotel sector. I, as a data analyst, figure out the key problem of declining revenue using data analytics.

# Key Performance Metrics:
1. Realization Percentage: — Calculate the percentage of actual revenue compared to the potential revenue.

2. Occupancy Percentage: — Analyze the percentage of occupied rooms to the total available rooms.

3. Average Daily Revenue: —Determine the average revenue earned per day.

4. Daily Booked Rooms per Night: Track the number of rooms booked daily.

5. Average Rating: — Evaluate the average hotel customer rating.

# Data modeling:

Data modeling plays a pivotal role and serves as the foundation for generating meaningful reports. The entire framework of visualizations is constructed upon a well-designed data model. Neglecting proper data modeling can have adverse effects on the overall performance of the generated reports.
In the context of this project, we have meticulously followed the Snowflake data modeling method. This approach involves structuring data into normalized forms, resulting in reduced redundancy and improved query performance. This methodology enhances the way we organize and process data, ensuring optimal results for our analysis.
![3](https://github.com/VijayKumarVuyyala/Hospitality-Data-Analysis/assets/160216489/8e6d32c6-1161-42d6-9c3a-3d2cdc96b822)

# Creating calculated measures:

ADR Calculate the ADR (Average Daily rate). It is the ratio of revenue to the total rooms booked/sold. It is the measure of the average paid for rooms sold in a given time period.
ADR = DIVIDE( [Revenue], [Total Bookings],0)

Realization % calculates the realization percentage. It is nothing but the successful “checked out” percentage of overall bookings happened.
Realisation % = 1- ([Cancellation %]+[No Show rate %])


RevPAR Calculate the RevPAR (Revenue Per Available Room) RevPAR represents the revenue generated per available room, whether or not they are occupied. RevPAR helps hotels measure their revenue-generating performance to accurately price rooms. RevPAR can help hotels measure themselves against other properties or brands.
RevPAR = DIVIDE([Revenue],[Total Capacity])

DBRN calculates DBRN (Daily Booked Room Nights). This metric tells on average how many rooms are booked for a day considering a time period.
DBRN = DIVIDE([Total Bookings], [No of days])

DSRN calculates DSRN (Daily Sellable Room Nights). This metric tells on average how many rooms are ready to sell for a day considering a time period.
DSRN = DIVIDE([Total Capacity], [No of days])

DURN calculate DURN (Daily Utilized Room Nights). This metric tells on average how many rooms are successfully utilized by customers for a day considering a time period.
DURN = DIVIDE([Total Checked Out],[No of days])

Revenue WoW change % indicates revenue change percentage week over week.
Revenue WoW change % = 
        Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
        var revcw = CALCULATE([Revenue],dim_date[wn]= selv)
        var revpw = CALCULATE([Revenue],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
        
        return
        DIVIDE(revcw,revpw,0)-1

Occupancy WoW change % indicates occupancy change percentage week over week.
Occupancy WoW change % = 
        Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
        var revcw = CALCULATE([Occupancy %],dim_date[wn]= selv)
        var revpw = CALCULATE([Occupancy %],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
        
 return
        DIVIDE(revcw,revpw,0)-1

ADR WoW change % helps to find the ADR (Average Daily rate) change percentage week over week.
ADR WoW change % = 
        Var selv = IF(HASONEFILTER(dim_date[wn]),SELECTEDVALUE(dim_date[wn]),MAX(dim_date[wn]))
        var revcw = CALCULATE([ADR],dim_date[wn]= selv)
        var revpw = CALCULATE([ADR],FILTER(ALL(dim_date),dim_date[wn]= selv-1))
        
        return
        DIVIDE(revcw,revpw,0)-1

Cancellation % calculating the cancellation percentage.
Cancellation % = DIVIDE([Total cancelled bookings],[Total Bookings])

# Power-bi-dashboard
![1](https://github.com/VijayKumarVuyyala/Hospitality-Data-Analysis/assets/160216489/23e7139f-fc77-4737-b803-b837a7a562de)
![2](https://github.com/VijayKumarVuyyala/Hospitality-Data-Analysis/assets/160216489/e1575409-cdf1-4f41-a04d-3a3ba7c4fafa)

#Key Findings from this dashboard:
The dashboard was utilized in an attempt to observe all the significant key metrics every week. The metrics of Realisation, ADR, and RevPar remained constant, with only a slight fluctuation in occupancy ranging from 50% to 60% when filtering the data according to the week. Throughout the entirety of the period, both occupancy and cancellation rates remained close to the benchmark set by the industry.
Furthermore, Realisation, ADR, and RevPar also sustained a similar consistency when comparing weekdays to weekends.

# Insights and suggestions:
       # ADR Remains Stable
Upon analyzing the dashboard, it’s evident that the Average Daily Rate (ADR) for AtliQ Hotels has remained relatively stable over the given time frame. This stability in pricing indicates a consistent pricing strategy.
Notably, AtliQ Hotels currently do not employ dynamic pricing based on weekdays and weekends. This presents an opportunity to consider adjusting the pricing strategy. Dynamic pricing can help optimize revenue by offering different rates for weekdays and weekends, aligning pricing more closely with demand fluctuations.
This insight suggests that exploring dynamic pricing strategies could be a valuable initiative to consider, potentially leading to increased revenue and better revenue management.

     # Overall Occupancy Rate
The overall occupancy rate for AtliQ Grands’ properties currently stands at a solid 57%. This figure reflects the percentage of available rooms that are being utilized by guests. A 57% occupancy rate indicates a substantial portion of rooms are booked, contributing positively to revenue.
Maintaining a healthy occupancy rate is crucial for optimizing revenue and resource management. This insight suggests that AtliQ Grands has been successful in attracting guests and efficiently filling available rooms.
As part of ongoing strategies, it may be worthwhile to explore avenues to further increase occupancy, especially during off-peak periods, to maximize revenue potential.
Overall, the 57% occupancy rate provides a foundational understanding of AtliQ Grands’ performance and can serve as a basis for further revenue optimization efforts.

     # Average Rating
The average guest rating for AtliQ Grands’ properties is a commendable 3.62. This rating, derived from guest reviews and surveys, reflects the overall satisfaction of guests who have experienced our hospitality.
A rating of 3.62 signifies a positive guest experience, with the majority of guests expressing satisfaction with their stays. Guest ratings are a vital indicator of our service quality and the guest experience we provide.
As we continue to prioritize guest satisfaction, it’s important to maintain and improve upon this rating. By consistently delivering exceptional service, addressing guest feedback, and enhancing guest experiences, we can aim for even higher ratings in the future.
The 3.62 average rating underscores our commitment to offering outstanding hospitality and ensuring our guests have memorable stays.

# Suggestions:

Suggested, ways to raise revenue is to enhance occupancy rates.

Take advantage of late bookings and additional days of stay to increase revenue.

Maintain Occupancy Percentage is maximum on Weekends

Maximum bookings are done through others and makeyourtrip platform must focus on platforms from where people prefer fewer bookings.

Average rating is between 3.65 and 3.6 so try to pull the reasons from the hotels where hotel ratings are very low and fix them ASAP to generate more engagement.

Mumbai is showing a high average rating but those cities have ratings below 3 so fix them by understanding the reasons behind low ratings.

Fixed the issue highlighted by the customer in low-rated hotels to Increase occupancy rate.

Dynamic pricing strategy Offering coupons and cashback incentives directly to customers who book rooms through the hotel’s website or offline at checkout thus increasing realization.

# Tools used
1. POWER BI

2. DAX

