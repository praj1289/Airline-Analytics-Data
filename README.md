

# Airlines Challenge

## Problem Statement

You are working for an airline company looking to enter the United States domestic market. Specifically, the company has decided to start with 5 round trip routes between medium and large US airports. An example of a round trip route is the combination of JFK to ORD and ORD to JFK. The airline company has to acquire 5 new airplanes (one per round trip route) and the upfront cost for each airplane is $90 million. The company’s motto is “On time, for you”, so punctuality is a big part of its brand image. 

You have been tasked with analyzing 1Q2019 data to identify:
 1. The 10 busiest round trip routes in terms of number of round trip flights in the quarter. Exclude canceled flights when performing the calculation.
 2. The 10 most profitable round trip routes (without considering the upfront airplane cost) in the quarter. Along with the profit, show total revenue, total cost, summary values of other key components and total round trip flights in the quarter for the top 10 most profitable routes. Exclude canceled flights from these calculations.
 3. The 5 round trip routes that you recommend to invest in based on any factors that you choose.
 4. The number of round trip flights it will take to breakeven on the upfront airplane cost for each of the 5 round trip routes that you recommend. Print key summary components for these routes.
 5. Key Performance Indicators (KPI’s) that you recommend tracking in the future to measure the success of the round trip routes that you recommend.

## Input Dataset

- Flights
- Tickets
- Airport Codes

## Assumptions

- Each airplane is dedicated to one round trip route between the 2 airports.
- Costs:
  - Fuel, Oil, Maintenance, Crew- $8 per mile total
  - Depreciation, Insurance, Other- $1.18 per mile total
  - Airport operational costs for the right to use the airports and related services are fixed at $5,000 for medium airports and $10,000 for large airports. There is one charge for each airport where a flight lands. Thus, a round trip flight has a total of two airport charges.
  - For each individual departure, the first 15 minutes of delays are free, otherwise each minute costs the airline $75 in added operational costs.
  - For each individual arrival, the first 15 minutes of delays are free, otherwise each minute costs the airline $75 in added operational costs.
- Revenue:
  - Each plane can accommodate up to 200 passengers and each flight has an associated occupancy rate provided in the Flights data set. Do not use the Tickets data set to determine occupancy.
  - Baggage fee is $35 for each checked bag per flight. We expect 50% of passengers to check an average of 1 bag per flight. The fee is charged separately for each leg of a round trip flight, thus 50% of passengers will be charged a total of $70 in baggage fees for a round trip flight.
  - Disregard seasonal effects on ticket prices (i.e. ticket prices are the same in April as they are on Memorial Day or in December)

## Steps Followed:

### 1. Quality Check

- Issues encountered:
  - Missing data - Missing data issue was addressed by imputing with the mean wherever needed. This helped keep the dataset's integrity without introducing bias. 
  - Outliers - Outliers where the z-score was 3 or more were removed from the tickets dataset. This reduced the impact of our findings while suggesting recommendations.
  - Memory constraints - Reduced the variable size to 32-bit instead of the default 64-bit to preserve memory as well as faster execution without compromising accuracy.
  - Incorrect datatypes - Addressed by updating the variable type.
  - Duplicate data

### 2. Data Munging

- Created reusable code to perform following functions:
  - Inner join 2 tables
  - Read CSV files
  - Update datatype - To change type from 64-bit to 32-bit
  - Impute with mean - Update null values with mean
  - Create boxplot - To create a boxplot to check for outliers
- Assumption:
  - ITIN_FARE column contains single person fare and not the total fare for all passengers
    
### 3. Visual Narrative

- Top 10 busiest routes based on the number of round trips

  LAX - SFO is the busiest with 4164 rount trips, LGA - ORD comes second with 3576, LAS - LAX comes third with 3254
  
![Image](https://github.com/user-attachments/assets/8fcfdbb2-97cd-4d34-84bf-3f3711b762ba)

- Top 10 most profitable routes in the quarter
  
  JFK - LAX is the most profitable route with net profit of $263m, ATL - LGA comes second with $164m, DCA - ORD comes third with $163m
  
![Image](https://github.com/user-attachments/assets/9132b39a-7e91-4ad8-b3cb-a9f4222f91c8)

- Top 5 round trip routes that I recommend

  This is based on the average profit per trip based on the analysis performed.

![Image](https://github.com/user-attachments/assets/df6ec55a-4b3e-489f-a241-ef999d1e9069)

- Number of round trip flights it will take to breakeven for the 5 recommended trip routes (cost of plane $90m)
  
  - MDT - PHL: 856
  - ADK - ANC: 972
  - DEN - SUN: 983
  - EGE - JFK: 992
  - DEN - MOT: 1078
 
![Image](https://github.com/user-attachments/assets/157f26df-c24e-49d7-a078-2151ff177435)

### 4. Final Recommendation

The criteria for the final recommendation is the average profit per flight based on the provided data. 

#### Recommendations for the top 5 round trips:
  - MDT - PHL: Harrisburg, PA - Philadelphia, PA
  - ADK - ANC: Adak, AK - Anchorage, AK
  - DEN - SUN: Denver, CO - Friedman, ID
  - EGE - JFK: Eagle County, CO - New York, NY
  - DEN - MOT: Denver, CO - Minot, ND

 #### Common trend identified for these recommendations:
 - The routes might have little competition, providing a chance to capture the market demand.
 - Affluent travelers in these areas are likely willing to pay a premium for convenience.
 - The cities are hubs for economic activity and tourism, ensuring steady passenger volumes.
 - Cities like New York, Denver and Philadelphia provide access to a larger network of connections for both domestic and international travel passengers.

#### Points to consider for individual routes:
- MDT - PHL might cater to regional travelers needing quick access to a big city like Philadelphia for connecting international or long-haul flights.
- Alaska is known for natural beauty and outdoor activities. Anchorage attracts tourists and Adak hosts military installations, which may ensure consistent demand from government personnel.
- Denver is also a central location so might attract tourists and travelers who have connecting flights to other cities.

#### Points to track to measure success:
  - Passenger demand & occupancy rate - seasonal trends might lead to fluctuations (e.g. aurora viewing during winters in Alaska, ski season in Denver).
  - On time performance - the company prides itself for being on time, so this is one of the most critical parameters.
  - Customer feedback
  - Revenue per passenger
  - Competitor activity - track new routes from competitors to stay ahead of the competition
  - Cancellation Rate per Route
 
### 5. What's Next
Invest in better decision making process enablers that can build forecasting models to optimize the current process as well as help build any future processes. This would lead to better market adoption and penetration. 
