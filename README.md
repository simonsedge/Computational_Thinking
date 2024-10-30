# Computational Thinking For Problem Solving (UPenn Engineering Online Learning)



## 4 pillars of computational thinking:
- Decomposition (taking a complex problem and breaking it into more manageable sub-problems)
- Pattern Recognition (after decomposing we'll find common patterns amongst sub-problems - good for desired repetitive tasks for several identical data in any area in life)
- Data Representation and Abstraction (determining what inputs of problem are important)
- Algorithms (step by step instructions on how to solve the problem and this course uses flowchart for instructions but ill be translating that to pseudocode)   

algorithm cross_street()
  look to the right
  look to the left
    if car coming
      do not cross
    else
      cross
    return

## Common Algorithms pt.1 (unordered Largest/smallet value)
exs:

1) There's a list of values and you want to create an algorithm that returns the largest value in that list:

1.1) My first idea was:

algorithm find_largest()
  set index0 of list to max_so_far variable # the current max recorded as list is iterated
  iterate the next value
  compare new_value and max_so_far
  if
    new_value>max_so_far
    max_so_far=new_value
  go back to "iterate the next value"
  return max_so_far

1.2) My flowchart-to-pseudocode solution was interpreted like:

algorithm find_largest()
get input list
  if input empty
    stop
read the first item in list and store it in "max" variable
if for item in list, item>max  
  max = item
  are there any other items in the list?
    read next untested item
    go back to "if for item in list, item>max"
  else
    return max
    stop
else
  go back to "are there any other values in the list?" line

1.3) Chatgpt's solution for pseudocode was:
checks if the list is empty first. If not, it sets the first item as the initial maximum, then iterates through the remaining items to update the maximum as needed, finally outputting the largest value in the list.

Algorithm Find_Max()
    Input: list
    If list is empty then
        Output: "N/A"
        Stop
    End If
    
    Read first item in list and store value in max

    While there is an untested item in list
        Read next untested item
        If item > max then
            Store item in max
        End If
    End While

    Output: max
    Stop
End Algorithm


1.3) extra: now find the smallest value

algorithm find_smallest()
get list
  if list empty
  stop
min = [0]list
if for item in list, item<min:
  min = item
  are there any other items in the list?
    read next item
    go back to "if for item in list, item<min:" line
  else
    return min
    stop
else
    go back to "are there any other items in the list?" line

## Common Algorithms pt.2 (unordered Linear Search - does a collection contain a value?)
exs:

1) determine whether a list of values contains a target value:

1.1) My first idea was:
algorithm_linear_search()
have a data point defining target_value
iterate list 1-by-1 or if data is better structured create a better algo to see if item==target_value

1.2) My flowchart-to-pseudocode translation was interpreted like:
algorithm_linear_search()
get input list
has this current item in list been compared to target_value?
if yes
  read next item in list
  if item == target
    return "true"
    stop
  else
    go back to "is there another item?" line
else
  return "false"
  stop

1.3) Chatgpt's Solution to Flowchart was:
i mean it's in the wording itself. it literally just compares each item to a target and only spits out something if there's a match. so it's basically a loop of comparisson against the same value and if nothing comes out as a match then it's a false.

Algorithm Linear_Search()
    Input: list, target_value
    While there is an untested item in list (only doesnt work for 1st value if list is empty)
        Read next item in list (this is the item i was considering in the previous line)
        If item == target_value then
            Output: true
            Stop
        End If
    End While
    Output: false
    Stop
End Algorithm

## Common Algorithms pt.3 (Algorithmic complexity - how long will algo take to execute if input increases?)

Complexity is just an expression of the number of operations in an algorithm.

You tend to focus on the worst case scenario, so i need an answer as to what the worst case scenario is 

Going back to the algorithm find_largest, we made n-1 comparisons with n == # of items and it would always maintain no matter the linear operation performed on n - this means the # of comparissons is roughly the same as number of elements so the algorithm has linear complexity

Going back to the algotithm linear_search, regardless of whether there's a match or not, no matter item/target_value position, n size is irrelevant as algo stops when finds a match. but worst case scenario it doesnt find a match which should be worse than finding a match at last - therefore also linear complexity (no shit name of algo was linear search) as worst case scenario is n operations.

## Common Algorithms pt.4 (Binary Search - how long will algo take to execute if input increases?)

Here ordering lists is introduced to create better algos, therefore turning linear search into binary search in regards to most efficient algo

Since binary search is dividing by 2 as many times needed and worst case scenario is no match for maximum number of operations, this means it has y=log2(x) logarithmic complexity with y = number of comparisons/operations in worst case scenario and x the number of items in a list

exs:

1) determine whether a sorted list of values contains a target value

1.1) my first thought:
algorithm_binary_search()
get sorted list
loop break list in half with 1 pointer at one item
if pointer==target, return true
if pointer>target
  remove pointer and any value above it from the searchable list
if pointer<target
  remove pointer and any value below it from the searchable list

1.2) interpretation of flowchart
i actually got it right but there's other ways to write it like chatgpt

1.3) chatgpt interpretation of flowchart:
This pseudocode continuously checks the middle element of the list. If it matches the target, it outputs true and stops. Otherwise, it eliminates either the first or last half of the list based on whether the middle element is less than or greater than the target. If the list becomes empty without finding the target, it outputs false.

Algorithm Binary_Search()
    Input: list, target_value

    While list is not empty
        Read middle item, mid
        If mid == target_value then
            Output: true
            Stop
        End If

        If mid < target_value then
            Eliminate mid and first half of list
        Else
            Eliminate mid and last half of list
        End If
    End While

    Output: false
    Stop
End Algorithm
