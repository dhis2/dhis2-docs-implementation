# Data Elements

## Data elements should be in a data element group

All data elements should be in a data element group. This allows users to find the data elements more easily in analysis apps and also contributes to having more complete data element group sets. Maintenance operations can also be made more efficient by applying bulk settings (ie. sharing) to all data elements within a data element group.

### Recommendation

Data elements that are not in a data element group should be added to a relevant data element group. If the data elements are not needed, they should be deleted.

### Diagnosing if the problem exists

Data elements that are not in a data element group can be found by running the data integrity check. You can also use the following queries to obtain summaries of these data elements.

#### SQL - Identification

You can identify the number of **AGGREGATE** data elements that are not within a data element group using the following query:
```
select 'aggregate_dataelement_nongrouped', count(*)::varchar, (100*count(*)/(select count(*) from dataelement))::varchar || '%', 'Aggregate data elements not in any data element groups.' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from dataelementgroupmembers)
```

You can identify the number of **TRACKER** data elements that are not within a data element group using the following query:
```
select 'tracker_dataelement_nongrouped', count(*)::varchar, (100*count(*)/(select count(*) from dataelement))::varchar || '%', 'Tracker data elements not in any data element groups.' from dataelement where domaintype != 'AGGREGATE' and dataelementid not in (select dataelementid from dataelementgroupmembers)
```

#### SQL - Listing

You can list the **AGGREGATE** data elements not in a data element group using the following query
```
select 'Data elements (aggregate) not in any data element groups.';
select name,uid from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from dataelementgroupmembers);
```

You can list the **TRACKER** data elements not in a data element group using the following query
```
select 'Data elements (tracker) not in any data element groups.';
select name,uid from dataelement where domaintype != 'AGGREGATE' and dataelementid not in (select dataelementid from dataelementgroupmembers);
```

## Data elements should have data values

All data elements in a production database should have data values associated with them. If there are data elements that have been in the system for some time and do not have any data values associated with them, they are serving no purpose in the system.

### Recommendation

Data elements that do not have any data values should be deleted.

### Diagnosing if the problem exists

We can review if data elements have any data values using different sets of criteria. This will allow you to determine in more detail if data elements need to be deleted or can be kept. The criteria we are currently summarizing for **AGGREGATE** data elements includes:

- "Abandoned" data elements. These are data elements that have not been updated in at least 100 days and do not have any data values associated with them.
- Data elements with no values in the last 3 periods based on the data set period type associated with those data elements
- Data elements with no values at all

#### SQL - Identification

We can summarize these results together for **AGGREGATE** data elements using the following query:

```
with ds_period as (select datasetid, dataelementid, periodid from dataset ds left join period pe using(periodtypeid) left join datasetelement using(datasetid) where date_part('day', now() - pe.enddate::timestamp)::int <= 3*date_part('day', pe.enddate::timestamp - pe.startdate::timestamp)::int)

select 'aggregate_dataelement_abandoned',count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements that have not been changed in last 100 days and do not have any data values' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from datavalue group by dataelementid) and date_part('day', now() - lastupdated::date) > 100

union all

select 'aggregate_dataelement_nonewdata', count(*)::varchar, (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE' ))::varchar || '%', 'Aggregate data elements with no data values in the last 3 periods (based on data set period type).' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select distinct dataelementid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by dataelementid)

union all

select 'aggregate_dataelement_nodata', count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements with NO data values' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from datavalue group by dataelementid);
```