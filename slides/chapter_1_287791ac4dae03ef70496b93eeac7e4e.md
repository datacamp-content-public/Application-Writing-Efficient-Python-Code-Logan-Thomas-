---
title: Insert title here
key: 287791ac4dae03ef70496b93eeac7e4e
video_link:
  mp3: test2.mp3

---
## I Feel the Need...

```yaml
type: "TitleSlide"
key: "49d13c7500"
assignment: "The Need for Speed"
```

`@lower_third`

name: Logan Thomas
title: Senior Data Scientist - Nielsen


`@script`
- As mentioned in the previous section, part of writing efficient Python code means writing code that executes quickly.

- In this lesson, we will learn how to test the runtime of our code.

- Understanding the runtime for a given block of code is an important feature when thinking about efficiency. 

- Comparing runtimes between two code bases that do the same thing allows us to pick the code with the optimal performance.

- By gathering and analyizing runtimes, we can be sure to implement the code that is fastest and thus more efficient.


---
## How can we time our code?

```yaml
type: "FullSlide"
key: "4141a4e178"
disable_transition: false
center_content: false
```

`@part1`
- We could write our own timer...

      import datetime as dt
      import numpy as np

      # set start time
      start = dt.datetime.now()

      # Do something
      rand_numbs = np.random.rand(1000000)

      # Calculate runtime (now - start)
      run_time = dt.datetime.now() - start

      print('run time: {}'.format(run_time))


- But this seems verbose, clunky, and inefficient...


`@script`
- In order to compare runtimes, we first need a way to compute the run time for a line or number of lines of code

_ We could do this using a simple approach with the datetime module

- We would set the start date as the current time before executing a line of code.

- We would then execute our line of code (here selecting 1 mil random numbers between 0 and 1)

- Then, we would calculate the run time as the current time after executing our code minus what the start time was before executing our code

- We print the run time in order to see how long selecting 1 mil random numbers took.

- Although this is one way to time a specific line of code, we can see that this would quickly become verbose and clunky.

- We would need to set multiple start and end times to calculate run times for different pieces of our code.

- There has to be a better way...


---
## How can we time our code (efficiently)?

```yaml
type: "FullSlide"
key: "8164cc28e0"
```

`@part1`
- Calculate runtime with iPython magic command **%timeit**

