# project 4 answers

part 1

2. Which products had their inventory change from week 3 to week 4?

answer:
be49171b-9f72-4fc9-bf7a-9a52e259836b
b66a7143-c18a-43bb-b5dc-06bb5d1d3160
689fb64e-a4a2-45c5-b9f2-480c2155624d
55c6a062-5f4a-4a8b-a8e5-05ea5e6715a3
fb0e8be7-5ac4-4a76-a1fa-2cc4bf0b2d80
4cda01b9-62e2-46c5-830f-b7f262a58fb1

,,,

select product_id, count(1)
from dev_db.dbt_connerdemomecom.products_snapshot
group by 1
having count(1)>1

,,,,

3. can you use the inventory changes to determine which products had the most fluctuations in inventory?

4cda01b9-62e2-46c5-830f-b7f262a58fb1	Pothos
55c6a062-5f4a-4a8b-a8e5-05ea5e6715a3	Philodendron
689fb64e-a4a2-45c5-b9f2-480c2155624d	Bamboo
b66a7143-c18a-43bb-b5dc-06bb5d1d3160	ZZ Plant
be49171b-9f72-4fc9-bf7a-9a52e259836b	Monstera
fb0e8be7-5ac4-4a76-a1fa-2cc4bf0b2d80	String of pearls

 Did we have any items go out of stock in the last 3 weeks? 

 No, there were no inventories of 0 in my snapshot

part 2

1. 81% make it to add to cart, 77% make it to checkout

,,,


select 
    count(distinct case when page_views > 0 then session_id end) as page_views,
    count(distinct case when add_to_carts > 0 then session_id end) as add_to_carts,
    count(distinct case when checkouts > 0 then session_id end) as checkouts
from dev_db.dbt_connerdemomecom.fact_page_views

,,,

2. add_to_cart to checkout has the biggest dropoff of only 77.30% conversion



part 3

if you are thinking about moving to analytics engineering, what skills have you picked that give you the most confidence in pursuing this next step?

Well, as I am an employee of Sigma, I can testify that Jake has made our dbt environment quite ~robust~. In that context, taking this course solves a bit of a different problem for me, as I am not learning dbt to implement it in my workspace. Rather, this course has made me literate in dbt, where I can actually understand, read, and contribute to the robust dbt environment that I very luckily already exist within. Realizing that dbt isn't as intimidating as my initial reaction and exposure to it had me feel has been very empowering in my role. Can't wait to use all these new skills to start building some of my own models, rather than just using existing ones or updating/adding to exisiting ones!
