---
title: Insert title here
key: 287791ac4dae03ef70496b93eeac7e4e

---
## I Feel the Need...<br>
The Need For Speed

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
ignsign


---
## %timeit intro

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



---
## %timeit output

```yaml
type: "FullSlide"
key: "28f20e20e6"
```

`@part1`
- %timeit gives additional information beyond one timer run
        %timeit rand_numbs = np.random.rand(1000000)
        12.7 ms ± 1.15 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)
    - 12.7 ms mean 
    - 1.15 ms standard deviation
    - 7 runs (with 100 loops each run)


`@script`



---
## %timeit functionality

```yaml
type: "FullSlide"
key: "604f223d7e"
```

`@part1`
- %timeit provides functionality for setting the number of runs and/or loops
        # Set number of runs to 1; number of loops to 10
        %timeit -r1 -n10 rand_numbs = np.random.rand(1000000)
        13.4 ms ± 0 ns per loop (mean ± std. dev. of 1 run, 10 loops each)
        
- %timeit can be run on a single line or multiple lines of code
        # Single line (line magic)
        %timeit l = [x for x in range(10)] 
        
        # Multi line (cell magic)
        %%timeit
        l = []
        for x in range(10):
            l.append(x)


`@script`



---
## saving %timeit output

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

           a_time = %timeit -o make_list_a()
           37.9 µs ± 1.16 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)

           b_time = %timeit -o make_list_b()
           93.1 µs ± 8.34 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)

           improvement = (a_time.average - b_time.average)/b_time.average * -100
           print('Run time improvement: {:.2f}%'.format(improvement))
           Run time improvement: 59.31%


`@script`



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

