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
