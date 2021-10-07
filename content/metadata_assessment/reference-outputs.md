# Charts, Tables, Maps

## Charts should be viewed routinely

The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as any pre-defined period of your choosing.

### Recommendation

If a chart has been viewed 1 time or less within your definition of routine, it should be deleted.

### Diagnosing if the problem exists

#### SQL - Identification

To identify how many charts have not been viewed routinely, you can use the following query via SQL.

```
select 'chart_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of charts' as description from chart

union all

select 'chart_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart))||'%', 'Charts that have been viewed 1 time or less from 2020 onward' as description from chart where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2020 group by favoriteuid having count(*) >1)

union all 

select 'chart_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart))||'%', 'Charts that have not been opened in the last 12 months' as description from chart where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'chart_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart))||'%', 'Charts that are publicly viewable' as description from chart where publicaccess like 'r%'

union all

select 'chart_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart where publicaccess like 'r%'))||'%', 'Public charts that have been viewed 1 time or less from 2020 onward' as description from chart where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2020 group by favoriteuid having count(*) >1)

union all

select 'chart_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart where publicaccess like 'r%'))||'%', 'Public charts that have not been opened in the last 12 months' as description from chart where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);
```

### Fixing these problems via deletion

## Tables should be viewed routinely

The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as any pre-defined period of your choosing.

### Recommendation

If a table has been viewed 1 time or less within your definition of routine, it should be deleted.

### Diagnosing if the problem exists

#### SQL - Identification

To identify how many tables have not been viewed routinely, you can use the following query via SQL.

```
select 'reporttable_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of report tables' as description from reporttable

union all

select 'reporttable_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable))||'%', 'Pivot tables that have been viewed 1 time or less from 2020 onward' as description from reporttable where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2020 group by favoriteuid having count(*) >1)

union all 

select 'reporttable_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable))||'%', 'Pivot tables that have not been opened in the last 12 months' as description from reporttable where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'reporttable_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable))||'%', 'Pivot tables that are publicly viewable' as description from reporttable where publicaccess like 'r%'

union all

select 'reporttable_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable where publicaccess like 'r%'))||'%', 'Public pivot tables that have been viewed 1 time or from 2020 onward' as description from reporttable where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2020 group by favoriteuid having count(*) >1)

union all

select 'reporttable_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable where publicaccess like 'r%'))||'%', 'Public pivot tables that have not been opened in the last 12 months' as description from reporttable where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);
```

#### SQL - Listing

### Fixing these problems via deletion

## Maps should be viewed routinely

The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as any pre-defined period of your choosing.

### Recommendation

If a map has been viewed 1 time or less within your definition of routine, it should be deleted.

### Diagnosing if the problem exists

#### SQL - Identification

To identify how many maps have not been viewed routinely, you can use the following query via SQL.

```
select 'map_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of maps' as description from map

union all

select 'map_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map))||'%', 'maps that have viewed 1 time or less from 2020 onward' as description from map where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2020 group by favoriteuid having count(*) >1)

union all 

select 'map_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map))||'%', 'maps that have not been opened in the last 12 months' as description from map where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'map_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map))||'%', 'maps that are publicly viewable' as description from map where publicaccess like 'r%'

union all

select 'map_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map where publicaccess like 'r%'))||'%', 'Public maps that have been viewed 1 time or less from 2020 onward' as description from map where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2020 group by favoriteuid having count(*) >1)

union all

select 'map_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map where publicaccess like 'r%'))||'%', 'Public maps that have not been opened in the last 12 months' as description from map where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);
```

#### SQL - Listing

### Fixing these problems via deletion

## Summary

You can run a summary query in order to generate summary statistics on all of these items at once. Use the following query to retrieve a summary output:

```
-- CHARTS
select 'chart_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of charts' as description from chart

union all

select 'chart_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart))||'%', 'Charts that have been viewed 1 time or less after 2017' as description from chart where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all 

select 'chart_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart))||'%', 'Charts that have not been opened in the last 12 months' as description from chart where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'chart_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart))||'%', 'Charts that are publicly viewable' as description from chart where publicaccess like 'r%'

union all

select 'chart_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart where publicaccess like 'r%'))||'%', 'Public charts that have been viewed 1 time or less after 2017' as description from chart where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all

select 'chart_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from chart where publicaccess like 'r%'))||'%', 'Public charts that have not been opened in the last 12 months' as description from chart where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'CHART_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);



-- REPORT TABLES
select 'reporttable_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of report tables' as description from reporttable

union all

select 'reporttable_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable))||'%', 'Pivot tables that have been viewed 1 time or less after 2017' as description from reporttable where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all 

select 'reporttable_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable))||'%', 'Pivot tables that have not been opened in the last 12 months' as description from reporttable where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'reporttable_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable))||'%', 'Pivot tables that are publicly viewable' as description from reporttable where publicaccess like 'r%'

union all

select 'reporttable_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable where publicaccess like 'r%'))||'%', 'Public pivot tables that have been viewed 1 time or less after 2017' as description from reporttable where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all

select 'reporttable_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from reporttable where publicaccess like 'r%'))||'%', 'Public pivot tables that have not been opened in the last 12 months' as description from reporttable where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'REPORT_TABLE_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);



-- MAP
select 'map_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of maps' as description from map

union all

select 'map_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map))||'%', 'maps that have viewed 1 time or less after 2017' as description from map where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all 

select 'map_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map))||'%', 'maps that have not been opened in the last 12 months' as description from map where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'map_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map))||'%', 'maps that are publicly viewable' as description from map where publicaccess like 'r%'

union all

select 'map_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map where publicaccess like 'r%'))||'%', 'Public maps that have been viewed 1 time or less after 2017' as description from map where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all

select 'map_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from map where publicaccess like 'r%'))||'%', 'Public maps that have not been opened in the last 12 months' as description from map where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'MAP_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);
```