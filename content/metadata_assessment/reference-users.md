## Users should log in routinely

All users should log in routinely. The definition of "routine" may vary between implementations and therefore you can assess this over both the last 12 months as well as a pre-defined period of your choosing.

### Recommendation

- Users that have not logged in for the period defined as routine can likely be disabled.
- Users that have never logged in can likely be deleted.
- For users in which an invitation was sent but never activated their account two courses of action can be taken:
  - Delete the invitation
  - Resend the invitation for the user to activate their account

### Diagnosing if the problem exists

Users that have not been logging in can be identified via SQL. 

#### SQL - Identification

You can obtain the number of users that have not logged in routinely using the following query. Note you should alter the period to that which you can consider routine.

```
select 'user_count' as indicator, count(*)::varchar as value, '100%' as percent, 'Total number of users' as description from users

union all

select 'user_active', count(*)::varchar , (100*count(*)/(select count(*) from users))||'%', 'Users logged in during last 30 days' from users where date_part('day', now() - lastlogin::date) <= 30

union all

select 'user_active1y', count(*)::varchar , (100*count(*)/(select count(*) from users))||'%', 'Users logged in during last 365 days' from users where date_part('day', now() - lastlogin::date) <= 365

union all

select 'user_active1yenabled', count(*)::varchar , (100*count(*)/(select count(*) from users))||'%', 'Users not logged in during last 365 days, but are not disabled' from users where date_part('day', now() - lastlogin::date) > 365 and disabled = false;
```

#### SQL - Listing

###  Fixing these problems via deletion

## Users should be part of a user group

If there are any sharing settings applied, all users should be part of a user group.

### Recommendation

If a user is not part of any user group(s) (or a user group(s) that gives them access to something they need), they should be added to the required user group(s).

### Diagnosing if the problem exists

#### SQL - Identification

#### SQL - Listing

##  Fixing this problem by adding users to user groups



