# Dashboards

- [Dashboards](#dashboards)
  - [Dashboards should have content](#dashboards-should-have-content)
    - [Recommendation](#recommendation)
    - [Diagnosing if the problem exists](#diagnosing-if-the-problem-exists)
      - [SQL - Identification](#sql---identification)
      - [SQL - Listing](#sql---listing)
  - [Dashboards should be viewed routinely](#dashboards-should-be-viewed-routinely)
    - [Recommendation](#recommendation-1)
    - [Diagnosing if the problem exists](#diagnosing-if-the-problem-exists-1)
      - [SQL - Identification](#sql---identification-1)
      - [SQL - Listing](#sql---listing-1)
  - [Dashboards should be shared (when appropriate)](#dashboards-should-be-shared-when-appropriate)
    - [Recommendation](#recommendation-2)
    - [Diagnosing in the problem exists](#diagnosing-in-the-problem-exists)
      - [Identification](#identification)
      - [Listing](#listing)
    - [Updating a private dashboards sharing settings](#updating-a-private-dashboards-sharing-settings)
  - [Fixing these problems via deletion](#fixing-these-problems-via-deletion)
  - [Summary](#summary)

## Dashboards should have content

All dashboards should have content on them. Dashboards without any content do not serve any purpose, and may have been created by accident or as part of a training exercise.

### Recommendation

Dashboards without content that have not been modified in the last 14 days can be removed.

### Diagnosing if the problem exists

Dashboards that do not have any content can be identified via the API or through a SQL query.

#### SQL - Identification

You can identify the number of dashboards without any content using the following query:
```
select 'dashboard_empty', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards with no content' from dashboard where dashboardid not in (select dashboardid from dashboard_items)
```

#### SQL - Listing

You can list the dashboards without any content using the following query
```
```

## Dashboards should be viewed routinely

All dashboards should be reviewed routinely. Dashboards that are no longer viewed routinely are not being used and serve no purpose within the system. The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as a pre-defined period of your choosing.

### Recommendation

Dashboards that are not viewed routinely can be removed.

### Diagnosing if the problem exists

#### SQL - Identification

You can identify the number of dashboards that are not being viewed routinely using the following query:
```
select 'dashboard_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that have been viewed 1 time or less after 2017' as description from dashboard where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all 

select 'dashboard_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that have not been opened in the last 12 months' as description from dashboard where not uid in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'dashboard_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that are publicly viewable' as description from dashboard where publicaccess like 'r%'

union all

select 'dashboard_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard where publicaccess like 'r%'))||'%', 'Public dashboards that have been viewed 1 time or less after 2017' as description from dashboard where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all

select 'dashboard_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard where publicaccess like 'r%'))||'%', 'Public dashboards that have not been opened in the last 12 months' as description from dashboard where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);
```

To successfully use this query, you should modify the year referenced in the query. This example is showing dashboards that have been viewed 1 time or less after 2017, and the year referenced is >= 2018. If you want to use other years as reference you should update this accordingly.

This query will output the following information for you to review:

- Dashboards that have been viewed 1 time or less since the year you select
- Dashboards that have not been opened in the last 12 months
- Dashboards that are publicly viewable
- Public dashboards that have been viewed 1 time or less since the year you select
- Public dashboards that have not been opened in the last 12 months

#### SQL - Listing

You can list the dashboards that have been viewed 1 time or less since a certain year using the following query

```
```

You can list the dashboards that have been not been viewed in the last 12 months using the following query

```
```

## Dashboards should be shared (when appropriate)

Dashboards should be shared so they can be used appropriately throughout the system. In cases where individual, private dashboards are made, these should serve a very specific purpose unique to the user that created it.

### Recommendation

- The number of private dashboards should be less then the number of shared dashboards
- Private dashboards that are no longer in use can be deleted
- Private dashboards in which more users need access to should have the correct sharing settings applied to them

### Diagnosing in the problem exists

**SQL**

#### Identification

You can identify the number of private dashboards as well as dashboards shared with at least 10 users (users are placed within a user group that the dashboard is shared with) using the following query:

```
select 'dashboard_private', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that are private' from dashboard where publicaccess = '--------' and dashboardid not in (select dashboardid from dashboardusergroupaccesses union select dashboardid from dashboarduseraccesses)

union all

select 'dashboard_shared10+', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards shared with 10 or more people' from dashboard where dashboardid in (select dash.dashboardid from dashboardusergroupaccesses left join dashboard dash using(dashboardid) left join usergroupaccess uga using (usergroupaccessid) left join usergroupmembers ugm using (usergroupid) group by dash.dashboardid having count(*) >= 5) OR publicaccess like 'r%'
```

#### Listing

You can list the dashboards that are private using the following query
```
```

### Updating a private dashboards sharing settings

In order to modify the sharing settings of a private dashboard

##  Fixing these problems via deletion

In order to remove these dashboards there are 3 processes we can recommend:

1. Deleting them manually through the dashboard app if you have access to them
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

You can run a summary query in order to generate summary statistics and all of these items at once. Use the following query to retrieve a summary output:
```
select 'dashboard_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of dashboards' as description from dashboard

union all

select 'dashboard_empty', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards with no content' from dashboard where dashboardid not in (select dashboardid from dashboard_items)

union all 

select 'dashboard_private', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that are private' from dashboard where publicaccess = '--------' and dashboardid not in (select dashboardid from dashboardusergroupaccesses union select dashboardid from dashboarduseraccesses)

union all

select 'dashboard_shared10+', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards shared with 10 or more people' from dashboard where dashboardid in (select dash.dashboardid from dashboardusergroupaccesses left join dashboard dash using(dashboardid) left join usergroupaccess uga using (usergroupaccessid) left join usergroupmembers ugm using (usergroupid) group by dash.dashboardid having count(*) >= 5) OR publicaccess like 'r%'

union all

select 'dashboard_used' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that have been viewed 1 time or less after 2017' as description from dashboard where uid not in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all 

select 'dashboard_used1y' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that have not been opened in the last 12 months' as description from dashboard where not uid in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid)

union all 

select 'dashboard_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards that are publicly viewable' as description from dashboard where publicaccess like 'r%'

union all

select 'dashboard_used_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard where publicaccess like 'r%'))||'%', 'Public dashboards that have been viewed 1 time or less after 2017' as description from dashboard where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and extract(year from timestamp) >= 2018 group by favoriteuid having count(*) >1)

union all

select 'dashboard_used1y_public' as indicator, count(*)::varchar as value, (100*count(*)/(select count(*) from dashboard where publicaccess like 'r%'))||'%', 'Public dashboards that have not been opened in the last 12 months' as description from dashboard where publicaccess like 'r%' and uid not in (select favoriteuid from datastatisticsevent where eventtype = 'DASHBOARD_VIEW' and favoriteuid is not null and timestamp > (now() - INTERVAL '12 months') group by favoriteuid);
```
Note that you should run the queries to list dashboards that meet certain criteria one-by-one and not as a summary.