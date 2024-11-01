# Computational Thinking For Problem Solving (University of Pennsylvania Engineering Online Learning)

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

1.4) Actual solution was:
algorithm find_largest()
  input: list_collection
  output: max_so_far_value
max_so_far_value = list_collection[0]
for item in list_collection:
  if item > max_so_far_value:
    max_so_far_value = item
output max_so_far
stop

1.5) extra: now find the smallest value

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

1.4) Actual solution as seen in 3.5
algorithm linear_search
  inputs: list_collection, target_value
  output: true if match, false if not
for item in list_collection:
  if item=target
  then output: true
    stop
output: false


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

## Common Algorithms pt.5 (Brute Force)

In this example brute force had an exponential complexity of 2^n since for each meeting of the group of meetings was either apart of the solution or not

Worst way to employ brute force is when permutations (order) matters like a djiskra type algo for shortest multi path since all # possibilities == n! so this is actually named factorial complexity

A few years ago, I taught a class with eight teaching assistants and I wanted to meet all of them once a week. I know the students are busy and it would be hard to get all of us together in the same place at a reasonable time of day. So, I gave them five options for meeting times as you see here, and then I wanted to choose some combination of meeting times so that I could meet each TA at least once during the week, even if it meant having multiple meetings. So, an algorithm we could use here is to use brute force to find all possible combinations of the five meeting times and then identify those combinations where I can meet all TA's and then optimize it by finding the combination with the smallest number of meetings because I'm busy too. So, how many possible solutions are there? To determine the number of possible solutions using brute force, we can look at each potential meeting time and say that we either will or will not include it in the solution. For example, from Monday 4:00 PM, I either do or do not have a meeting at that time. So, there are two options for Monday 4:00 PM because I either do or do not include it in the solution. Likewise for Tuesday 6:00 PM, I either do or do not include it in the combination of meeting times. So, there are two options for it as well and so on. Now let's look at the combinations of options like we did for the museum example starting with just the first two times. One combination is to have meetings at both Monday 4:00 PM and Tuesday 6:00 PM. That is, I can include both in my solution. Another combination is to have a meeting on Monday at 4:00 PM but not Tuesday 6:00 PM, that's part of another solution. The third combination is to not meet on Monday at 4:00 PM, but to meet Tuesday at six, that's yet another solution. The fourth combination of these two times is to not have meetings at either time. So, you see again that we're just multiplying the number of options. For each of the five meeting times, we either do or do not include it. 

## Common Algorithms pt.6 (Greedy Algorithms)

A simple approach that doesn't always give the best algorithm solution but it's close to optimal in much less time. Contrary to brute force, you make a decision that seems best currently (just the mental translation of "you gotta start somewhere" and you eye-scan the best option to start with) and keep repeating the same decision until done. So in a way greedy algorithms are better for human use vs computer use to get a somewhat right answer with a large input size.

So let's assume i got a daily schedule full of classes and some breaks. I want to solve the problem of my laptop battery going dead, therefore i need to charge it during class breaks. but i want to charge it as few times as possible. instead of looking at all possible breaks and going brute force thinking "i either charge or not charge per every break", a greedy algorithm that only charges right after or before battery going dead for the first time and repeating for next times might very well be the optimal solution.

## Case Studies

The centre problem had 27 groups requesting meetings and they wanted to meet as many as possible.
1st decompose into subproblems determining which group to meet and when to remove conflicting requests
2nd through pattern recognition realise that the loop is to look at requests and choosing the best one (we ended up choosing the one with the earliest starting time or ending time ex. even if meeting A starts at 8:00 am, meeting B can have prevailance over meeting B if meeting B ends before meeting A)
3rd through data representation and abstraction meeting requests are represented using start and end times
4th through algorithms choose a request to schedule and remove conflicting requests and repeat until done

The pseudocode for this can be found in 3.5

This was chatgpt's attempt at it: 

Algorithm Scheduling()
    Input: Collection of all requests

    If collection is empty then
        Output: schedule
        Stop
    End If

    Set earliest_request to first request in collection

    While there are more requests in collection
        Look at next request
        If end time of next request is before end time of earliest_request then
            Set next request as earliest_request
        End If
    End While

    Add earliest_request to schedule

    While there are more requests in collection
        Look at next request
        If start time of next request is before end time of earliest_request then
            Remove next request from collection
        End If
    End While

    Repeat process with remaining requests

    Output: schedule
    Stop
End Algorithm


In regards to complexity, even though both loops, individually, are linear, you have an inner loop within a outter loop so if you increase input size you'll have to do twice as many things, twice as many times == quadratic/n^2 complexity as 2x inputs results in 4x as many operations

