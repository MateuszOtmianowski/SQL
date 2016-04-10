# SQL

##Notes from SQL course on Udemy

###General

*	**DESC** list columns in a table with type of data stored in each;
*	**q’[XXX]’** allows the use of special characters, any character can be used instead of “[“ and “]” as far as they are the same;
*	**DISTINCT** is used for showing unique combination of values, only one DISTINCT operator can be used in one single query;
*	**SELECT ‘XXX’** from table returns XXX for each row in the table;
*	**||** could be used to concatenate columns into one;
*	Any operation (like mathematical) with NULL values, except concatenate, returns NULL;
*	**<>** and **!=** can both be used and give the same result;
*	**BETWEEN XXX AND XXX** can be used with numbers, dates and characters;
*	**IN** queries a database for the values in a given list;
*	**LIKE** is used for searching in string values, following special signs can be used:
>	**%**: 0 or more characters;
>	**_**: 1 character;
*	**LIKE** without special characters is equal to “=” operator but is slower;
*	**LIKE** is case sensitive;
*	**IS NULL** is used for searching for NULL values, =NULL does not work;
*	**Logical operators** include:
  *	**AND**
  *	**OR**
  *	**NOT**
*	**ORDER BY xxx ASC/DESC (NULLS FIRST/LAST)**;
*	adding a number to a date, increases day count;
*	substracting two dates results in the number of days between the two;

###Single row functions
*	**Case conversion functions**:
  -	**LOWER**: converts all input characters to lowercase;
  -	**UPPER**: converts all input characters to uppercase;
  -	**INITCAP**: converts first character to uppercase and the rest to lowercase;
* It is a good idea to use in search querries UPPER or LOWER, becouse in that case you don't need to know how the entry was written, this could look as follows:
  > WHERE UPPER(*column_name*)=*'something'*;
* **Character manipulation functions**:
  - **SUBSTR**('*string**', *first_num*, *last_num*);
  - **LENGTH**('*string*');
  - **CONCAT**('*string*','*string*') rarely used, equivalent to ||, works only with a two strings;
  - **INSTR**('*string*',''*string*') - return the postion of second string in the first one;
  - **TRIM**('*string*'), deletes all spaces;
  - **LTRIM**('*string*') deletes spaces on the left;
  - **RTRIM**('*string*') deletes spaces on the right;
  - **REPLACE**('*string*',''*string*','*string*');
  - **LPAD**('*string*',*number*,'*character*') fills the entry with characters on the left side, so the whole length equals *number*;
  - **RPAD**('*string*',*number*,'*character*') analogous to the above but fills the entry on the right side;
  
*	**Numeric functions**:
  - **ROUND**(*number*,*number*);
  - **TRUNC**(*number*,*number*) truncates value to a specified decimal;
  - **CEIL**(*number*) returns the smallest integer greater or equal to a specified number ex CEIL(2,67) returns '3';
  - **FLOOR**(*number*) returns the largest integer smaller or equal to a specified number ex CEIL(2,67) returns '2';
  - **MOD**(*number*, *number*) return reminder of division;

*	**Dates functions**:
  - **ADD_MONTHS**(*date*,*number*);
  - **MONTHS_BETWEEN**(*date*,*date*);
  - **ROUND**(*date*, 'MONTH'/'YEAR') rounds the date;
  - **TRUNC**(*date*, 'MONTH'/'YEAR') rounds the date;
  - **NEXT_DAY**(*date*, 'TUESDAY') returns next specified day of week;
  - **LAST_DAY**(*date*) returns last day of the month;

*	**Conversion functions**:
  - **TO_NUMBER**(*char*[,'format_model']);
  - **TO_CHAR**(*number*/*date*[,'format_model']);
  - **TO_DATE**(*char*[,'format_model']);

*	**Null Value Functions**:
  - **NVL**(*Expression1*, *Expression2*) if *Expression1* is NULL returns *Expression2*, data types must match, useful in arithmetic operations to avoid calculation error;
  - **NVL2**(*Expression1*, *Expression2*, *Expression3*) if *Expression1* is not NULL, return *Expression2*, else return *Expression3*, *Expression1* does not to be of the same type as *Expression2* and *Expression3*, but *Expression2* and *Expression3* must be same data type;
  - **NULLIF**(*Expression1*, *Expression2*) compares both expression, return NULL if they are equal, if not return *Expression1*, could be followed with checking if it is NULL to check if given condition is met;
  - **COALESCE**(*Expression1*, *Expression2*,...,*ExpressionX*) returns first expression that is not NULL or the last expression if all previous are NULL;

*	**Conditional Expressions**:
  - **CASE** *expression* WHEN *comparison_expression1* THEN *return_expression1*
  [WHEN *comparison_expression2* THEN *return_expression2*
  WHEN *comparison_expressionN* THEN *return_expressionN*
  ELSE *else_expr*] **END**
  - *expression* and *comparison_expression* msut be of the same data type;
  - **CASE** can be used both in **SELECT** and **WHERE** clauses;
  - **DECODE**(*col*|*expression*, *search1*, *result1* [,*search2*,*result2*,...,][,*default*]) could be used as alternative to **CASE**;
  - last alone expression is used as default value if none of decode statements are met;
 
*	**Group functions**:
  - SELECT group_function([DISTINCT|ALL] *column_name*),... FROM *table* [WHERE *condition];
  - group functions operate on multiple rows and return one result per group;
  - gfs are used after SELECT keyword, multiple gfs can be used in one SELECT statement;
  - gfs ignore NULL values, null value functions can be used to handle such cases as for example COUNT(nvl(commission_pct,0));
  - ALL is default;
  - gfs include: *AVG*, *COUNT*, *MAX*, *MIN*, *SUM*;
  - **COUNT**(*) includes rows with NULL values;
  - nested group functions need GROUP BY clause;
 
*	**GROUP BY clause**:
  - column aliases can not be used in GROUP BY clauses;
  - SELECT clause can not have any different columns then used in GROUP BY clause;

*	**HAVING clause**:
  - **WHERE** clause restricts rows, **HAVING** clause restricts groups;
  - **HAVING** clause is used after group by clause;
 
*	**Joins**:
  - **NATURAL JOIN** joins two tables with the columns that have the same name, if combination of columns having same name is not matched rows are not returned;
  - *equijoin* is join with *USING* statement, it is join using only specific columns in two tables, syntax looks as follows:... JOIN *table* USING (*column_name*), more than one *column_name* could be used;
  - table aliases are used for handling duplicate column names in two tables, tehy increase readability and query performance;
  - 
  
