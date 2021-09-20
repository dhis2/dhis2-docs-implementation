# Data sets

## Data sets should have data

All **active** datasets should have data values associated with them. Active data sets are data sets which should be currently used (within the last 3 reporting periods) to collect data. 

### Recommendation

- If a data set is not being updated with new data or no new data values are being entered within the last 3 periods (relative to the period type assigned to the dataset) against the dataset **but** there are data values from previous periods the data set should be archived (ie. assign it a prefix)
- If a data set has no new or previous data values within the last 3 periods (relative to the period type assigned to the dataset) and will not be used to collect data, the data set should be removed.

### Diagnosing if the problem exists

#### SQL - Identification

You can use the following query in order to generate a summary of the number of data sets that: 

 1. Do not have any **updated** data values within the last 3 periods (relative to the period type assigned to the dataset)
 2. Do not have any **new** data values within the last 3 periods (relative to the period type assigned to the dataset)

```
with ds_lastupdate as (select datasetid, avg(date_part('day', pe.enddate::timestamp - pe.startdate::timestamp))::int as interval from dataset ds left join period pe using(periodtypeid) group by datasetid), 
ds_period as (select datasetid, dataelementid, periodid from dataset ds left join period pe using(periodtypeid) left join datasetelement using(datasetid) where date_part('day', now() - pe.enddate::timestamp)::int <= 3*date_part('day', pe.enddate::timestamp - pe.startdate::timestamp)::int)

select 'dataset_count' as indicator, count(*)::varchar as value,'100%' as percent, 'Total number of data sets' as description from dataset

union all

select 'dataset_noupdateddata', count(*)::varchar, (100*count(*)/(select count(*) from dataset))::varchar || '%', 'Data sets with no data values with lastupdated date within the last 3 periods (based on data set period type). Note: this is not taking into account the reporting period.' from dataset ds where datasetid not in (select datasetid from datasetelement left join datavalue dv using(dataelementid) left join ds_lastupdate using(datasetid) where date_part('day', now() - dv.lastupdated::timestamp) < ds_lastupdate.interval*3)

union all 

select 'dataset_nonewdata', count(*)::varchar, (100*count(*)/(select count(*) from dataset))::varchar || '%', 'Data sets with no data values in the last 3 periods (based on data set period type).' from dataset where datasetid not in (select distinct datasetid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by datasetid);
```

#### SQL - Listing

- List the data sets that have not had any **updated** data values entered within the last 3 periods (relative to the period type assigned to the dataset)

```
select 'Data sets with no data values with lastupdated date within the last 3 periods (based on data set period type). Note: this is not taking into account the reporting period.';
with ds_lastupdate as (select datasetid, avg(date_part('day', pe.enddate::timestamp - pe.startdate::timestamp))::int as interval from dataset ds left join period pe using(periodtypeid) group by datasetid), 
select name,uid from dataset ds where datasetid not in (select datasetid from datasetelement left join datavalue dv using(dataelementid) left join ds_lastupdate using(datasetid) where date_part('day', now() - dv.lastupdated::timestamp) < ds_lastupdate.interval*3);
```

- List the data sets that have not had any **new** data values entered within the last 3 periods (relative to the period type assigned to the dataset)

```
select 'Data sets with no data values in the last 3 periods (based on data set period type).';
with 
ds_period as (select datasetid, dataelementid, periodid from dataset ds left join period pe using(periodtypeid) left join datasetelement using(datasetid) where date_part('day', now() - pe.enddate::timestamp)::int <= 3*date_part('day', pe.enddate::timestamp - pe.startdate::timestamp)::int)
select name,uid from dataset where datasetid not in (select distinct datasetid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by datasetid);
```

## Data sets should be assigned to organisation units

All **active** datasets should be assigned to an organisation unit. Active data sets are data sets which should be currently used (within the last 3 reporting periods) to collect data.

### Recommendation

