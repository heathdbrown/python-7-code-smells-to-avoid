# python-7-code-smells-to-avoid
> Youtube video from ArjanCodes explaining Code Smells for Python and coming from the Refactoring book by Martin Fowler

Video: https://www.youtube.com/watch?v=LrtnLEkOwFE&list=TLPQMTQwNzIwMjE9-kfIcaaTIA&index=3
Code from Video: https://github.com/ArjanCodes/2021-code-smells

Book: https://martinfowler.com/books/refactoring.html

## Overivew
1. Imprecise Types
2. Duplicate Code
3. Not using available built-in functions
4. Vague identifiers
5. Using isinstance to separate behavior
6. Using boolean flags to make a method do 2 different things
7. Catching and then ignoring exceptions
8. Not Using custom exceptions

### Imprecise Types

Instead of using a generic type like 'str' which can be anything using something line 'enum' to set a value or a pre-defined set of values is better to keep from having failures with random values.

Example:
  - role = 'vice preseident'

```python
from enum import Enum, auto

class Role(Enum):
   PRESIDENT = auto()

@dataclass
class Employee:
  role: Role #changes from str to Role instance

```

### Duplicate Codes
Get rid of functions or methods or areas that you will have to edit multiple times to fix bugs.

Basically, do not repeat yourself (DRY).

### Not using available built-in functions
Not using list comprehensions to reduce and clearly show what is happening

Exmample:

```python
def find_employees(self, role: Role) -> List[Employee]:

  return [employee for employee in self.employee.role is role] ! list comprehension from nested if statements and creating a new list and then passing it back.
```

### Vague Identifiers
Don't use vague names to identify items

amount becomes hours_worked: here we are changing amount from the 'amount of hours' to the item and the unit. 'hours_worked'

### Using isinstance to seperate behavior

Isinstance points to issues with not thinking through the speration you need.

https://youtu.be/LrtnLEkOwFE?list=TLPQMTQwNzIwMjE9-kfIcaaTIA&t=734

once you add pay into each class then add the pay method as an 'abstract method' and Employee the becomes an abstract class. (need to look this up to understand better)

### Using boolean flags to make a method do 2 different things
By using a parameter that is a boolean you have mad the method do 2 things instead of only 1 item.

Fix this by splitting the method into two:
- take_a_holiday
- pay_out_a_holiday

### Catching and then ignoring exceptions
Don't ignore exceptions with useless try/except blocks, do something with the Exception

If you want to catch exceptions catch the specific exception and do something not the generic exceptions.

### Not Using custom exceptions

Don't use the built-in error instead use a custom error to catch it properly and do something with it.
