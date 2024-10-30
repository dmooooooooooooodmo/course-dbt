# project 2 answers

Which products had their inventory change from week 1 to week 2? 
        4cda01b9-62e2-46c5-830f-b7f262a58fb1
        55c6a062-5f4a-4a8b-a8e5-05ea5e6715a3
        be49171b-9f72-4fc9-bf7a-9a52e259836b
        fb0e8be7-5ac4-4a76-a1fa-2cc4bf0b2d80

,,,
select * from dev_db.dbt_connerdemomecom.products_snapshot
where dbt_valid_to is not null;

,,,,
