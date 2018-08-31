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
  - Can operate on a single line of code using one '%' character and on multiple lines of code using two '%' characters
  - Link to docs ([here](https://ipython.readthedocs.io/en/stable/interactive/magics.html))

        %timeit np.random.rand(1000000)
        %%timeit


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "31cb057257"
```

`@script`


