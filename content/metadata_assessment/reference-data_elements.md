# Data Elements

## Data elements should be in a data element group

All data elements should be in a data element group. This allows users to find the data elements more easily in analysis apps and also contributes to having more complete data element group sets. Maintenance operations can also be made more efficient by applying bulk settings (ex. sharing) to all data elements within a data element group.

### Recommendation

Data elements that are not in a data element group should be added to a relevant data element group. If the data elements are not needed, they should be deleted.

### Diagnosing if the problem exists

Data elements that are not in a data element group can be found by running the data integrity check. You can also use the following queries to obtain summaries of these data elements.

#### SQL - Identification

You can identify the number of **AGGREGATE** and **TRACKER** data elements that are not within a data element group using the following query:
```
select 'aggregate_dataelement_nongrouped', count(*)::varchar, (100*count(*)/(select count(*) from dataelement))::varchar || '%', 'Aggregate data elements not in any data element groups.' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from dataelementgroupmembers)

union all

select 'tracker_dataelement_nongrouped', count(*)::varchar, (100*count(*)/(select count(*) from dataelement))::varchar || '%', 'Tracker data elements not in any data element groups.' from dataelement where domaintype != 'TRACKER' and dataelementid not in (select dataelementid from dataelementgroupmembers);
```

If you wish to focus your assessment on data elements that have been recently updated, rather then all data elements in the system, you can use the following

**AGGREGATE**
```
with ds_period as (select datasetid, dataelementid, periodid from dataset ds left join period pe using(periodtypeid) left join datasetelement using(datasetid) where date_part('day', now() - pe.enddate::timestamp)::int <= 3*date_part('day', pe.enddate::timestamp - pe.startdate::timestamp)::int)

select 'dataelement_nongrouped_newdata', count(*)::varchar, (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE' ))::varchar || '%', 'Aggregate data elements with data values in the last 3 periods (based on data set period type) that are not in any groups.'  from dataelement where domaintype = 'AGGREGATE' and dataelementid in (select distinct dataelementid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by dataelementid) and dataelementid not in (select dataelementid from dataelementgroupmembers);
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
select name,uid from dataelement where domaintype = 'TRACKER' and dataelementid not in (select dataelementid from dataelementgroupmembers);
```

## Data elements should have data values

All data elements in a production database should have data values associated with them. If there are data elements that have been in the system for some time and do not have any data values associated with them, they are serving no purpose in the system. They may have been created during training or a development period. 

### Recommendation

Data elements that do not have any data values should be deleted. Data elements that should have recent data values but do not should be reviewed to determine if the program intends to keep reporting on them; if not these should be removed from the dataset they are associated with.

### Diagnosing if the problem exists

We can review if data elements have any data values using different sets of criteria. This will allow you to determine in more detail if data elements need to be deleted or can be kept. The criteria we are currently summarizing for **AGGREGATE** data elements includes:

- "Abandoned" data elements. These are data elements that have not been updated in at least 100 days and do not have any data values associated with them.
- Data elements that have not been recently updated with data values (we defined this as data elements with no new values in the last 3 periods based on the data set period type associated with those data elements)
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

#### SQL - Listing

We can list **AGGREGATE** data elements that meet the criteria we have outlined previously using the following:

- Abandoned data elements

```
select 'Aggregate data elements that have not been changed in last 100 days and do not have any data values';
select name,uid from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from datavalue group by dataelementid) and date_part('day', now() - lastupdated::date) > 100;
```

- Data elements with no values in the last 3 periods based on the data set period type associated with those data elements
```
select 'Aggregate data elements with no data values in the last 3 periods (based on data set period type).';
select name,uid from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select distinct dataelementid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by dataelementid)
```

- All data elements with no values at all
```
select 'Aggregate data elements with NO data values';
select name,uid from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from datavalue group by dataelementid)
```

## Data elements should be used for analysis

All data elements that are captured in DHIS2 should be used to produce some type of analysis output (charts, maps, tables). This can be by using them directly in an output, or by having them contribute to an indicator calculation that is used an output. 

### Recommendation

Data elements that are not routinely being reviewed in analysis, either directly or indirectly through indicators, should be reviewed to determine if they still need to be collected. If these are meant to be used in routine review, then associated outputs should be created using them. If these data elements are not going to be used for any type of information review, consideration should be made to either archive them or delete them.

### Diagnosing if the problem exists

To review if data elements are being used in analysis outputs, we can review saved charts, maps and tables to determine if the data element is either directly or indirectly being used in these saved items.