- **Magic commands** are enhancements added on top of the normal Python syntax
  - Prefixed by the "%" character
  - Link to docs ([here](https://ipython.readthedocs.io/en/stable/interactive/magics.html))
  - See all avaiable magic commands with `%lsmagic`


`@script`
- Luckily for us, iPython comes with some handy built it magic commands that we can use to time our code

- Magic commands are enhancements that have been added on top of the normal Python syntax.

- These commands are prefixed with the percentage sign

- If you aren't familiar with magic commands, take a moment to review the documentation using the provided link.

- To see a list of all magic command available to us, use %lsmagic to list all magic commands.

- We will focus only on the %timeit magic command moving forward, but it is helpful to know what magic commands are at your disposal.


---
## Intro to %timeit

```yaml
type: "FullSlide"
key: "9e83557fec"
```

`@part1`
Old, ineffieceint timer
      # set start time
      start = dt.datetime.now()

      # Do something
      rand_numbs = np.random.rand(1000000)

      # Calculate runtime (now - start)
      run_time = dt.datetime.now() - start

      print('run time: {}'.format(run_time))

Now becomes

      %timeit rand_numbs = np.random.rand(1000000)


`@script`
- Now that we know we have a %timeit magic command in our toolbelt, how do we use it.

- Consider the previous example where we wrote our own timer to get the runtime for selecting 1 mil random numbers between 0 and 1.

- Instead of setting up a start time and calculating  the run time on our own, the magic command %timeit allows us to provide the single line of code we want to time.

- That's it! One line of code using the magic command %timeit allows to calculate the run time without developing any additional code.

- Magic indeed!


---
## Output of %timeit

```yaml
type: "FullSlide"
key: "28f20e20e6"
```

`@part1`
- %timeit gives additional information beyond one timer run
        In [1]: %timeit rand_numbs = np.random.rand(1000000)
        Out[1]: 12.7 ms ± 1.15 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)
    - 12.7 ms mean 
    - 1.15 ms standard deviation
    - 7 runs (with 100 loops each run)


`@script`
- The magic command %timeit not only allows us to time specific lines of code quickly, it also provides additional information that we weren't getting with our old inefficient timer.

- Notice that the output of %timeit provides some useful information

- First, we see that a mean and standard deviation of time is provided

- We also see that multiple runs and loops were generated

- This is another advantage of using the magic command %timeit.

- %timeit will not just run through the provided code once like our old inefficeint timer did.

- Instead, %timeit will run through the provided code multiple times and provided an average and standard deviation for the runtime of the code.

- This helps us get a more accurate representation of the actual runtime rather than relying on just one iteration of the code as we did in the past.


---
## Functionality of %timeit

```yaml
type: "FullSlide"
key: "604f223d7e"
```

`@part1`
- %timeit provides functionality for setting the number of runs and/or loops
        # Set number of runs to 1; number of loops to 10
        In [1]: %timeit -r1 -n10 rand_numbs = np.random.rand(1000000)
        Out[1]: 13.4 ms ± 0 ns per loop (mean ± std. dev. of 1 run, 10 loops each)
        
- %timeit can be run on a single line or multiple lines of code
        # Single line (line magic)
        %timeit l = [x for x in range(10)] 
        
        # Multi line (cell magic)
        %%timeit
        l = []
        for x in range(10):
            l.append(x)


`@script`
- %timeit doesn't just give us more information about the runtime of a given code block, it also gives us some handy functionality as well.

- We can specify the number of runs using the -r flag and the number of loops using the -n flag.

- We can also run %timeit on a single line of code (called line magic) using one Percentage sign, or, we can run %timeit on multiple lines of code (called cell magic) using two Percentage sings.

- Most of the time we will be wrapping multiple lines of code in a function, but it is helpful to note that %timeit can handle single or multiple lines of code


---
## Saving %timeit Output

```yaml
type: "FullSlide"
key: "0d2d88d034"
```

`@part1`
- %timeit also allows us to save the output as a variable

        a = %timeit -o rand_numbs = np.random.rand(1000000)

- This allows us to dig deeper into the execution times of each run
    - a.all_runs
    - a.average 
    - a.best
    - a.worst


`@script`
- Another great functionality of the magic command %timeit, is the ability to save output as a variable

- We do this by using the -o flag

- This allows us to save the output of one %timeit analysis to compare to another.

- It also allows us to dig deeper into the %timeit output for a given analysis

- We can use the .all_runs method to see the average time across loops for each run

- We can use methods like .average to see the average time across all runs

- We can use the method .best and .worst to see the best and worst times across the runs within a %timeit analysis.

- Take a look at the methods available by storing a %timeit analysis as the variable a and typing 
a.[TAB]


---
## Using %timeit to compare

```yaml
type: "FullSlide"
key: "04753d2c90"
```

`@part1`
- Saving the output from two %timeit analyses makes it easy to compare
            def make_list_a():
                return [x for x in range(1000)]

            def make_list_b():
                l = []
                for x in range(1000):
                    l.append(x)
                return l

           In [1]: a_time = %timeit -o make_list_a()
           Out[1]: 37.9 µs ± 1.16 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)

           In [2]: b_time = %timeit -o make_list_b()
           Out[2]: 93.1 µs ± 8.34 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)

           In [3]: improvement = (a_time.average - b_time.average)/b_time.average * -100
                  print('Run time improvement: {:.2f}%'.format(improvement))
           Out[3]: Run time improvement: 59.31%


`@script`
- Now that we know how to use the %timeit magic command and how to store its output, we can begin comparing results

- Suppose you have two functions that do the exact same thing (in this case build a list of integers from 0 to 999).

- make_list_a() uses a list comprehension to build the integer list

- make_list_b() uses a for loop to loop over the integers and adds each integer to a list

- We can to see which of these implementations is faster and more efficient

- We can compare the two functions using the %timeit magic command

- Here we see that the list comprehension method (make_list_a) is a much better implementation.


---
## Orders of Time

```yaml
type: "FullSlide"
key: "c4c5da1108"
```

`@part1`
- Reference for orders of magnitude (fastest at top)

| symbol |        name | unit (s) | 
|--------|-------------|----------|
|     ns |  nanosecond |  10^(-9) |
|     µs | microsecond |  10^(-6) |
|     ms | millisecond |  10^(-3) |
|      s |      second |   10^(0) |


`@script`
- For convenience, a table to time orders of magnitude is provided here

- The table is ordered from fastest at the top to slowest at the bottom. 

- Feel free to reference this table when comparing %timeit analyses


---
## Off to the Races!

```yaml
type: "FinalSlide"
key: "31cb057257"
```

`@script`
- Now that we know how to use the magic command %timeit, we can compare different codes bases in order to select the one that is most efficient

- In the following exercises, you will practice timing different lines of code and selecting which implementations are best based on runtime

- It's off the to races. Enjoy.

