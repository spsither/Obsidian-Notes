# Task
- Identify all the records in Staff DB where GB number can not be found in the Master DB
```
select s.*
from staffs s
left join tblgreenbook t
on t.sGBID = s.sGBID
where t.id is null
and s.sGBID is not null;
```
An example of such sGBID data is [[List of faulty gbNo in staff db]]
- Delete all such records 
```
create table term_hierarchy_backup (tid bigint unsigned);

insert into term_hierarchy_backup

select DISTINCT(s.id)
from staffs as s
left join tblgreenbook as t
on t.sGBID = s.sGBID
where t.id is null;

DELETE FROM staffs AS th
WHERE th.id IN (select tid from term_hierarchy_backup);
```
- Conform by checkin the following left join
```
select count(*)
from staffs s
left join tblgreenbook t
on t.sGBID = s.sGBID
where t.id is null;
```

