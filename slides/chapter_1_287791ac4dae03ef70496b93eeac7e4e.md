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
## Insert title here...

```yaml
type: "FullSlide"
key: "604f223d7e"
```

`@part1`
time it with %%
time it with -n, -r, -o


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "31cb057257"
```

`@script`


