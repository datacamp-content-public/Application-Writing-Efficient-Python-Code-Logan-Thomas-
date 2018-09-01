---
title: Insert title here
key: c809b53dd88a8fbe0d9c61398fb6efa1

---
## I Feel the Need...The Need for Speed!

```yaml
type: "TitleSlide"
key: "9f032d2725"
assignment: "The Need for Speed!"
```

`@lower_third`

name: Logan Thomas
title: Senior Data Scientist - Nielsen


`@script`
- Hi, I'm Logan Thomas a Senior Data Scientist at Nielsen.

- In this lesson, we will learn how to test the run time of our code

- As mentioned in the previous section, runtime is an important consideration when thinking about efficiency.

- Comparing run times between two code bases that effectively do the same thing allows us to pick the code with the optimal performance

- By gathering and analyzing runtimes, we can be sure to implement the code that is fastest and thus more efficient


---
## How can we time our code?

```yaml
type: "FullSlide"
key: "6d0c8b03e2"
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

- We could do this using a simple approach with the datetime module

- We set the start time as the current time before executing a line of code.

- We would then execute our line of code to be tested (here selecting 1 mil random numbers between 0 and 1)

- Then, we would calculate the run time as the current time after executing our code minus what the start time was before executing our code

- We then print the run time to see how long our code took.

- Although this is one way to time a specific line of code, we can see that this would quickly become verbose and clunky.

- We would need to set multiple start and end times to calculate run times for different pieces of our code.

- There has to be a better way...


---
## How can we time our code (efficiently)?

```yaml
type: "FullSlide"
key: "680195e261"
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

- If you aren't familiar with magic commands, don't worry, take a moment to review the documentation using the provided link.

- We will focus only on the %timeit magic command moving forward, but it is helpful to know what magic commands are at your disposal.


---
## %timeit to the rescue

```yaml
type: "FullSlide"
key: "4dad699894"
```

`@part1`
Old, inefficient timer
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
- Consider the previous example where we wrote our own timer to get the runtime for selecting 1 mil random numbers between 0 and 1.

- Instead of calculating the run time on our own, the %timeit command allows us to provide a single line of code we want to time.

- That's it! One line of code using the magic command %timeit allows to calculate the run time without developing any additional code.

- Magic indeed!


---
## %timeit output

```yaml
type: "FullSlide"
key: "a12f7bca3a"
center_content: true
```

`@part1`
- `%timeit` gives additional information
      In [1]: %timeit rand_numbs = np.random.rand(1000000)
      Out[1]: 12.7 ms ± 1.15 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)
    - 12.7 ms mean, 1.15 ms standard deviation, 7 runs (with 100 loops each run)
- Order of Time Reference

| symbol |        name | unit (s) | 
|--------|-------------|----------|
|     ns |  nanosecond |  10^(-9) |
|     µs | microsecond |  10^(-6) |
|     ms | millisecond |  10^(-3) |
|      s |      second |   10^(0) |


`@script`
- %timeit provides additional information that we weren't getting with our old inefficient timer.

- First, we see that a mean and standard deviation of time is provided

- We also see that multiple runs and loops were generated

- This is another advantage of using the magic command %timeit.

- %timeit will run through the provided code multiple times and provided an average and standard deviation across runs to calculate the runtime of our code.

- This helps us get a more accurate representation of the actual runtime rather than relying on just one iteration of the code as we did in the past.


---
## %timeit functionality

```yaml
type: "FullSlide"
key: "4d19ac90ae"
```

`@part1`
- `%timeit` provides functionality for setting the number of runs and/or loops
      # Set number of runs to 1 (-r1); number of loops to 10 (-n10)
      In [1]: %timeit -r1 -n10 rand_numbs = np.random.rand(1000000)
      Out[1]: 13.4 ms ± 0 ns per loop (mean ± std. dev. of 1 run, 10 loops each)
        
- `%timeit` can be run on a single line or multiple lines of code
      # Single line (line magic)
      %timeit l = [x for x in range(10)] 
        
      # Multi line (cell magic)
      %%timeit
      l = []
      for x in range(10):
          l.append(x)


`@script`
- %timeit gives us some handy functionality as well.

- We can specify the number of runs using the -r flag and the number of loops using the -n flags seen here.

- We can also run %timeit on a single line of code (called line magic) using one Percentage sign, or, we can run %timeit on multiple lines of code (called cell magic) using two Percentage sings.

- Most of the time we will be wrapping multiple lines of code in a function, but it is helpful to note that %timeit can handle single or multiple lines of code


---
## Saving %timeit Output

```yaml
type: "FullSlide"
key: "2ddefa2c61"
```

`@part1`
- `%timeit` also allows us to save the output as a variable
      a = %timeit -o rand_numbs = np.random.rand(1000000)

- This allows us to dig deeper into the `%timeit` output
    - a.all_runs
    - a.average 
    - a.best
    - a.worst


`@script`
- Another great functionality of the magic command %timeit, is the ability to save output as a variable

- We do this by using the -o flag

- This allows us to save the output of one %timeit analysis to compare to another.

- We can also dig deeper into the %timeit output for a given analysis when we save the output

- We can use methods like .best and .worst to see the best and worst times across the runs within a %timeit analysis.


---
## Using %timeit to compare

```yaml
type: "FullSlide"
key: "736d92160f"
center_content: false
```

`@part1`
- Saving the output from two `%timeit` analyses makes it easy to compare
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
- Now we can begin comparing results

- Suppose you have two functions that do the exact same thing (in this case build a list of integers from 0 to 999).

- make_list_a() uses a list comprehension to build the integer list

- make_list_b() uses a for loop to loop over the integers and adds each integer to a list

- We can use %timeit to see which of these implementations is faster and more efficient

- Here we see that the list comprehension method (make_list_a) is a much better implementation.


---
## Off to the Races!

```yaml
type: "FinalSlide"
key: "bbd83e71db"
```

`@script`
- Now we can use %timeit to compare different codes bases in order to select the one that is most efficient. It's Off to the Races!