Then the dog center problem.
1st decompose subproblems: determine similarity, find 3 most similar dogs, do a majority vote for disaster search and rescue suitability prediction
2nd pattern recognition: repeated process of calculating similarity for each dog using each individual test result
3rd data representation and abstraction: dogs are represented as test results, as well as whether they are suitable for disaster search and rescue
4th algorithm: calculate similarity for each dog, find 3 max similarity values between a pair of dogs, count number of similar dogs that are suitable for disaster search and rescue via creating some logic around quantifying the qualitative aspects of the problem

The pseudocode for this can be found in 3.5

This was chatgpt's attempt at it:

Algorithm Prediction()
    Input: collection of dogs, new_dog

    While there are more dogs in collection
        Calculate similarity between this dog and new_dog
    End While

    Repeat 3 times
        Set most_similar_dog to first dog in collection
        
        While there are more dogs in collection
            Look at next dog
            If this dog is more similar to new_dog than most_similar_dog then
                Set this dog as most_similar_dog
            End If
        End While
        
        Add most_similar_dog to list of similar dogs
        Remove most_similar_dog from collection
    End Repeat

    Set vote to 0

    For each dog in list of similar dogs
        If dog is suitable for Search & Rescue (S&R) then
            Increment vote
        End If
    End For

    If vote >= 2 then
        Output: "suitable"
    Else
        Output: "not suitable"
    End If

    Stop
End Algorithm

This is actually a popular machine-learning algorithm known as K-Nearest Neighbors. For some value of k, which is usually odd like three in this case, we find the most similar or nearest elements for which we already know some piece of info and use that to predict the info for some new elements.

So, what's the complexity of this algorithm? This algorithm consists of three parts, calculating the similarity of each dog, finding the three most similar dogs and conducting the vote. The first part is definitely linear. We do the calculation once for each dog. If there are twice as many dogs, it takes twice as many steps. The second part is also linear. In finding the most similar dog, we look at each dog in the list once. If we had twice as many dogs, we'd need to do twice as many comparisons. Now, you might say "Wait, isn't this quadratic like the scheduling algorithm, since we have the loop within a loop?" But, it doesn't matter that we go through the list three or five or a hundred times, because it's independent of the number of dogs. So, it's linear overall. If we doubled the number of dogs, we only double the number of steps. Conducting the vote is also linear. In the worst case, if we were doing a vote over all the dogs, then we'd have to look at each dog's value and that's linear. Since all parts of the prediction algorithm are linear, the algorithm as a whole is also linear. Because again, if for instance, we doubled the number of inputs, we have to do all the parts twice as many times. So overall, we just have twice as many total operations, which means it's linear.

Finishing thoughts by the professor: When I was a graduate student, I taught an introduction to computer science class, and our textbook defined computer science as the study of algorithms. But, you don't have to be a computer scientist to think algorithmically or to use algorithms. As we've seen in this part of the course, there are lots of common algorithms and patterns among them. There are some basic algorithmic approaches that can be used in solving lots of different problems. Once we've used computational thinking and developed an algorithm, the next step is to express the algorithm to a computer. In order to do that, we need to know the language that the computer understands. But, in order to do that, we first need to know what the computer is capable of doing. That's what we'll see in the next part of the course.

# von Neumann architecture

Modern computing is done under this architecture where CPU instructions and data is stored separatly in RAM memory in an address.

Memory (RAM): Stores both program instructions and data. Memory is organized in bytes, with each byte being eight bits (binary digits), where each bit represents a value of either 0 or 1. The CPU accesses memory by unique addresses to either write or read data. Smaller data types like letters are stored in one byte, while larger numbers use multiple bytes (e.g., 2, 4, or 8 bytes).

CPU (Central Processing Unit): Executes program instructions, composed of:

Control Unit: Fetches, decodes, executes instructions, and moves to the next one, following a repetitive cycle. It uses registers (temporary memory) to store operands and results temporarily.
Arithmetic and Logic Unit (ALU): Handles basic math and logical operations, such as addition and comparison. These simple operations can be combined to implement complex algorithms.
Input/Output (I/O): Facilitates interaction between the computer and external devices (e.g., keyboard, mouse, monitor). Devices send signals (interrupts) to notify the CPU when they have data, and the CPU signals them when it has data to display or process.

Programming Basics: Writing a program is expressing an algorithm in a way the computer can understand. A program manipulates data, running an algorithm on that data, which is stored in memory at a specific address.

Memory Addresses and Variables:Modern computers automatically manage memory addresses, so programmers use variables (labels or names) to represent memory addresses.
This abstraction lets programmers focus on the data without needing to know its specific memory location, similar to using the label “Empire State Building” instead of knowing the actual address.

