String functions:
- || is the concatenation operator; it merges multiple texts into one (in SQL Server use +, in MySQL use concat()),
- length(x) returns the length of text x (in SQL Server use len()),
- lower(x), upper(x), initcap(x) will all write x in the appropriate case,
- substring(x, y, z) will return the part of x starting from position y and with z characters in length (in Oracle use substr()),
- replace(x,y,z) will search x for y, and if it finds any y, it will replace if with z.

Numeric functions:
- Computations in floating point numbers are not always exact. Use decimal numbers for all money columns and when precision matters.
- Dividing two integers is a integer division. Use CAST(column AS TYPE) to avoid it.
- mod(x,y) or x%y - it returns the reminder of division of x by y
- round (x) or round(x,p) - rounds up the number to the integer or to specified precision (p)
- ceil(x) - rounds up to a nearest integer value
- floor(x) - rounds down to a nearest integer value
- trunc(x) or trunc(x,p) - always round towards zero to interger value or to specified precision (p)
- abs(x) - returns a absolute value of x
- sqrt(x) - returns a square root of x

Date functions:
- SQL features dates ('2010-01-01'), time ('13:00:00') and timestamps ('2010-01-01 13:00:00').
- You can compare the above types, use BETWEEN and ORDER BY with them.
- The function EXTRACT(DAY FROM column) allows to extract certain parts of date/time.
- Use AT TIME ZONE to switch between time zones.
- INTERVAL '7' DAY is an interval of 7 days which you can add to/subtract from a timestamp/date.
- INTERVAL '2-1' YEAR TO MONTH another type of interval, this one is a interval of 2 years and 1 month.
- For current date and time, you can use CURRENT_DATE, CURRENT_TIME or CURRENT_TIMESTAMP.

Null values:
- Rule number one: never trust a NULL. Keep your eyes open.
- Use the operator IS NULL to check if the column is NULL.
- Use the operator IS NOT NULL to check if the column is not NULL.
- The equality and non-equality conditions (price = 7, price = NULL, price > 15) are NEVER true when the argument is NULL.
- Arithmetical operations (e.g. a + b) and most functions (e.g. a || b, length(a)) will return a NULL if any of the values is a NULL.
- COALESCE(x,y,…) returns the first non-NULL argument.
- NULLIF(x,y) returns x when x != y or NULL when x = y.
- In some databases, you can use NULLS FIRST or NULLS LAST to specify how NULLs are treated in the ORDER BY clause.

Aggregate functions:
- COUNT(*) counts the number of all rows.
- COUNT(column1) counts the number of rows where column1 is not NULL.
- COUNT can be used to count non-NULL expressions.
- Avoid COUNT(*) with LEFT JOINs.
- DISTINCT only takes into account distinctive values.
- AVG, SUM, MAX and MIN ignore NULLs, but COUNT takes them into account when counting the number of rows.
- You can use COALESCE(x,y) to replace x with y when x is NULL. For example, you can replace NULLs with 0.
- You can use AVG, SUM, MIN or MAX with DISTINCT.
- You can use ROUND to round the score obtained with AVG.

Case when:
- A simple CASE has the following syntax:
	CASE column_name
	  	WHEN value1 THEN text1
  		WHEN value2 THEN text2
  		…
  		ELSE text_else
	END
- A searched CASE WHEN has the following syntax:
	CASE
  		WHEN condition1 THEN text1
  		WHEN condition2 THEN text2
  		…
  		ELSE text_else
	END
- The ELSE part is optional.
- Remember about the END clause at the end.
- You can use CASE WHEN with SUM to count multiple values in a single query:
	SUM(CASE WHEN x THEN 1 ELSE 0 END)
- Similarly, you can use CASE WHEN with COUNT to count multiple values in a single query
	COUNT(CASE WHEN x THEN column END)
