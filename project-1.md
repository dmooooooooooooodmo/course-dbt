# project 1 answers

How many users do we have?
answer: 130

,,,
select count(*) from dev_db.dbt_connerdemomecom.stg_postgres__users
,,,

On average, how many orders do we receive per hour?
answer: 7.52 

,,,
select avg(order_count) as avg_order_per_hour
from (
    select count (order_id) as order_count
    from dev_db.dbt_connerdemomecom.stg_postgres__orders
    group by date_trunc('hour',created_at)
) AS avg_hourly_order;
,,,,


On average, how long does an order take from being placed to being delivered?
answer: 3.89 days

,,,
select avg(datediff(day, created_at, delivered_at)) AS avg_time_in_days
from dev_db.dbt_connerdemomecom.stg_postgres__orders
where delivered_at is not null
,,,


How many users have only made one purchase? Two purchases? Three+ purchases?
answer: 1 purchase = 25, 2 purchases = 28, 3+ purchases = 71

,,,
select
    case 
        when order_count = 1 then '1 purchase'
        when order_count = 2 then '2 purchases'
        else '3+ purchases'
    end as purchase_category,
    count(*) as user_count
from (
    select user_id, count(order_id) as order_count
    from dev_db.dbt_connerdemomecom.stg_postgres__orders
    group by user_id
) as user_orders
group by purchase_category
,,,

Note: you should consider a purchase to be a single order. In other words, if a user places one order for 3 products, they are considered to have made 1 purchase.

On average, how many unique sessions do we have per hour?
answer: 16.33
,,,
select avg(session_count) as avg_sessions_per_hour
from (
    select count(distinct session_id) as session_count
    from dev_db.dbt_connerdemomecom.stg_postgres__events
    group by date_trunc('hour', created_at)
) as hourly_sessions
,,,