Types of Variables:
- Single Value Variables: Variables like count store individual values, such as a number or letter.
- Collections (Arrays): Variables can hold multiple values in contiguous memory locations, allowing for easy sequential access.
  - Example: values is a collection, where each element can be accessed by its index (e.g., values[2] for the third element in a zero-based index system).

Indexing in Collections:
- Many languages use zero-based indexing, where the first element has index 0.
- Indexing enables direct access to specific elements within a collection.

Objects: Objects allow grouping of values under a single name, with distinct labels for each attribute.
Example: A dog object named Jake might include properties like age and weight. The entire grouping is the object, but each property has its own label within that object.

Practical Use of Variables: Variables simplify memory operations by allowing read and write operations based on labels rather than actual memory addresses.
For example, assigning count = 0 writes 0 to memory at the address corresponding to count, determined by the CPU, not the programmer.

Now how does the control unit execute instructions within a program and provide conditional and iterative control for program flow?

Control Unit's Role in Execution:
- The control unit performs a repetitive four-step cycle: fetch, decode, execute, update, and then repeat.
- In simple cases, the control unit moves from one instruction to the next sequentially in memory. For instance, to add two numbers and store the result, the control unit fetches each number, sends them to the ALU (Arithmetic and Logic Unit) for addition, and writes the result to memory, then moves to the next instruction.

Conditional Execution:
- Conditional execution allows the program to perform one instruction in certain cases and a different one in others, an essential capability for flexible programming.
- This structure is often visualized in a flowchart and is handled by the control unit through an if-then-else construct. For example, the control unit may execute an instruction to compare values and, based on the result (true or false), direct the program to follow one of two possible instructions.
- In programming, these conditions are expressed as if-then-else or nested as if-then-elseif to handle more complex decision-making.

Loops and Iteration:
- Loops allow repeated execution of instructions until a specified condition is met. This flow is crucial for algorithms that require iteration.
- The loop checks a condition after each cycle; if true, the program returns to a previous instruction to repeat the steps. Once the condition evaluates to false, the loop exits, and the program continues with the subsequent instructions.

Programming Constructs:
- If-Then-Else Construct: Executes different instructions based on a condition.
- If-Then-ElseIf: A more complex version that checks multiple conditions in sequence.
- Loops: Used for repeated instruction execution based on a condition.

Application in Algorithms: With conditional and iterative control, the control unit's abilities align with foundational algorithmic structures. This knowledge prepares students to think about programming and algorithms in terms of conditions and repetitions, essential for writing efficient and logical code.

# Expressing algorithms in pseudocode

exs:

1) understand the pseudocode below:
stop ← number of items in list - 2
for each item in list
    for i in range 0 ... stop
		    if list[i] > list[i+1]
		    then
			    temp ← list[i]
			    list[i] ← list[i+1]
			    list[i+1] ← temp
output: list

Here is an explanation of the solution:

As the hint suggests, let’s create a simple input list with values {4, 2, 3, 1} and see what happens on each step.

1: stop is set to the number of items in list - 2, which is 4 - 2 = 2

2: we start looping and set item to the first element of the list, which is 4

3: we have another loop with i set to 0

4: we see if list[0] > list[1], which sees if 4 > 2, which is true

6: the variable temp holds list[0], which is 4

7: list[0] is set to list[1], which is 2, which means our list now contains {2, 2, 3, 1}

8: list[1] is set to temp, which is 4, so our list is now {2, 4, 3, 1}

3: we continue with the inner loop, with i now set to 1

4: we see if list[1] > list[2], which sees if 4 > 3, which is true

6: the variable temp holds list[1], which is 4

7: list[1] is set to list[2], which is 3, so now the list is {2, 3, 3, 1}

8: list[2] is set to temp, which is 4, so the list becomes {2, 3, 4, 1}

3: we continue the inner loop, with i now set to 2; note that because stop is 2, this is the last time we will execute this inner loop

4: we see if list[2] > list[3], which sees if 4 > 1, which is true

6: temp holds list[2], which is 4

7: list[2] is set to list[3], so the list is now {2, 3, 1, 1}

8: list[3] is set to temp, which is 4, so the list becomes {2, 3, 1, 4}

At this point it may be possible to speculate what this algorithm does after just one pass through the outer loop, but let’s do the outer loop one more time just to check. 

Let’s simplify things a bit, though, and note that lines 6-8 simply switch the values of list[i] and list[i+1]; we won’t walk through all three of those steps as we continue the example.

