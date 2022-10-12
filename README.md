# Cluvio-SQL-examples
Cluvio SQL examples of meal plan business


These are just screenshots of fully interactive charts within Cluvio using these SQL syntaxes to perform cohort anyalses:



SELECT
{nutrition_mealtotal.created_at:aggregation} eatmonth,
{rubyuser_rubyuser.created_at:month} signmonth, 
count(*) mealslogged
FROM 
nutrition_mealtotal 
RIGHT JOIN rubyuser_rubyuser 
ON nutrition_mealtotal.user_id = rubyuser_rubyuser.id
WHERE 
{nutrition_mealtotal.created_at=timerange}
GROUP BY
{rubyuser_rubyuser.created_at:month},
{nutrition_mealtotal.created_at:aggregation}



select count(*), nutrition_mealtotal.user_id, rubyuser_rubyuser.user_id, auth_user.id, auth_user.email, rubyuser_rubyuser.username 
from nutrition_mealtotal
inner join rubyuser_rubyuser
on rubyuser_rubyuser.id = nutrition_mealtotal.user_id
inner join auth_user
on auth_user.id = rubyuser_rubyuser.user_id 
group by nutrition_mealtotal.user_id,
auth_user.id,
rubyuser_rubyuser.user_id,
rubyuser_rubyuser.username 
order by count desc
