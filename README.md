# Computational Thinking For Problem Solving (UPenn Engineering Online Learning)

## 4 pillars of computational thinking:
- Decomposition (taking a complex problem and breaking it into more manageable sub-problems)
- Pattern Recognition (after decomposing we'll find common patterns amongst sub-problems - good for desired repetitive tasks for several identical data in any area in life)
- Data Representation and Abstraction (determining what inputs of problem are important)
- Algorithms (step by step instructions on how to solve the problem and this course uses flowchart for instructions but ill be using pseudocode)   

algorithm cross_street()
  look to the right
  look to the left
    if car coming
      do not cross
    else
      cross
    return

## Common Algorithms
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

1.2) The solution was:

algorithm find_largest()
get input list
  if input empty
    stop
read the first item in list and store it in "max" variable
if for item in list, item>max  
  max = item
  if item is untested (1st item in list as 1st time being picked)
    read next untested item
    go back to "if for item in list, item>max"
  else
    return max
    stop
else
  go back to "if item is untested (1st item in list as 1st time being picked)" line

1.3) extra: now find the smallest value

algorithm find_smallest()

   
   
   