- Data sets that have not been recently updated (within the last 100 days) and are not assigned to any organisation units that **should be** active should be assigned to organisation units as appropriate
- Data sets that have not been recently updated (within the last 100 days) and **should not be** active should be marked as archived (ie. assign it a prefix)
- Data sets that have not been recently updated (within the last 100 days) and **do not have any data** should be deleted if they are not going be used. You can determine if a data set has data by reviewing the section ["Data sets should have data."](#data-sets-should-have-data)

### Diagnosing if the problem exists

We can determine if data sets have not been updated within the last 100 days and are not assigned to any organisation units by using the following queries

#### SQL - Identification

To get a count of these data sets use the following:

```
select 'dataset_count' as indicator, count(*)::varchar as value,'100%' as percent, 'Total number of data sets' as description from dataset

union all

select 'dataset_abandoned',count(*)::varchar , (100*count(*)/(select count(*) from dataset))||'%' as percent, 'Data sets that have not been changed in last 100 days and are assigned to 1 or less orgunits' from dataset where date_part('day', now() - lastupdated::date) > 100 and (datasetid not in (select datasetid from datasetsource) or datasetid in (select datasetid from datasetsource group by datasetid having count(*) = 1));
```

#### SQL - Listing

To get a list of these data sets use the following:

```
select 'Data sets that have not been changed in last 100 days and are assigned to 1 or less orgunits';
select name,uid from dataset where date_part('day', now() - lastupdated::date) > 100 and (datasetid not in (select datasetid from datasetsource) or datasetid in (select datasetid from datasetsource group by datasetid having count(*) = 1));
```

##  Fixing these problems via deletion

In order to remove datasets if needed there are 3 processes we can recommend:

1. Deleting them manually through the maintenance app if you have access to them
2. Deleting them by exporting them out and importing them back in using **DELETE** as the import mode
3. Deleting them through the API

To delete the items via the API you have two options

**Individual deletion**

```
```

**Multiple deletion**
```
```

## Summary

You can run a summary query in order to generate summary statistics on all of these items at once. Use the following query to retrieve a summary output:

```
with ds_lastupdate as (select datasetid, avg(date_part('day', pe.enddate::timestamp - pe.startdate::timestamp))::int as interval from dataset ds left join period pe using(periodtypeid) group by datasetid), 
ds_period as (select datasetid, dataelementid, periodid from dataset ds left join period pe using(periodtypeid) left join datasetelement using(datasetid) where date_part('day', now() - pe.enddate::timestamp)::int <= 3*date_part('day', pe.enddate::timestamp - pe.startdate::timestamp)::int)

select 'dataset_count' as indicator, count(*)::varchar as value,'100%' as percent, 'Total number of data sets' as description from dataset

union all

select 'dataset_abandoned',count(*)::varchar , (100*count(*)/(select count(*) from dataset))||'%' as percent, 'Data sets that have not been changed in last 100 days and are assigned to 1 or less orgunits' from dataset where date_part('day', now() - lastupdated::date) > 100 and (datasetid not in (select datasetid from datasetsource) or datasetid in (select datasetid from datasetsource group by datasetid having count(*) = 1))

union all

select 'dataset_noupdateddata', count(*)::varchar, (100*count(*)/(select count(*) from dataset))::varchar || '%', 'Data sets with no data values with lastupdated date within the last 3 periods (based on data set period type). Note: this is not taking into account the reporting period.' from dataset ds where datasetid not in (select datasetid from datasetelement left join datavalue dv using(dataelementid) left join ds_lastupdate using(datasetid) where date_part('day', now() - dv.lastupdated::timestamp) < ds_lastupdate.interval*3)

union all 

select 'dataset_nonewdata', count(*)::varchar, (100*count(*)/(select count(*) from dataset))::varchar || '%', 'Data sets with no data values in the last 3 periods (based on data set period type).' from dataset where datasetid not in (select distinct datasetid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by datasetid);
```