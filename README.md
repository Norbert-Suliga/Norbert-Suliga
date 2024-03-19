For this challenge you need to create a simple HAVING statement, you want to count how many people have the same age and return the groups with 10 or more people who have that age.

SELECT age, COUNT(*) AS total_people
FROM people
GROUP BY age
HAVING COUNT(*) >= 10;

------------------------------------------------------------------------------

For this challenge you need to create a simple GROUP BY statement, you want to group all the people by their age and count the people who have the same age.

SELECT age, COUNT(*) AS people_count
FROM people
GROUP BY age;

--------------------------------------------------------------------------------

For this challenge you need to create a SELECT statement, this SELECT statement will use an IN to check whether a department has had a sale with a price over 98.00 dollars.

SELECT id, name
FROM departments
WHERE id IN (
    SELECT department_id
    FROM sales
    WHERE price > 98.00
);

-----------------------------------------------------------------------------------

For this challenge you need to create a SELECT statement, this SELECT statement will use an IN to check whether a department has had a sale with a price over 90.00 dollars BUT the sql MUST use the WITH statement which will be used to select all columns from sales where the price is greater than 90.00, you must call this sub-query special_sales.

WITH special_sales AS (
    SELECT *
    FROM sales
    WHERE price > 90.00
)
SELECT d.id, d.name
FROM departments d
WHERE d.id IN (
    SELECT department_id
    FROM special_sales
);

------------------------------------------------------------------------------------

Using our monsters table with the following schema:
monsters table schema
id
name
legs
arms
characteristics
return the following table:
** output schema**
name
characteristics
Where the name is the original string repeated three times (do not add any spaces), and the characteristics are the original strings in reverse (e.g. 'abc, def, ghi' becomes 'ihg ,fed ,cba').

SELECT 
    CONCAT(name, name, name) AS name,
    REVERSE(characteristics) AS characteristics
FROM 
    monsters;

------------------------------------------------------------------------------------

In this kata you should simply determine, whether a given year is a leap year or not. In case you don't know the rules, here they are:
Years divisible by 4 are leap years,
but years divisible by 100 are not leap years,
but years divisible by 400 are leap years.
Tested years are in range 1600 ≤ year ≤ 4000.

select
  year,
  case
    when year%400=0 then true
    when year%100=0 then false
    when year%4=0 then true
    else false
  end as is_leap
from years
order by year; 

----------------------------------------------------------------------------------

Complete the solution so that it returns true if the first argument(string) passed in ends with the 2nd argument (also a string).

function solution(string, ending) {
    return string.endsWith(ending);
}
// Test cases
console.log(solution('abc', 'bc'));  // returns true
console.log(solution('abc', 'd'));   // returns false

-------------------------------------------------------------------------------------

In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

function filter_list(list) {
    return list.filter(item => typeof item === 'number');
}

// Test cases
console.log(filter_list([1, 2, 'a', 'b'])); // [1, 2]
console.log(filter_list([1, 'a', 'b', 0, 15])); // [1, 0, 15]
console.log(filter_list([1, 2, 'aasf', '1', '123', 123])); // [1, 2, 123]

-------------------------------------------------------------------------------------

Welcome.
In this kata you are required to, given a string, replace every letter with its position in the alphabet.
If anything in the text isn't a letter, ignore it and don't return it.
"a" = 1, "b" = 2, etc.

function alphabetPosition(text) {
    const alphabet = 'abcdefghijklmnopqrstuvwxyz';
    return text.toLowerCase()
               .split('')
               .filter(char => alphabet.includes(char))
               .map(char => alphabet.indexOf(char) + 1)
               .join(' ');
}

// Test case
console.log(alphabetPosition("The sunset sets at twelve o' clock."));
// Output: "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"

----------------------------------------------------------------------------------------

Make a program that filters a list of strings and returns a list with only your friends name in it.
If a name has exactly 4 letters in it, you can be sure that it has to be a friend of yours! Otherwise, you can be sure he's not...
Ex: Input = ["Ryan", "Kieran", "Jason", "Yous"], Output = ["Ryan", "Yous"]
i.e.
friend ["Ryan", "Kieran", "Mark"] `shouldBe` ["Ryan", "Mark"]


function friend(names) {
    return names.filter(name => name.length === 4);
}

// Test case
console.log(friend(["Ryan", "Kieran", "Jason", "Yous"])); // Output: ["Ryan", "Yous"]