Now that we’ve completed the inner loop, we continue the outer loop, keeping in mind that list is now {2, 3, 1, 4}:

2: we continue looping and set item to the next element of the list, which is 3; note that item is not actually used anywhere other than line 2. All this does is ensure that the loop on lines 3-8 is executed the same number of times as there are items in the list.

3: we restart the inner loop with i set to 0

4: we see if list[0] > list[1], which sees if 2 > 3, which is false, so we do not execute lines 6-8

3: we continue with the inner loop, with i now set to 1

4: we see if list[1] > list[2], which sees if 3 > 1, which is true

6-8: we swap list[1] and list[2], so the list now becomes {2, 1, 3, 4}

3: we continue the inner loop, with i now set to 2

4: we see if list[2] > list[3], which sees if 3 > 4, which is false, so we do not execute lines 6-8, and because i reached the value of stop, we are done with the inner loop

Now the list is {2, 1, 3, 4}. Can you see what is happening? Let’s try one more:

2: we continue looping for the third time

3: we restart the inner loop with i set to 0

4: we see if list[0] > list[1], which sees if 2 > 1, which is true

6-8: we swap list[0] and list[1], so the list is now {1, 2, 3, 4}

3: we continue looping with i set to 1

4: we see if list[1] > list[2], which sees if 2 > 3, which is false

3: we continue looping with i set to 2

4: we see if list[2] > list[3], which sees if 3 > 4, which is false

Now we’re done with the inner loop and the list is {1, 2, 3, 4}. We do have one more iteration of the outer loop to perform, but we’ll stop here because perhaps you see what’s happening: as we go through the inner loop, bigger numbers are being swapped with neighboring smaller numbers so that the bigger numbers are moving to the right. Each time we do the outer loop, the biggest number moves all the way to the right, up until it hits the numbers that are bigger than it. The result is that the numbers end up in sorted order.

So the point of this algorithm is to sort a list in ascending order. It will, however, most likely do unnecessary operations to achieve that. Let's try an initial list [23, -345, 243, 0, 0, -40, 50]. So stop, the number of times the inner loop will run for each list item, equals 7-2=5. For the outer loop, in the 1st iteration it would set i=0, compare index 0 with index 1 (23 and -345) and since 23>-345 it swaps them and the current list becomes [-345, 23, 243, 0, 0, -40, 50]. Then do the same until i=5 where the current list after 1st outer loop iteration will be [-345, 23, 0, 0, -40, 50, 243]. Then repeat this until the 7th outer loop iteration is done where the current list will be [-345, -40, 0, 0, 23, 50, 243] - a fully ascending sorted list by comparing each element to the next one and swapping them if need be

This algorithm is known as bubble sort and is one of the simplest algorithms for sorting elements in a list. It is called bubble sort because on each iteration of the outer loop, the largest value “bubbles” its way to the top (or to the right), until it reaches its place in the sorted list.

Although bubble sort is simple to implement, it is very inefficient and exhibits quadratic complexity, meaning that an input of N elements would require around N^2 operations, and that doubling the input’s size would require four times as many operations. The most efficient sorting algorithms, such as merge sort and quick sort, require NlogN operations, which are much fewer than N^2 for large values of N, but are more complicated to implement.

# Case studies

Back to the center problem. Solution to it was:

algorithm centre_meetings
  inputs: requests_collection (elements with start and end times)
  output: scheduled_requests the full schedule that contains requests that don't overlap
