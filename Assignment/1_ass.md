
# Largest element of a list

## The problem
Find the largest element of a list.

## Hints
Take the first element as the largest number. Then loop through the list and compare each element.
 

## Solution
```python
def get_largest(nums):
   largest = nums[0]
   for num in nums:
       if num > largest:
           largest = num
   return largest
 
my_nums = [0,15,68,1,0,-55]
 
largest = get_largest(my_nums)
 
print('The largest number is: ', largest)
```

## Explanation
In the beginning, consider the first element of the list as the largest element. 

Don’t set the largest value to 0. If every number in the list is a negative number, your return will be wrong. 

Then just loop through the list and compare. If the current number is greater than the largest number, set it as the largest number. 

That’s it. Easy peasy. 

## Shortcut
One shortcut is to  pass a list of numbers to the max function. This will return the largest number in the list.

```python
nums = [41, 69, 23, 45, 19, 8]

largest = max(nums)
print(largest)
```


