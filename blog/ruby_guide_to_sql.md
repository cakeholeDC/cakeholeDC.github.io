#A Rubyist's Guide to SQL Joins

If you've ever had a job that required you to run reports, you've probably had some light exposure to SQL _(Structured Markup Language)_. You've probably noticed that even if you don't have any coding experience, the syntax is pretty readable.

```sql
SELECT column FROM table WHERE (column = 'value')
```

Even if you don't know what the data is, you can draw the conclusion that we're `SELECT`ing _something_ `FROM` _something else_ `WHEN` a condition is met. You can probably even guess what that condition is! Pretty simple, right? Well, it is. Until `JOIN` enters the picture...

For years, I struggled with how to properly `JOIN` two tables. In fact, I hated them so much that my go to move was to download the data to _.csv_ and perform a bunch of `VLOOKUP` functions in Excel™

<p align="center">![shudder.gif](https://media.giphy.com/media/DBa308wq8XTMs/giphy.gif)

I know. **I apologize.**

The reason I was scared of `JOIN`s is because whenever I looked up examples and documentaiton I always found something that looked like this:

```sql
SELECT * FROM employees e
  JOIN jobs j ON e.job_id = j.job_id
  LEFT JOIN employees m ON e.manager_id = m.employee_id
  LEFT INNER JOIN departments d ON d.department_id = e.department_id
  OUTER JOIN employees dm ON d.manager_id = dm.employee_id
  LEFT JOIN locations l ON d.location_id = l.location_id
  LEFT JOIN countries c ON l.country_id = c.country_id
  RIGHT JOIN regions r ON c.region_id = r.region_id
  LEFT OUTER JOIN jobs jj ON jj.job_id = jh.job_id
ORDER BY e.employee_id;
```
*I'm sorry... what?*


Along with the super useful documentation of:

```
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.

Note: FULL OUTER JOIN can potentially return very large result-sets!

Tip: FULL OUTER JOIN and FULL JOIN are the same.
```