while requests is not empty
  #find request to schedule using the greedy approach earlier in which we choose the meeting request with the earliest ending time. so this code is just going through the collection requests and finding the minimum value
  earliest_start_time = requests_collection[0]
  earliest_end_time = requests_collection[0].end_time (earliest end time to be the end time of the first request)
  for each request in requests_collection
    if request.end_time < earliest_end_time (if end time is less than the earliest end time we've seen so far)
    then
      earliest_request = request (update earliest request)
      earliest_end_time = request.end_time (and update earliest end time)
  add earliest_request to scheduled_requests (we now know earliest request represents the one with the earliest ending time and we add it to our collection which we'll use for holding the output)
      
  #remove any requests that cannot be scheduled
  for each request in requests (inner loop all the requests)
    if request.start_time < earliest_request.end_time
    then remove request from requests

Now back to the dog rescue problem. Solution was:

algorithm dog_rescue
  inputs: dogs_collection (elements that have values for catwalk_test, surface_test, conflict_test, suitable, and similarity to the new dog), and new_dog (same 3 elements but does not have similarity and suitable values)
  outputs: majority value of suitable for the 3 elements in dogs that have the highest similarity values - a prediction of whether new dog will be suitable for search and rescue. take the 3 dogs with highest similarity, then take the majority value for their suitable values

#calculate similarity for each dog
for each dog in dogs_collection
  dogs.similarity = 0
  if dog.catwalk_test = new_dog.catwalk_test
  then dog.similarity = dog.similarity + 1
  if dog.surface_test = new_dog.surface_test
  then dog.similarity = dog.similarity + 1
  if dog.conflict_test = new_dog.conflict_test
  then dog-similarity = dog.similarity + 1
  
#find 3 most similar dogs - This is very similar to the algorithm we saw on previous part of the course in which we look for the largest value in a collection, and it's also similar to the scheduling algorithm we just saw, except that that one was looking for the smallest value. Because we're looking for the three highest values, we'll repeat these steps three times.

loop 3x
  most_similar_dog = dogs[0] (lets say the most similar dog so far is the first iteration)
  highest_similarity = dogs[0].similarity (and lets assume the highest similarity so far is the first iteration)
  for each dog in dogs:
    if dog.similarity > highest_similarity
    then
      highest_similarity = dog.similarity (update highest_similarity variable by assigning the similarity of the iterated dog)
      most_similar_dog = dog (update most_similar_dog variable by assigning the iterated dog)
  add most_similar_dog to similar_dogs (add the most similar dog to a collection called similar_dogs)
  remove most_similar_dog from dogs (remove the recently added most similar dog from the list of all the other potential)

#find majority value for 3 most similar dogs - do a vote based on whether they were suitable for disaster search and rescue
vote = 0
for each dog in similar_dogs (iterate over the 3 dogs)
  if dog.suitable = true
  then vote = vote + 1
if vote ≥ 2 (since there are 3 dogs a majority would be 2 or more)
then output: true (the new dog is suitable for at least 2 of the most similar dogs)
else output: false

# Introduction to Programming with Python

Programming is really only the last step after you do computational thinking, design the architecture/software, etc. It's simply the act of expressing an algorithm using syntax that computer can compile.

It starts by analysing a basic algo and asking what it does:
{
values = []
count = 0
for value in values:
	if value>0:
 		count = count + 1
print(count)
}

So it takes a list, initializes variable count (stupid name could just name it positive_numbers) to 0, then in a loop for every value in the list if value>0, update the count variable to ++1. after iterating all values (when loop ends), print the count.

Then mentions some obvious stuff, good note that variables should not include uppercase letters. Stuff like print("string ", c) will print out a constant string with a variable. Stuff like how a syntax error is like writing "dog red arrive pavement" when you don't use the right words (prant("...") or incorrect use) and/or order (5=age) and/or missing data . Or stuff like runtime errors when code is expressed using valid syntax but computer cannot evaluate it like typeError when trying to assign an invalid sum of 2 different types of data to a variable. Or like when you haven't initialized variables or ZeroDivision error. And reminds you that python will stop after 1st error so only 1 error shown in compiler even if many even in the same line

Some mentions on operators (** for power, // for integer_quotient which rounds to nearest whole number so 2.5 or 2.9 becomes 2, % for modulus as in the quotient which is the difference between numerator and closest integer multiplication to numerator without going past it).
Also, reminder that python prioritizes **, then *, then +; And you use parenthesis to prioritise.
Then some mention on comparison operators ==, != or <>, >= and how maths characteristics are always based off that like "is A divisible by B" is just a % b == 0
Also some mention of how elif should be used instead of else (just the notion that elif should be used if i want to include the intersection of previous if statement and the new "else" statement. an else would probably be a larger set which would be just the opposite of the initial if)

Then on lists he just says that a list is nothing more than a collection of integers/strings/floats assigned to a collection of variables, and that whole pack is assigned to a variable
- you use it because you can perform operations with the data without having to declare new variables like
	- list.append("...") to add to end of list
	- list.insert(3, "...") to allocate index 3 in the list to the element i want to insert
	- list.remove("...") to remove 1st instance of that value from the list (in case of duplicates) - and the fact that when you remove an element, indexes above slide to the left
	- list.pop(3) to remove element in index position 3
- on indices it's list[0] for example and if counting from the end index it doesn't start at 0 but at -1 instead, then -2, -3, ...
	- to add an element to the end it's always append and not insert(-1) as that's the second to last place therefore shifting every element after that to the right
- another note on runtime index error when i try to use an index that is out of range for the list
- another note on runtime error value error when i try to remove a value that is not in the list
	- if i wanted to check if there's a value before removing it or protect against index errors, instead of writing a greedy algo going 1 by 1 until match like in "unordered Search", python has nice syntax:
 		- if "corgi" in list:
   			... (like list.remove("corgi"))

it also makes some points on safeguarding against indexerrors via instead of writing var = list.pop(i) you write if len(list)>i: \ var = list.pop(i), therefore guaranteeing it doesnt give a runtime error

there's an exercise where you had some initial code and had to create the logic. the only interesting point was about swapping 1st and last values and how ridiculously stupid it is that could need to do 4 steps for that. so in that sense although the program would work nonetheless, its extremely inneficient for the seemingly simple task to write it like:

  list.append(list[0]) # O(1)
  list.pop(0) # O(n) because it shifts all elements to the left
  list.insert(0, list[-2]) # O(n) because it shifts all elements to the right
  list.pop(-2) # O(>1) because it still needs to shift last element to the right

instead i could either:

- do tuple unpacking which is a O(1) operation as no elements need to be reshuffled in memory: values[0], values[-1] = values[-1], values[0]
- using a temporary variable which is what they have done in that exercise that tripped me up with the ascending sorting algorithm. This is also 0(1).
	temp = values[0]     # Store the first element in a temporary variable
	values[0] = values[-1]  # Move the last element to the first position
	values[-1] = temp       # Set the last position to the original first element

they mention the basic count = count + 1 is the same as count += 1 (not ++1 this does not exist in python) and how indentation is necessary in for/if/while/... statements

they also mention how you can do nested for-loops like:
names1 = []
names2 = []
common_names = []
for name1 in names1: # imagine an outer circular loop being formed englobing the inner circular loop below - it will stay in first name1 and loop all name2's before iterating the 2nd pass of names1
	for name2 in names2:
 		if name1 == name 2 and name1 not in common_names: #another good tip, didn't know i could use "and" and "not in"
   			common_names.append(name1)
print(common_names)

and how i can understand debugging better if i print what's happening before and after any conditional statements like print("comparing ", name1, " to ", name2) before and in the same indent as the if statement in the previous code and print("adding ", name1, " to common_names") after the if statement inside it (indented)

nested for loops are great for iterating all elements but sometimes we want to access elements by their indices while in a loop and we need some counter index that increments on each iteration. example: determine if list is sorted in increasing order

ages = []
is_sorted = True # whether or not its sorted (initialize as True, assuming the list is sorted until we find otherwise.)
for i in range(1, len(ages)):
	if ages[i] <= ages[i-1]:
 		is_sorted = False
   		break
if is_sorted:
	print("the list is sorted")
else:
	print("the list is not sorted")

An explanation on why to use the boolean initialization is found here

ages = [1, 3, 2]  # Example list

#Initializing `is_sorted = True` is a common technique when you want to assume something is true until proven otherwise.
#Starting Assumption:
#By initializing `is_sorted` to True, you’re assuming the list is sorted from the start.
#As you loop through the list, you check each element pair.
#If you find any pair that’s out of order, you set `is_sorted = False` and break out of the loop.
is_sorted = True

for i in range(1, len(ages)):
    #Why Initialize to True Instead of False?
    #If you initialized `is_sorted` to False, it would imply the list is unsorted from the beginning.
    #Then, you would need extra logic to set it to True only if every pair satisfies the sorted condition, which complicates the code.
    #By starting with True, you only need to change it to False if you find a single unsorted pair.
    #This approach allows you to detect an unsorted list early and exit the loop as soon as the list is confirmed to be unsorted,
    #making the code more efficient.
    
    if ages[i] < ages[i - 1]:  # Check if the current element is less than the previous one
        is_sorted = False  # List is not sorted, so we set `is_sorted` to False
        break

#Minimal Initialization:
#Setting `is_sorted = True` is the simplest, most efficient way to initialize this variable for the given logic.
#It avoids the need for extra checks or a more complicated setup.

#Example Walkthrough
#Imagine you have a list [1, 3, 2]:
#- `is_sorted` starts as True.
#- You check 1 <= 3 (okay) and move on.
#- Then you check 3 <= 2 (not okay). Here, you set `is_sorted = False` and break out of the loop, knowing the list isn’t sorted.

#Key Takeaway:
#Initializing `is_sorted = True` sets up a default assumption that simplifies the logic.
#You only need to change it if you find evidence to the contrary, which makes the code cleaner and more efficient.

#After the loop, we check if `is_sorted` is still True
if is_sorted:
    print("The list is sorted")
else:
    print("The list is not sorted")

in regards to while loops: for loops are good when we know in advance how many times we want to run the loop. but while loops are good for when we only know the condition for the loop to occur and when condition changes, loop breaks:

things like making sure the user inserts a valid input like "while number<=0: \ print("that number is not positive") \ value = input("please enter a positive number: ") \ number=int(value)
this number = int(value) is a very interesting function where int converts the string input in value = input("please enter a positive number: ") and converts it to a integer.

then i mean for nearly every algorithm i want there's already a function in python that does it:
- like finding the largest value algorithm, in reality its just: max(values)
- like finding the target value, in reality its just: if target_value in list: \ print("list contains target_value")

Now in regards to functions, sometimes we want to keep reusing some algorithm without writing it multiple times (doesn't alter complexity though for the same program, although it improves maintenance and runtime efficiency) or separate the code just so it's easier for humans to read. this is known in other programming languages as a subroutine/proceadure/method but in python we call it a function - takes arguments and we'll call the return value. It's really nothing new, it's just the separation of code i already have.

You first define it by specifying name, parameters, and body. then you can invoke it in the code by specifying input arguments and assigning variables to hold outputs:
def calculate_hypotenuse(a,b):
	return (aa+bb)**0.5
x, y = 3, 4 #btw if i had called these "a" and "b", because it's not inside indented, or in other words, out of scope, these variables would be different than the variables inside the function. so it's just a reading nightmare but technically speaking its alright. so printing "a" would output 3 in this case instead of an out-of-scope "x" value serving as argument for calling the function like c = calculate_hypotenuse(100, ...) where you could expect 100 to be printed when printing "a"
c = calculate_hypotenuse(x,y)
print(c)

Instead of writing the algo for the determination if list is sorted, i could define a function and then easily call it with new lists as arguments:
{
def is_increasing(my_list):
	is_sorted = True
 	for i in range(1, len(my_list)):
  		if my_list[i-1] >= my_list[i]:
    			is_sorted = False
       			break
       	return is_sorted
}
ages = [int1, int2, ...]
names = [string1, string2, ...] 
print(is_increasing(ages)) prints obvious answer
print(is_increasing(names)) prints true if list has ascending alphabetical order

But more interesting is the fact you can have a function return multiple values like when say extracting the 3 largest values:
{
def three_largest(input_list):
	list_copy = input_list.copy() #great practise to not modify original	
	max_value1 = max(list_copy)
	list_copy.remove(max_value1) #don't double count
	...
	max_value3 = max(list_copy)
	return (max_value1, max_value2, max_value3) # in order to return them all together as a single output of this function you put the data in a tuple - a temporary collection of values that we use when we want a function to return more than 1 thing. the question to whether why not a list instead is technical and stylistical. first off, stylistically, python code should only return a list when the thing it's returning is supposed to be a list and not a workaround as a way of returning multiple things. From a technical point of view if we return a list, the code that called our function could add or remove elements which may or may not be what we want, so tuples cannot have elements added or removed. and as a side note, tuples do not imply that the elements belong together as part of a collection
}
numbers = [4, 5, 1, 2, 8, 9, .3]
first, second, third = three_largest(numbers) #we use the variables to hold the three return values that were grouped together into the tuple

Now moving on to classes and objects:
if you want to still store several elements in a single variable like a list but want to have a different name for each element within that collection.
A dog named Jake is a collection of entities or attributes such as age, weight, breed, complexion, ... so each element has its own name. You don't use a list cuz a list is easier to accidentally transform data and there's no way to know the properties should go together in the analysis if i just use a list and dont name each element.
For this situation its better to use an object - a named collection of variables or attributes that each have their own individual names as well. Before we use the object, we need to define the blueprint for the object, also known as a class:

{
class Cat: #class names start with capital letters, we have not created the object yet at this point
	def_init_(self, init_name, init_age, init_color): #the init function is a special function called the constructor and it's called when we create (the first)/(a new) cat object - that is, a new instance of the cat class. the first parameter is always self, meaning "this object", and then have the other parameters i think i'll need to create the cat
 		#initializing the object's attributes, the "self." notation means that this variable is an attribute that is part of this object
   		self.name = init_name
   		self.age = init_age
     		self.color = init_color
}
var_1 = Cat("james", 3, "grey") #this is an object - you're creating a new cat variable and invoking its constructr or its init function - an instance of the cat class
var_2 = Cat("agnes", 4, "black") #another object
print(james.color)
agnes.age = 5 (overrides the previous age to become this age inside the var_2 cat object)

Now another important point is a class not only has attributes but can have its own operations or functions as well:

class Cat:
	def _init_(self, init_name):
 		self.name = init_name
   		self.friends = [] #empty list but question i have is: if this is another attribute why not also write it inside the _init_?
     	def add_friends(self, new_friend): #just a regular function they created to allow adding a friend to the friends empty list. you gotta use self to indicate that it's this cat
      		if new_friend not in self.friends: #self.friends is a list and it means each cat class/object has its own list of friends
			self.friends.append(new_friend)
james = Cat("james")
agnes = Cat("agnes")
james.add_friend(agnes)
for friend in james.friends:
	print(friend.name) #since we know those friends are cats, we know they have name attributes, so we can print like this

Now lets say you want to find the cat with the youngest age. Should you write the algo or use in-built python functions to find a minimum? Well usually you'd try to never write them myself but this is slightly different because we're not looking for the "minimum cat", we're looking for the "minimum age" associated with a cat. Therefore i could write:
{
def youngest_cat(cats): #cats is a list with many elements
	youngest = cats[0] #way to define cats here is by a list of elements or the object's name
 	youngest_age = cats[0].age #initializing that the age of the youngest cat iterated at that point is that cat's age
  	for cat in cats: #iterate over all the cats in the list and call each one "cat"
   		if cat.age < youngest_age:
			youngest = cat
   			youngest_age = cat.age
      	return youngest
}
james = Cat("james", 3, "grey")
...
...
...
my_cats = [james, agnes, sally, snowy] #the youngest_cat function takes a list as its input
print("Youngest is ", youngest_cat(my_cats).name)

## Back to the case studies, but now in python

The centre meetings problem:
#represents a meeting request
class Request:
	def _init_(self, input_name, input_start, input_end):
 		self.name = input_name
   		self.start = input_start
     		self.end = input_end
#create requests
r1 = Request("A", 0, 3)
...
r7 = Request["G", 7, 9)
requests = [r1, ..., r7]

scheduled_requests = [] #initialize empty list to schedule requests
while len(requests)>0: #we don't use for loop cuz we don't know how many times we will run the loop
	#schedule the one with earliest ending time
 	earliest = requests[0]
  	earliest_end = requests[0].end
   	for request in requests:
    		if request.end < earliest_end:
      			earliest = request
	 		earliest_end = request.end #we know that earliest is the request with the earliest ending time
    	print("schedulling ", earliest.name) #just so we can check which request is being scheduled and then below add it to the list of scheduled requests
     	scheduled_requests.append(earliest)

      	#remove all the requests with start time before that ending time unscheduled 
       	unscheduled = list(requests) #make copy of the requests list because if we didn't the code would be looping over the elements of the request list but also simultaneously removing elements from that list
	for request in requests:
 		if request.start < earliest.end: #overlapping requests
   			unscheduled.remove(request)
      	requests = unscheduled
#now scheduled_requests hold all scheduled requests
      	

The dogs disaster search and rescue problem:
#this class represnets a dog
class Dog:
	def _init_(self, input_test1, input_test2, input_test3, input_suitable = None): #meaning a dog is represented as a full result of these 3 elements and the None is used for when we know there's a variable but we don't know its values so unless we assign it a value when calling it, it serves no purpose
 		self.catwalk_test = input_test1
   		self.surface_test = intput_test2
     		self.conflict_test = input_test3
       		self.suitable = input_suitable
#create some dogs
all_dogs = []
all_dogs.append(Dog(True, Flase, True, True))
all_dogs.append(Dog(False, False, True, False))
all_dogs.append(Dog(True, True, True, True))
all_dogs.append(Dog(True, Flase, True, False))

new_dog = Dog(True, False, False) #you don't specifcy the 4th element like before becase that element is what you're trying to assess so you don't know anything about it yet, it's just something that will be used in the future when i do know

#determine similarity to all other dogs
for dog in all_dogs:
	dog.similarity = 0 #assign a similarity attribute that wasn't added in the class or object when i created it - this is a feature in python that can do it even outside class/object
 	if dog.catwalk_test == new_dog.catwalk_test:
  		dog.similarity += 1
    	if dog.surface_test == new_dog.surface_test:
     		dog.similarity += 1
       	if dog.confliect_test == new.dog.conflict_test:
		dog.similarity += 1

#find 3 most similar dogs
similar_dogs = []
#loop 3 times
for i in range(3): #produces a list containing 0, 1, and 2 and will do the loop 1x for each of those 3 values
	most_similar_dog = all_dogs[0]
 	max_similarity = all_dogs[0].similarity
  	for dog in all_dogs:
   		if dog.similarity > max_similarity:
     			max_similarity = dog.similarity
			most_similar_dog = dog
   	similar_dogs.append(most_similar_dog)
    	all_dogs.remove(most_similar_dog)
vote = 0
for dog in similar_dogs:
	if dog.suitable:
 		vote += 1
if vote >= 2 :
	print("prediction: suitable!")
else:
	print("prediction: not suitable")
