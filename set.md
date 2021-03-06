# set
### Introduction
- A set is a programming data structure where the order of the objects inside does not matter because there can only be one of each piece of data without any duplicates. This means that the position of a data piece in the set can be determined by the information contained in the data piece. For example, if a set contained the numbers 1,4,7,5,3,12,15 it would look something like {1,-,3,4,5,-,7,-,-,-,-,12,-,-,15}. While this method means that you can't have any duplicates, it makes it very easy to find if a set contains a certain piece of data, you just need to go to the place where that data piece would be stored and see if it is there. The technique that allows a data piece to be stored in one index and one index only is called hashing.

### hashing sets
- The most basic hash function is index(n) = n. This function will cause the data to be stored in the location index that equals it. For example, 1 will be stored in index 1, 2 will be stored in index 2, 3 will be stored in index 3, and so on.  The problem with this function is that if you want to store a small number of very large numbers such as 1743, 1438, 3958, and 4853, you would need a set with thousands of spaces for just four number, resulting in a lot of wasted space. One method of reducing the required memory is to use the modulus (%) operator in the hash function. The modulus operator divides the first number by the second (X % Y) and returns the remainder. For example, 22 / 5 is 4 with a remainder of 2, so 22 % 5 = 2.  
- If your hash function is index(n) = n % y where y is equal to the size of the set, the data will be placed at the index equal to the modulus, and thanks to how rounding works, it’s impossible for the index to be outside the set, preventing overflow problems.

### addressing conflicts from hashing
- There is one problem with using modulus in the hash function. It’s possible for two different numbers to have the same modulus, and thus would be placed in the same index. When this happens, it is called a conflict. There are two methods of dealing with a conflict. The first is called open addressing, and the second is called chaining.
- Open addressing works by when you try to put something into an index space and find something already there, we simply place the data in the next available spot. The problem with this method is that it can generate more conflicts when you try to put a new number in the set.
- Chaining is when each index space doesn’t contain just one piece of data, instead it contains a list that contains the data that can go in the index space.
- The problem with these methods of resolving conflict is that they slow the function down. The reason to use a set at all is because it has an O(1) performance, where finding a particular piece of data always takes the same amount of time regardless of how big the set is. When you have conflicts or a chained list, the function becomes less and less efficient until after a certain point, you would be better off making a new, larger set and copying everything into that set.

### example problem: combining two different sets
``` python
def combine_set(set1,set2)
set3 = set() 
for number in set1:
  set3.add(number)
for number in set2:
  set3.add(number)
  return set3
```
### practice problem
- implement a function that looks through two sets and returns any duplicates between them
- see solution [here](https://github.com/PaulMDecker/cse212final-project/blob/main/set-solution.py)
### set syntax

set Operation  |  description  | code                 | Big O Performance
---------------|---------------|----------------------|----------------
add(value) | Adds "value to the set | my_set.add(value) | O(1) - Performance of hashing the value (assuming good conflict resolution) 
| remove(value) | Removes the "value" from the set | my_set.remove(value) | O(1) - Performance of hashing the value (assuming good conflict resolution) | 
member(value) | Determines if "value" is in the set | if value in my_set: | O(1) - Performance of hashing the value (assuming good conflict resolution) | 
size() | Returns the number of items in the set | length = len(my_set) | O(1) - Performance of returning the size of the set| 




















