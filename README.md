select 
arrival_date_year,
hotel,
round(sum((stays_in_week_nights+stays_in_weekend_nights)*adr),2) as Revenue 
from Hotels
group by arrival_date_year,hotel

with Hotels as (
Select * from dbo.[2018]
Union
Select * from dbo.[2019]
Union
Select * from dbo.[2020])


Select * from Hotels
left join dbo.market_segment$
on Hotels.market_segment = market_segment$.market_segment
left join
dbo.meal_cost$
on meal_cost$.meal = Hotels.meal
