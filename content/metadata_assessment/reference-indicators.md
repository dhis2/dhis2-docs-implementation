# Indicators


## Indicators should be in an indicator group

All indicators should be in a data element group. This allows users to find the indicators more easily in analysis apps and also contributes to having more complete indicators group sets. Maintenance operations can also be made more efficient by applying bulk settings (ex. sharing, filtering) to all indicators within an indicator group.

### Recommendation

Indicators that are not in a indicator group should be added to a relevant indicator group. If the indicators are not needed, they should be deleted.

### Diagnosing if the problem exists

Indicators that are not in a data element group can be found by running the data integrity check. You can also use the following queries to obtain summaries of these indicators.

#### SQL - Identification

You can identify the number of indicators that are not within an indicator group using the following query (note, this will also give you the total number of existing indicators)

```
select 'indicator_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of indicators' as description from indicator

union all

select 'indicator_nongrouped',count(*)::varchar, (100*count(*)/(select count(*) from indicator))||'%', 'Indicators not in any groups' from indicator where indicatorid not in (select indicatorid from indicatorgroupmembers);
```

#### SQL - Listing


## Indicators should be used in analysis outputs

All indicators that are calculated should be used to produce some type of analysis output (charts, maps, tables). This can be by using them directly in an output or providing direct feedback in a dataset.

### Recommendation

Indicators that are not routinely being reviewed in analysis, either in an output or data set, should be reviewed to determine if they still need to be calculated. If these are meant to be used for routine review, then associated outputs should be created using them. If these indicators are not going to be used for any type of information review, consideration should be made to either archive them or delete them.

### Diagnosing if the problem exists

To review if indicators are being used in analysis outputs, we can review saved charts, maps and tables to determine if the indicator is being used in saved output or within a data set.

#### SQL - Identification

```
select 'indicator_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of indicators' as description from indicator

union all

select 'indicator_nouse',count(*)::varchar, (100*count(*)/(select count(*) from indicator))||'%', 'Indicators not used in favourites OR data sets' from indicator where indicatorid not in (select indicatorid from datadimensionitem where indicatorid > 0) and indicatorid not in (select indicatorid from datasetindicators)

union all

select 'indicator_noanalysis',count(*)::varchar, (100*count(*)/(select count(*) from indicator))||'%', 'Indicators not used in favourites' from indicator where indicatorid not in (select indicatorid from datadimensionitem where indicatorid > 0);
```

#### SQL - Listing

##  Fixing these problems via deletion

## Indicators should be shared with a user group(s)

Depending on the system configuration, indicators may need correct sharing settings applied to them such that each indicator has the correct sharing settings applied to the indicator.

### Recommendation

If an indicator is not shared correctly, share it with the appropriate user group(s)

### Diagnosing if the problem exists

#### SQL - Identification

#### SQL - Listing

##  Fixing these problems via deletion
