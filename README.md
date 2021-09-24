# sql

select decimal_place_precision ,REPLACE(decimal_place_precision,'\' ,'' )   from  ebr_currentweight_entity  where ebr_currentweight_entity.decimal_place_precision  is not null  and strpos(decimal_place_precision,'\')>0

update ebr_currentweight_entity set decimal_place_precision =REPLACE(decimal_place_precision,'\' ,'' )
where ebr_currentweight_entity.decimal_place_precision  is not null  and strpos(decimal_place_precision,'\')>0
