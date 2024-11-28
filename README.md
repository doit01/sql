删除重复deleteduplicates
delete
-- select id, quote_version_id,part_id, parent_id,activity_name_en
FROM oq_prod.oq_execution_quote_summary_activityhttps://github.com/doit01/sql/blob/main/README.md
WHERE ctid IN (
  SELECT ctid
  FROM (
    SELECT ctid, ROW_NUMBER() OVER (PARTITION BY quote_version_id,part_id, parent_id,activity_name_en ORDER BY (SELECT NULL)) AS rn
    FROM oq_prod.oq_execution_quote_summary_activity where parent_id  is not null
  ) sub
  WHERE rn > 1
);
# sql

select decimal_place_precision ,REPLACE(decimal_place_precision,'\' ,'' )   from  ebr_currentweight_entity  where ebr_currentweight_entity.decimal_place_precision  is not null  and strpos(decimal_place_precision,'\')>0

update ebr_currentweight_entity set decimal_place_precision =REPLACE(decimal_place_precision,'\' ,'' )
where ebr_currentweight_entity.decimal_place_precision  is not null  and strpos(decimal_place_precision,'\')>0

   create table t(id int,name varchar(20),class int,score int);
   
  insert into t values(1,'math',1,90);

insert into t values(2,'math',2,80);

insert into t values(3,'math',1,70);

insert into t values(4,'chinese',2,60);

insert into t values(5,'chinese',1,50);

insert into t values(6,'chinese',2,60);

insert into t values(7,'physical',1,70);

insert into t values(8,'physical',2,80);

insert into t values(9,'physical',1,90);


select name,class,sum(score) from t group by grouping sets((name),(class),()) order by name,class
select name,class,sum(score) from t group by grouping sets((name,class)) order by name,class
cube((a),(b),(c))等价于grouping sets((a,b,c),(a,b),(a,c),(a),(b,c),(b),(c),()) *

select name,class,sum(score)  from t group by cube((name),(class)) order by name,class

select coalesce(name,'total') as name,

 coalesce(class,0) as class,

 coalesce(sum(score),0) as sum_score,

 coalesce(round(avg(score),2),0) as avg_score

 from t

 group by grouping sets((name,class),())

 order by name,class