#### SQL - Identification

```
select 'dataelement_noanalysis', count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements that are not used in any favourites, either directly or through indicators' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select de.dataelementid from dataelement de left join indicator ind on (ind.numerator like '%'||de.uid||'%' or ind.denominator like '%'||de.uid||'%') where ind.name is not null and ind.indicatorid in (select indicatorid from datadimensionitem where indicatorid > 0)) and dataelementid not in (select dataelementoperand_dataelementid from datadimensionitem where dataelementoperand_dataelementid > 0) and dataelementid not in (select dataelementid from datadimensionitem where dataelementid > 0);
```

#### SQL - Listing

```
select 'Aggregate data elements that are not used in any favourites, either directly or through indicators.';
select name,uid  from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select de.dataelementid from dataelement de left join indicator ind on (ind.numerator like '%'||de.uid||'%' or ind.denominator like '%'||de.uid||'%') where ind.name is not null and ind.indicatorid in (select indicatorid from datadimensionitem where indicatorid > 0)) and dataelementid not in (select dataelementoperand_dataelementid from datadimensionitem where dataelementoperand_dataelementid > 0) and dataelementid not in (select dataelementid from datadimensionitem where dataelementid > 0);
```

## Fixing the problem via deletion

In order to remove data elements, some extra steps may need to be taken. This is because data elements can also be associated with data values and audit tables that show you how values have been modified. We can therefore discuss the following:

### Data elements with no associated values

In order to remove data elements with no values at all, there are 3 processes we can recommend:

1. Deleting them manually through the maintenace app if you have access to them
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
with ds_period as (select datasetid, dataelementid, periodid from dataset ds left join period pe using(periodtypeid) left join datasetelement using(datasetid) where date_part('day', now() - pe.enddate::timestamp)::int <= 3*date_part('day', pe.enddate::timestamp - pe.startdate::timestamp)::int)

select 'dataelement_count' as indicator, count(*)::varchar as value,'100%' as percent, 'Total number of data elements' as description from dataelement

union all

select 'dataelement_nongrouped', count(*)::varchar, (100*count(*)/(select count(*) from dataelement))::varchar || '%', 'Data elements not in any data element groups.' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from dataelementgroupmembers)

union all

select 'dataelement_abandoned',count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements that have not been changed in last 100 days and do not have any data values' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from datavalue group by dataelementid) and date_part('day', now() - lastupdated::date) > 100

union all

select 'dataelement_noassign',count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements assigned to 1 or less orgunit' from dataelement where (dataelementid not in (select dataelementid from datasetelement)) or (dataelementid in (select dataelementid from datasetelement where datasetid not in (select datasetid from datasetsource)) or  (dataelementid in (select dataelementid from dataelement de left join datasetelement dse using(dataelementid) left join datasetsource dss using(datasetid) group by dataelementid having count(dss.*) = 1)))


union all

select 'dataelement_nongrouped_newdata', count(*)::varchar, (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE' ))::varchar || '%', 'Aggregate data elements with data values in the last 3 periods (based on data set period type) that are not in any groups.'  from dataelement where domaintype = 'AGGREGATE' and dataelementid in (select distinct dataelementid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by dataelementid) and dataelementid not in (select dataelementid from dataelementgroupmembers)

union all

select 'dataelement_nodata', count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements with NO data values' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select dataelementid from datavalue group by dataelementid)

union all

select 'dataelement_nonewdata', count(*)::varchar, (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE' ))::varchar || '%', 'Aggregate data elements with no data values in the last 3 periods (based on data set period type).' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select distinct dataelementid from ds_period where (dataelementid,periodid) in (select dataelementid, periodid from datavalue) group by dataelementid)

union all

select 'dataelement_noanalysis', count(*)::varchar , (100*count(*)/(select count(*) from dataelement where domaintype = 'AGGREGATE'))||'%' as percent, 'Aggregate data elements that are not used in any favourites, either directly or through indicators' from dataelement where domaintype = 'AGGREGATE' and dataelementid not in (select de.dataelementid from dataelement de left join indicator ind on (ind.numerator like '%'||de.uid||'%' or ind.denominator like '%'||de.uid||'%') where ind.name is not null and ind.indicatorid in (select indicatorid from datadimensionitem where indicatorid > 0)) and dataelementid not in (select dataelementoperand_dataelementid from datadimensionitem where dataelementoperand_dataelementid > 0) and dataelementid not in (select dataelementid from datadimensionitem where dataelementid > 0);
```