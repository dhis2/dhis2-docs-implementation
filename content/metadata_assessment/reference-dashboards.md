# Dashboards

## All dashboards should have content

All dashboards should have content on them. Dashboards without any content do not serve any purpose, and may have been created by accident or as part of a training exercise.

### Recommendation

Dashboards without content that have not been modified in the last 14 days can be removed.

### Diagnosing if the problem exists

Dashboards that do not have any content can be identified via the API or SQL.

**SQL**

You can identify the number of dashboards without any content using the following query:
```
select 'dashboard_empty', count(*)::varchar, (100*count(*)/(select count(*) from dashboard))||'%', 'Dashboards with no content' from dashboard where dashboardid not in (select dashboardid from dashboard_items)
```
You can list the dashboards without any content using the following query
```
```

**API**


###  Fixing the problem via deletion

In order to remove these dashboards there are 3 processes we can recommend:

1. Deleting them manually through the dashboard app if you have access to them
2. Deleting them through the API
3. Deleting them by exporting them out and importing them back in using **DELETE** as the import mode

To delete the items via the API you have two options

**Individual deletion**
```
```


**Multiple deletion**
```
```