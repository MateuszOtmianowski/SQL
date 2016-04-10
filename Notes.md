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
*	adding number to a date, increases day count;
*	substracting to dates results in the number of days between the two;

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
  - **RPAD**('*string*',*number*,'*character*') analogous to the above;
  
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
  - **NVL**(*Expression1*, *Expression2*) if *Expression1* is NULL return *Expression2*, data types must match, useful in arithmetic operations to avoid calculation error;
  - **NVL2**(*Expression1*, *Expression2*, *Expression3*) if *Expression1* is not NULL, return *Expression2*, else return *Expression3*, *Expression1* does not to be of the same type as *Expression2* and *Expression3*, but *Expression2* and *Expression3* must be same data type;
  - **NULLIF**(*Expression1*, *Expression2*) compares both expression, return NULL if they are equal, if not return *Expression1*, could be followe to is NULL to check if given condition is met;
  - **COALESCE**(*Expression1*, *Expression2*,...,*ExpressionX*) returns first expression that is not NULL or the last expression if all previous are NULL;

*	**Conditional Expressions**:
  - **CASE** *Expression1* WHEN *comparison_expression1* then *return_expression1*
  [WHEN *comparison_expression2* then *return_expression2*
  WHEN *comparison_expressionN* then *return_expressionN*
  ELSE *else_expr*]

