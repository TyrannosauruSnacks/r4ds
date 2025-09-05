
<!-- rnb-text-begin -->

---
title: "R for data science - 13 Numbers"
output: html_notebook
editor_options: 
  chunk_output_type: inline
---

Load libraries


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeSh0aWR5dmVyc2UpXG5gYGAifQ== -->

```r
library(tidyverse)
```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoi4pSA4pSAIEF0dGFjaGluZyBjb3JlIHRpZHl2ZXJzZSBwYWNrYWdlcyDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIAgdGlkeXZlcnNlIDIuMC4wIOKUgOKUgFxu4pyUIGRwbHlyICAgICAxLjEuNCAgICAg4pyUIHJlYWRyICAgICAyLjEuNVxu4pyUIGZvcmNhdHMgICAxLjAuMCAgICAg4pyUIHN0cmluZ3IgICAxLjUuMVxu4pyUIGdncGxvdDIgICAzLjUuMSAgICAg4pyUIHRpYmJsZSAgICAzLjIuMVxu4pyUIGx1YnJpZGF0ZSAxLjkuMyAgICAg4pyUIHRpZHlyICAgICAxLjMuMVxu4pyUIHB1cnJyICAgICAxLjAuMiAgICAg4pSA4pSAIENvbmZsaWN0cyDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIDilIAgdGlkeXZlcnNlX2NvbmZsaWN0cygpIOKUgOKUgFxu4pyWIGRwbHlyOjpmaWx0ZXIoKSBtYXNrcyBzdGF0czo6ZmlsdGVyKClcbuKcliBkcGx5cjo6bGFnKCkgICAgbWFza3Mgc3RhdHM6OmxhZygpXG7ihLkgVXNlIHRoZSBcdTAwMWJdODs7aHR0cDovL2NvbmZsaWN0ZWQuci1saWIub3JnL1x1MDAwN2NvbmZsaWN0ZWQgcGFja2FnZVx1MDAxYl04OztcdTAwMDcgdG8gZm9yY2UgYWxsIGNvbmZsaWN0cyB0byBiZWNvbWUgZXJyb3JzXG4ifQ== -->

```
── Attaching core tidyverse packages ─────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.3     ✔ tidyr     1.3.1
✔ purrr     1.0.2     ── Conflicts ───────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the ]8;;http://conflicted.r-lib.org/conflicted package]8;; to force all conflicts to become errors
```



<!-- rnb-output-end -->

<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeShueWNmbGlnaHRzMjMpXG5gYGAifQ== -->

```r
library(nycflights23)
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


# 13.2 Making Numbers

parse

:   change data type, e.g. from string to double

`parse_double()` for numbers written as strings


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxueCA8LSBjKFwiMS4yXCIsIFwiNS42XCIsIFwiMWUzXCIpXG5cbnBhcnNlX2RvdWJsZSh4KVxuXG5gYGAifQ== -->

```r
x <- c("1.2", "5.6", "1e3")

parse_double(x)

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`parse_number()` to ignore everything but numerics


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxueCA8LSBjKFwiJDEsMjM0XCIsIFwiVVNEIDMsNTEzXCIsIFwiNTklXCIpXG5wYXJzZV9udW1iZXIoeClcblxuYGBgIn0= -->

```r
x <- c("$1,234", "USD 3,513", "59%")
parse_number(x)

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


# 13.3 Counts

count

:   great for quick exploration and check during analysis


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZmxpZ2h0cyB8PiBjb3VudChkZXN0KVxuXG4jIHNvcnQgPSBUUlVFIGZvciBoaWdoIHRvIGxvd1xuZmxpZ2h0cyB8PiBjb3VudChkZXN0LCBzb3J0ID0gVFJVRSlcblxuIyBhbmQgd2hhdCBpJ3ZlIGJlZW4gZG9pbmcgYSBsb3Qgd2FzXG5mbGlnaHRzIHw+IFxuICBncm91cF9ieShkZXN0KSB8PiBcbiAgc3VtbWFyaXplKFxuICAgIG4gPSBuKClcbiAgKVxuXG4jIHdoaWNoIG9ubHkgc3RhcnRzIHRvIGJlIG1vcmUgZWZmaWNpZW50LCB3aGVuIG90aGVyIGNhbGN1bGF0aW9ucyBhcmUgb2YgaW50ZXJlc3RcbmZsaWdodHMgfD4gXG4gIGdyb3VwX2J5KGRlc3QpIHw+IFxuICBzdW1tYXJpemUoXG4gICAgbiA9IG4oKSxcbiAgICBkZWxheSA9IG1lYW4oYXJyX2RlbGF5LCBuYS5ybSA9IFRSVUUpXG4gIClcbmBgYCJ9 -->

```r
flights |> count(dest)

# sort = TRUE for high to low
flights |> count(dest, sort = TRUE)

# and what i've been doing a lot was
flights |> 
  group_by(dest) |> 
  summarize(
    n = n()
  )

# which only starts to be more efficient, when other calculations are of interest
flights |> 
  group_by(dest) |> 
  summarize(
    n = n(),
    delay = mean(arr_delay, na.rm = TRUE)
  )
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`n()` works within dplyr verbs, whereas `count()` is directly applicable.

`n_distinct()` for unique/distinct values of variables


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBob3cgbWFueSBkaWZmZXJlbnQgKGRpc3RpbmN0KSBjYXJyaWVycyBhcmUgdGhlcmUgZm9yIGVhY2ggZGVzdGluYXRpb24gKGdyb3VwX2J5KT9cbmZsaWdodHMgfD4gXG4gIGdyb3VwX2J5KGRlc3QpIHw+IFxuICBzdW1tYXJpc2UoY2FycmllcnMgPSBuX2Rpc3RpbmN0KGNhcnJpZXIpKSB8PiBcbiAgYXJyYW5nZShkZXNjKGNhcnJpZXJzKSlcbmBgYCJ9 -->

```r
# how many different (distinct) carriers are there for each destination (group_by)?
flights |> 
  group_by(dest) |> 
  summarise(carriers = n_distinct(carrier)) |> 
  arrange(desc(carriers))
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`sum()` adds the values of each row(weighted counts), whereas `count()` oder `n()` give the number of rows


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyB0b3RhbCBtaWxlcyBmbGV3bihzdW0pIGJ5IGVhY2ggcGxhbmUgKGdyb3VwX2J5KVxuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkodGFpbG51bSkgfD4gXG4gIHN1bW1hcmlzZShtaWxlcyA9IHN1bShkaXN0YW5jZSkpXG5cbiMgaG93IG9mdGVuIChuKSB0byBob3cgbWFueSBkaWZmZXJlbnQgZGVzdGluYXRpb25zIChuX2Rpc3RpbmN0KSB3ZW50IGVhY2ggcGxhbmUgKGdyb3VwX2J5KVxuZmxpZ2h0cyB8PiBncm91cF9ieSh0YWlsbnVtKSB8PiBcbiAgc3VtbWFyaXNlKGRlc3QgPSBuX2Rpc3RpbmN0KGRlc3QpLCBuID0gbigpKVxuYGBgIn0= -->

```r
# total miles flewn(sum) by each plane (group_by)
flights |> 
  group_by(tailnum) |> 
  summarise(miles = sum(distance))

# how often (n) to how many different destinations (n_distinct) went each plane (group_by)
flights |> group_by(tailnum) |> 
  summarise(dest = n_distinct(dest), n = n())
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`wt` as argument of `counr()` can replace `sum()`.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZmxpZ2h0cyB8PiBjb3VudCh0YWlsbnVtLCB3dCA9IGRpc3RhbmNlKVxuIyBkb2VzIHRoZSBzYW1lIGFzXG5mbGlnaHRzIHw+IFxuICBncm91cF9ieSh0YWlsbnVtKSB8PiBcbiAgc3VtbWFyaXplKG1pbGVhZ2UgPSBzdW0oZGlzdGFuY2UpKVxuIyB3aXRob3V0IHRoZSBsYWJlbCB0aG91Z2hcbmBgYCJ9 -->

```r
flights |> count(tailnum, wt = distance)
# does the same as
flights |> 
  group_by(tailnum) |> 
  summarize(mileage = sum(distance))
# without the label though
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`is.na` as `sum()` argument for counting missing values


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBob3cgbWFueSBmbGlnaHRzIHdpdGggbm8gZGVwYXJ0dXJlIHRpbWUoaXMubmEpIC0gaS5lLiB3ZXJlIGNhbmNlbGxlZCAtIGF0IGVhY2ggZGVzdGluYXRpb24oZ3JvdXBfYnkpP1xuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD4gXG4gIHN1bW1hcml6ZShuX2NhbmNlbGxlZCA9IHN1bShpcy5uYShkZXBfdGltZSkpKVxuYGBgIn0= -->

```r
# how many flights with no departure time(is.na) - i.e. were cancelled - at each destination(group_by)?
flights |> 
  group_by(dest) |> 
  summarize(n_cancelled = sum(is.na(dep_time)))
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.3.1 Exercises

1.  How can you use `count()` to count the number of rows with a missing value for a given variable? use with `is.na()` argument


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBob3cgbWFueShjb3VudCkgZmxpZ2h0cyBoYWQgbm8gZGVwX3RpbWUoaXMubmEpLCBpLmUuIHdlcmUgY2FuY2VsbGVkP1xuZmxpZ2h0cyB8PiBjb3VudChjYW5jZWxsZWQgPSBpcy5uYShkZXBfdGltZSkpXG5cbmBgYCJ9 -->

```r
# how many(count) flights had no dep_time(is.na), i.e. were cancelled?
flights |> count(cancelled = is.na(dep_time))

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


2.  Expand the following calls to `count()` to instead use `group_by()`, `summarize()`, and `arrange()`:
    1.  `flights |> count(dest, sort = TRUE)`


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBob3cgbWFueSBmbGlnaHRzKGNvdW50KSBmb3IgZWFjaCBkZXN0aW5hdGlvbihkZXN0KVxuZmxpZ2h0cyB8PiBjb3VudChkZXN0LCBzb3J0ID0gVFJVRSlcblxuIyBpcyB0aGUgc2FtZSBhc1xuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD4gXG4gIHN1bW1hcml6ZShuID0gbigpKSB8PiBcbiAgYXJyYW5nZShkZXNjKG4pKVxuYGBgIn0= -->

```r
# how many flights(count) for each destination(dest)
flights |> count(dest, sort = TRUE)

# is the same as
flights |> 
  group_by(dest) |> 
  summarize(n = n()) |> 
  arrange(desc(n))
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


2.  `flights |> count(tailnum, wt = distance)`


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBob3cgbWFueSBtaWxlcyAoY291bnQod3QgPSBkaXN0YW5jZSkgaGF0IGVhY2ggcGxhbmUgKHRhaWxudW0pXG5mbGlnaHRzIHw+IFxuICBjb3VudCh0YWlsbnVtLCB3dCA9IGRpc3RhbmNlKVxuXG4jIGlzIHRoZSBzYW1lIGFzIChtaW51cyB0aGUgbGFiZWwpXG5mbGlnaHRzIHw+IFxuICBncm91cF9ieSh0YWlsbnVtKSB8PiBcbiAgc3VtbWFyaXplKG1pbGVhZ2UgPSBzdW0oZGlzdGFuY2UpKVxuYGBgIn0= -->

```r
# how many miles (count(wt = distance) hat each plane (tailnum)
flights |> 
  count(tailnum, wt = distance)

# is the same as (minus the label)
flights |> 
  group_by(tailnum) |> 
  summarize(mileage = sum(distance))
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


# 13.4 Numeric transformations

## 13.4.1 Arithmetic and recycling rules

recycling

:   repeating the calculation with the short vector


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->

    ```r
    x <- c(1, 2, 10, 20)
    
    # now x is a vector of 5 numbers, but the '5' on the other side is a vector of just one, so the shorter vector is recycled on each longer vectors numbers 
    x / 5
    
    ```

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


    Generally you only want to recycle single numbers, but R will recycle any shorter length vector.

`%in%` just looks up if one of the values in the vector matches, whereas `==` recycles? Let's test that.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxueCA8LSBjKDEsMiw3LDk5KVxuXG43ID09IHhcbjcgJWluJSB4XG5gYGAifQ== -->

```r
x <- c(1,2,7,99)

7 == x
7 %in% x
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.4.2 Minimum und Maximum


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZGYgPC0gdHJpYmJsZShcbiAgfngsIH55LCB+eixcbiAgMSwgMywgOSxcbiAgNSwgMiwgNCxcbiAgNywgTkEsIDEyXG4pXG5cbmRmIHw+IFxuICBtdXRhdGUoXG4gICAgbWluID0gcG1pbih4LCB5LCB6LCBuYS5ybSA9IFRSVUUpLFxuICAgIG1heCA9IHBtYXgoeCwgeSwgeiwgbmEucm0gPSBUUlVFKVxuICApXG5gYGAifQ== -->

```r
df <- tribble(
  ~x, ~y, ~z,
  1, 3, 9,
  5, 2, 4,
  7, NA, 12
)

df |> 
  mutate(
    min = pmin(x, y, z, na.rm = TRUE),
    max = pmax(x, y, z, na.rm = TRUE)
  )
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


`min` and `max` give the overall max/min and `pmin` and `pmax` give the max/min for each row, in the case of a data frame.

## 13.4.3 Modular arithmetic

`%%` is a function to give the remainder of a division. `%/%` is the function to give the whole number of a division


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuMToxMCAlLyUgN1xuMToxMCAlJSA3XG5cbiMgZXhhbXBsZTogZ2V0IGggYW5kIG1pbiBmcm9tIEhITU0gdGltZSBmb3JtYXRzXG5mbGlnaHRzIHw+XG4gIHNsaWNlX3NhbXBsZShuID0gMTApIHw+IFxuICBzZWxlY3QoZGVwX3RpbWUpIHw+IFxuICBtdXRhdGUoIGggPSBkZXBfdGltZSAlLyUgMTAwLFxuICAgICAgICAgIG1pbiA9IGRlcF90aW1lICUlIDEwMFxuICApXG5gYGAifQ== -->

```r
1:10 %/% 7
1:10 %% 7

# example: get h and min from HHMM time formats
flights |>
  slice_sample(n = 10) |> 
  select(dep_time) |> 
  mutate( h = dep_time %/% 100,
          min = dep_time %% 100
  )
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.4.4 Logarithms

Use logarithms to visualize scales better, or make them more accessible for human readout. `log()` compresses and `exp()` stretches out.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuMToxNVxueCA8LSBsb2coMToxNSlcbmV4cCh4KVxuXG54IDwtIGxvZzIoMToxNSlcbnhcbjJeeFxuYGBgIn0= -->

```r
1:15
x <- log(1:15)
exp(x)

x <- log2(1:15)
x
2^x
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.4.5 Rounding

## 13.4.6 Breaks

Basic function for binning vectors into different ranges


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxueCA8LSAtNTo1XG54XG5jdXQoeCxcbiAgICBicmVha3MgPSAtMTA6MTBcbiAgICApXG4jIHNhbWUgYXNcbmN1dCh4LFxuICAgIGJyZWFrcyA9IGMoLTEwLCAtOSwgLTgsIC03LCAtNiwgLTUsIC00LCAtMywgLTIsIC0xLCAwLCAxLCAyLCAzLCA1LCA2LCA3LCA4LCA5LCAxMCkpXG5cbiMgc2VlIG4gaW4gYmluc1xudGFibGUoY3V0KHgsXG4gICAgICAgICAgYnJlYWtzID0gLTEwOjEwXG4gICAgICAgICAgKVxuICAgICAgKVxuYGBgIn0= -->

```r
x <- -5:5
x
cut(x,
    breaks = -10:10
    )
# same as
cut(x,
    breaks = c(-10, -9, -8, -7, -6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 5, 6, 7, 8, 9, 10))

# see n in bins
table(cut(x,
          breaks = -10:10
          )
      )
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.4.7 Cumulative and rolling aggregates


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxueCA8LSAxOjEwXG5jdW1zdW0oeClcbmN1bW1lYW4oeClcbmN1bXByb2QoeClcbmBgYCJ9 -->

```r
x <- 1:10
cumsum(x)
cummean(x)
cumprod(x)
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.4.8 Exercises

1.  Explain in words what each line of the code used to generate Figure 13.1 does.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBjaG9vc2UgREYgRmxpZ2h0cyBhcyBEYXRhXG5mbGlnaHRzIHw+XG4gICMgZ3JvdXB5IGJ5IHRoZSBob3VyIG9mIHNjaGVkdWxlZCBkZXBhcnR1cmUgdGltZSAoY3JlYXRlIGhvdXIgY29sdW1uIGJ5IGRpdmlkaW5nIHRoZSBISE1NIHZhbHVlIG9mIHNjaGVkX2RlcF90aW1lIGJ5IDEwMCBhbmQgd3JpdGUgb25seSB3aG9sZSBudW1iZXJzLCBiYXNpY2FsbHkgZXh0cmFjdCB0aGUgZmlyc3QgdHdvIERpZ2l0cyBvZiBhIGZvdXIgZGlnaXQgbnVtYmVyKVxuICBncm91cF9ieShob3VyID0gc2NoZWRfZGVwX3RpbWUgJS8lIDEwMCkgfD4gXG4gICMgYWRkIHRoZSBwcm9wb3J0aW9uIG9mIGNhbmNlbGxlZCBmbGlnaHRzIGZvciBlYWNoIGhvdXIoZ3JvdXApXG4gICMgY2FuY2VsbGVkIGZsaWdodHMgYXJlIGFzc3VtZWQgdG8gYmUgXCJOQVwiIGluIGRlcF90aW1lXG4gICMgY2FsY3VsYXRlIHRoZSBtZWFuIG9mIE5BcyBmb3IgZWFjaCBncm91cFxuICBzdW1tYXJpc2UocHJvcF9jYW5jZWxsZWQgPSBtZWFuKGlzLm5hKGRlcF90aW1lKSksXG4gICAgICAgICAgICBuID0gbigpKSB8PiAgIyBhbmQgc2hvdyB0aGUgdG90YWwgbiBmb3IgZWFjaCBncm91cFxuICAjIGZpbHRlciB0aG9zZSB0aGF0IHNob3VsZCBkZXBhcnQgYWZ0ZXIgMSBhbVxuICBmaWx0ZXIoaG91ciA+IDEpIHw+IFxuICAjIGNyZWF0ZSBhIGdncGxvdCB3aXRoIGhvdXIgb2YgZGVwIChncm91cHMpIG9uIHRoZSB4LWF4aXMgYW5kIHByb3BvcnRpb24gY2FuY2VsbGVkIG9uIHRoZSB5LWF4aXNcbiAgZ2dwbG90KGFlcyh4ID0gaG91ciwgeSA9IHByb3BfY2FuY2VsbGVkKSkgK1xuICAjIGRpc3BsYXkgdGhlIHZhbHVlcyBhcyBhIGxpbmUgd2l0aCBhIG1lZGl1bSBncmV5XG4gIGdlb21fbGluZShjb2xvciA9IFwiZ3JleTUwXCIpICtcbiAgIyBhZGQgdGhlIHZhbHVlcyBhcyBwb2ludHMgd2hvc2Ugc2l6ZXMgcmVwcmVzZW50IHRoZSBuIGluIGVhY2ggZ3JvdXBcbiAgZ2VvbV9wb2ludChhZXMoc2l6ZSA9IG4pKVxuICBcbmBgYCJ9 -->

```r
# choose DF Flights as Data
flights |>
  # groupy by the hour of scheduled departure time (create hour column by dividing the HHMM value of sched_dep_time by 100 and write only whole numbers, basically extract the first two Digits of a four digit number)
  group_by(hour = sched_dep_time %/% 100) |> 
  # add the proportion of cancelled flights for each hour(group)
  # cancelled flights are assumed to be "NA" in dep_time
  # calculate the mean of NAs for each group
  summarise(prop_cancelled = mean(is.na(dep_time)),
            n = n()) |>  # and show the total n for each group
  # filter those that should depart after 1 am
  filter(hour > 1) |> 
  # create a ggplot with hour of dep (groups) on the x-axis and proportion cancelled on the y-axis
  ggplot(aes(x = hour, y = prop_cancelled)) +
  # display the values as a line with a medium grey
  geom_line(color = "grey50") +
  # add the values as points whose sizes represent the n in each group
  geom_point(aes(size = n))
  
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


2.  What trigonometric functions does R provide? Guess some names and look up the documentation. Do they use degrees or radians?

sin, cos, tan, hypo, adj, opp

I guess degrees, as R usually prioritizes pragmatism.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuPz90cmlnb25vbWV0cnlcbmBgYCJ9 -->

```r
??trigonometry
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


Well it's radians, (products of `pi()` as the calculation would be more accurate for an array of arguments, to wait for the calculations with PI till the last possible step.

3.  Currently `dep_time` and `sched_dep_time` are convenient to look at, but hard to compute with because they're not really continuous numbers. You can see the basic problem by running the code below: there's a gap between each hour.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZmxpZ2h0cyB8PiBcbiAgZmlsdGVyKG1vbnRoID09IDEsIGRheSA9PSAxKSB8PiBcbiAgZ2dwbG90KGFlcyh4ID0gc2NoZWRfZGVwX3RpbWUsIHkgPSBkZXBfZGVsYXkpKSArXG4gIGdlb21fcG9pbnQobmEucm0gPSBUUlVFKVxuYGBgIn0= -->

```r
flights |> 
  filter(month == 1, day == 1) |> 
  ggplot(aes(x = sched_dep_time, y = dep_delay)) +
  geom_point(na.rm = TRUE)
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


Convert them to a more truthful representation of time (either fractional hours or minutes since midnight).


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBGcmFjdGlvbmFsIGhvdXJzXG4jIyBNTSB2YWx1ZXMgLyA2MCA9IGZyYWN0aW9uYWwgSG91cnNcblxuIyB0YWtlIHRlc3QgdmFsdWVcbnggPC0gMjM1OVxueCAlJSAxMDAgLyA2MCArIHggJS8lIDEwMFxuXG5mbGlnaHRzIHw+IFxuICBtdXRhdGUoc2NoZWRfZGVwX2ZyYWMgPSAoc2NoZWRfZGVwX3RpbWUgJSUgMTAwIC8gNjAgKyBzY2hlZF9kZXBfdGltZSAlLyUgMTAwKSkgfD4gXG4gIGdncGxvdChhZXMoIHggPSBzY2hlZF9kZXBfZnJhYywgeSA9IGRlcF9kZWxheSkpICtcbiAgICBnZW9tX3BvaW50KClcbiMgd2hhdCBhcmUgdGhlIHZhbHVlcyBiZXlvbmQgMjQgP1xuZmxpZ2h0cyB8PiBcbiAgbXV0YXRlKHNjaGVkX2RlcF9mcmFjID0gKHNjaGVkX2RlcF90aW1lICUlIDEwMCAvIDYwICsgc2NoZWRfZGVwX3RpbWUgJS8lIDEwMCkpIHw+XG4gIHNlbGVjdChzY2hlZF9kZXBfdGltZSwgc2NoZWRfZGVwX2ZyYWMpIHw+IFxuICBhcnJhbmdlKGRlc2Moc2NoZWRfZGVwX2ZyYWMpKVxuIyBmb3Jnb3QgYSAwIGluIHRoZSBmb3JtdWxhLCBjb3JyZWN0ZWRcblxuIyBtaW51dGVzIHNpbmNlIG1pZG5pZ2h0XG4jIHRlc3QgY2FsY3VsYXRpb25cbnggPC0gMjM1OVxueCAlJSAxMDAgIyBtaW51dGVzXG54ICUvJSAxMDAgIyBob3Vyc1xueCAlLyUgMTAwICogNjAgIyBob3VycyBpbnRvIG1pbnV0ZXNcbnggJSUgMTAwICsgeCAlLyUgMTAwICogNjAgIyBtaW51dGVzIHBsdXMgaG91cnMgaW50byBtaW51dGVzXG5cbiMjIHdob2xlIGdhbWVcbmZsaWdodHMgfD4gXG4gIG11dGF0ZShzY2hlZF9kZXBfbXNtID0gc2NoZWRfZGVwX3RpbWUgJSUgMTAwICsgc2NoZWRfZGVwX3RpbWUgJS8lIDEwMCAqIDYwKSB8PiBcbiAgZ2dwbG90KGFlcyh4ID0gc2NoZWRfZGVwX21zbSwgeSA9IGRlcF9kZWxheSkpICsgXG4gIGdlb21fcG9pbnQoKVxuYGBgIn0= -->

```r
# Fractional hours
## MM values / 60 = fractional Hours

# take test value
x <- 2359
x %% 100 / 60 + x %/% 100

flights |> 
  mutate(sched_dep_frac = (sched_dep_time %% 100 / 60 + sched_dep_time %/% 100)) |> 
  ggplot(aes( x = sched_dep_frac, y = dep_delay)) +
    geom_point()
# what are the values beyond 24 ?
flights |> 
  mutate(sched_dep_frac = (sched_dep_time %% 100 / 60 + sched_dep_time %/% 100)) |>
  select(sched_dep_time, sched_dep_frac) |> 
  arrange(desc(sched_dep_frac))
# forgot a 0 in the formula, corrected

# minutes since midnight
# test calculation
x <- 2359
x %% 100 # minutes
x %/% 100 # hours
x %/% 100 * 60 # hours into minutes
x %% 100 + x %/% 100 * 60 # minutes plus hours into minutes

## whole game
flights |> 
  mutate(sched_dep_msm = sched_dep_time %% 100 + sched_dep_time %/% 100 * 60) |> 
  ggplot(aes(x = sched_dep_msm, y = dep_delay)) + 
  geom_point()
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


4.    Round `dep_time` and `arr_time` to the nearest five minutes.


<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NDM1MzUyLCJuY29sIjo0LCJzdW1tYXJ5Ijp7IkEgdGliYmxlIjpbIjQzNSwzNTIgw5cgNCJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUJyVmNDNWhWVmRuZWM4N1paKzlEYVdpbVZCYVlwbmhEVkRRMHM4a21zeUxqVi9TZjFCSUVFbk1FUkRSVXlzbndrbUtOaW9ybVpid2xsZldUbWxHaVRiYy9LeW95S2tyU3lmU1hMaGFsbFpYcC8zNXJ2ZTlxN3dXSGMyYWllWjczZVdmdnZTN2Y5NjIxdjczVzJlODVSM1YxN3oraWUwU1NKTldrVnV0SXFpbitUZEpqcGh5Kzk4UWtxVlZ3MEpIVWtvYnhBaFI2S2Y2cEFWdmgvL1h1WXBKc0M0d0dkZ0oyd2FtL0pra2xCMTRNdkJ6WUdYZ3RzQnN3RnRpREdBZDBGM0E4OEI1aU9qR1RPQldZQzh3RHppRE9CczRCRmdJZkFoWUJId1VXQTVjQkh5ZjZnTXVKK3d0NEFQZ0tNRkRBVjRtdkFkOHNZQlh4UGVEN3dBK0FId00vQVg0Sy9JeDRHRmdIL0FKNEJIZ1VHQVFlSTM1RlBBNDhDYXduZmswOEZlSDN4QitKUHdGUEU4OFU4R2NDc2E5aUhLcXZJVEFlMVYyQjNRakV2N3BIQVhzQ2V3RVlpK3A0WUY5aS93Z0hBcThESmhJSEU2OEgzZ2gwQW04QzNreThCVGdjT0lKNEcvQU80SjNBZnhGSEYzQk1BY2NTLzEwQTVrZjFPT0Q0QWhZVmNDRndFWEJ4QVpnTFZjeUQ2c2VBSzRBbHdOWEFOY0Mxd0hYQUo0RHJDN2lCdUJHNGllZ0hiaW5nMWdKdUJ6NEpMQU0rQlh3RytHd0Ivd01zTCtEenhCZUlld3Y0WWdFcmdDOXZBaXVKci9qN3Ivb2I0Q25pRDhBR0FQT2grbWZpYjhEZmdYOFEveVJlK0JkcU5TSWw2c0FJNGtVQTd1TWE3dmZhMXNCTGdKSEF0c1FPd0NnQTkzbnRGY0FyQzlnUmVEVXdtaGdEN0VSZ2J0WjJKakFuYWtjUzd3SW1BNWdmdGFPSlk0aGpJMkJlMUxxSjR3bmtqdHA3aVduRVNRWE1pRENUT0FWNFAzQWFNQnM0SFVDdXFaMEpuQVY4Z0VBT3JDSHYxSkIzYWg4RVBrU2NCL1FTSHdiT0J6NENYQUJnYnRZd04ydkxDWXgvN1M3Z2J1SWVBSE9oOWtYaXl3WGNWd0RHdklhOFZQdGY0RnZBZzhTM2llOEEzd1crUi93UWVBaFlBeUJQMWRZQ2p4RElTYlZmQXNoSk5lU2oydU1GUEVFOFNhd25rSjlxbUc4cHhqdDlGVENHZUEyQnNVeVI1MVBrbVhSc2hOMExRTjVKa1hkUzVKMTBIMkI4QVFjQXlDL3BRY1RCQkhKTGlyeVNJcGVrYndlUVM5SkpBT1pNaWpGSlAwaWNWMEF2Z2ZGSXp5Y3dKaW5HSkVWK1NQR2NTSkViVWp3ajBzc0xRSzVJcndLdUlaWUN5Qk1wOGtPSzNKQWlINlEzQThnRjZhM0U3Y1Fkd0RMaVU4U25pYzhRbnkwQWN5RzlpOEJjU1BIY1NBY0xlSXpBdUtSUEVQOVh3Sk1FeGlmRitLUTJQcjhsa0JQU1B4U3dnZmdUOFRTQmZKSCt0WUMvRllEY2tTSnZwTThCLy9SQWV2Q29FVGlvWndVMENrQU9xYitvZ0swSTVKSDZOZ0J5U0gwNzRHWEE5Z1hzVUFDZUkzV01kZjJkQk1hOC9xNENKaGVBZkZHZkFoeEx2QnM0cmdEa2lQb0pCSEpGSFhtaWZpSXdyWURwQlBKRC9YM0V5Y0Fzb0FkQWZxaGpMVkpIZnFoakhWS2ZUNXhKSUYvVVAwQmdidGJQM2dTUVArcm5Gb0JuU1AyT0FqQlA2cDhsUGxjQTVrZ2QrYUtPNTBNZCthR092RkJmU2R4UFlGMVRSNjZvRHhEZklMNVpBUEpGL2JzRnJDS1FOK3FyQ2VTUCtocml4d1R5U1AybnhOb0lQeWNlSnRZUnZ5QWU5Y2hHRUpnUEdlWkN0ZzJCT1pEdFVBQ2VKeG1lSTltT0JidzZ3bWdDZVNqYnFRRGtvd3hybjJ4WEFqa3BReDdLZGllUWc3SzlpWDBLMkpmWUR6aUFPSkJBWHNvT2lvRGNsTDJlT0FRNGxNQjZLT3NoOEV6SjhEekpNQit5Y3dtc1diUHpDYXhmTXVTazdFSUN6NG9NK1NuRCtpVzdwQUNzWlRMa3FnenIyUXg1S2x0U0FQSlZkaldCbkpVaFoyWFhFY2hkMlEwRThsYUd2SlhkWGdEbVhvYnh6bjVJNEptUi9RakFtR1lZeDJ3ZDhTaUJ2SlFoSjJWNGJtVElTOWtUQlBKUmhqeVVJZmRrdndPZUtnQnIyT3laQXJBMnlaQnJNdVNXN1Bra3dYWWh5U3RFRlVCZXliRVd5Yk1DY2dKNUpjZDQ1QmlQSEdPUXZ3RkF6SFBFUEQ4TXdITWk3eUtRTy9LM0FsaC81c2dWK1RFRWNrT085VU9PL0pEai9zK3hOc2l4RHNoUEprNGw1Z0JMQzhDNk1VZE1jOFF5eHhveHY0bEFYSFBFTmNleklMOE5RRnh6M0xzNW52YzVjbnlPOVYyT1ozditKUUQzYmY1MUFQZGtqbnV2Z1QxVUEvNDFjZ0wzUkFNNXNZRTgyTUJ6dG9HNTJzQ3pzWEVnSG1aSmpNUUhEMnUwQk91enhQWm5XSXNscitSK0RQZEJndm1lWUU0bldNY25tSzhKL0V5UXl4TGtzUVQ1S2NFenNBTjV2b0tZVnhEekN1SmJHYzA5MjY2RTltNjdFM3NTZUlaWDl1WmVUdGluQU52WEljYVY0d2piNDUxSVRDVm1FTnJyd2JZSzFtT1ZIdUkwUW5zLzVOb0s4bXhsQWZkK2VPNVg4THl2SUJ3VlBPc3J1S2NxZU01WExpUXU1cjRROTFEbFV1NE5pM3ZDS3dxNE1zTEt6ZXdadjBWZ0RWYjVOdkVkN2hHTCswVGNXNVVmRWc4VmdIdk03U0cxajlSZXNyaWZOQ0NuaGoybDlwWENZUEt2L2FYdEtaOGdjQy9hL3RMbWhOdW51Ny9PQ2VSRHlXL3FMZk41Zlo1N084bXp5Q3M4ZnpnbmoyL0MzUkd6M2ZNSG12RDZUZk5IUmtZOE1lS3A1SXRiOE5wTjh5TDZ2MmdzZVhMRUM0YkdGd3h1bmkvTWg4bmptM0IzRSs2TmVGa1RYdDJDbjkwOFh6U21UVDZpVFo0N1JGNjZoWG5BODBlVEpqeTJCVThlSWk5b3dmMXQ4b05ENUExbHZtUlVDKzVzd2JNaTdtdVRWMndoSHR3OEx4N1RnbzlvaytkR3ZEVGlnUmE4ZnN2d1pTT0h5Uk5iOE5RV2ZQRVFlZmtXNHJYRDQ0OGxuai9lR2ZHc0p0d1g4WW9tUE5nZTk5V2E4S2cyZWE4MnViTk5ua0tlTlV4ZU9FVHUyelJmUHI0SmQ3WEozVnVJZTVwdzd6QjV5UkI1V2NRcm0vRHFKdng0bS96czBQaUtGN2ZnTVJFUHRPQTFRK1QxUStUblBGODVNdUpkaHNrVEk1N1VoS2RHUEQvaWk0ZkoxdytUbDN0ZU1vTzhvQWt2YnNIOVc0anZhY0lQTnVGMUxYaERtYStxUmN5OGVkVmVUYmlUUEVoK3BqMitPaDhpN3hqeCtJaTcydVR1RnR6VGhIdWI4SkkyZWRtL3lTdGI4T3BOOHpWenlZdmE1S1ZiaU85c2t3ZUd5V3VHeU91SHlNOXRucGVPYk1LN2JHR2UySVFudGVDcFErTnJ0eU9QSlIreWhYaHlDNTdSSmk5b2t4Y1BrZnRiOEQwUlA5Z21yL3NQOFliTjgzVjk1TnRhOElvMmVWWEVneEUvTXp6K1JONkNkMnpCNDRmSVhVMjQrei9FUGY4bTk1YjUrakVSVDRqNGlJaFBhTUZ6dHhBdkdpWXZiWlB2YkpNSGhzaHJXdkQ2TGNUUGJacHZXTjZFdjBGZVMvN2Rwdm5HSk9MdDJ1U3hiZkloTFhqeUVIbEdtN3dnNHNWdGNyL25tenBiOEJUeXJCYThzQW4zRFpGdmkzaEZtN3lxQlErU255bHpmNjFOM25xWXpQajB6NHQ0WVJPK3NBWDNOZUhyeUo5cms3OFc4YW9tL0pPSUdjZWJ4N2ZKQjdmZ3JoWjhKSm5QaVp0UGlyZ240ck1pdmlSaTdpOXVxWkJmM0lTM0orOFI4YUhrbzhoOFB0d3kxL0Y1N3VPTDdKWlczT21YcTBuZ2NlUUo1SU1panQrUGRmSDgyeUkra3Z4dThuR2RubzludmZmeS9EUWVoL2Rzb3lKbXZaYnYyV0x1SGlMM0RvMmJ2cjhUcjk4MGIvUWVMK2FKTFhocUM3NDQ0dVZOZUcyWi9lTjlNenkyQ1U5dXdRdGFjUC93dU5YN3hhYnZHY2MzNGU0MnVmZmY1R1hENU5WdDhyUEQ0eUcrdjB5QzNyM0RUandPdGdmWjc0RkhFNitweHNhcmNnRjF3KytrOWhoWm9mcHVyejEyNy9oL3dQZjV2MDY4OWhxZFZDOWhHZE1oWDA0K0RHVk15N3M3dGNjM0E1TzlmdGswM3RhSDZWcWQ1aGdMcmVyZGlkTngxN0I0TXAxMUxRUC9tcHJvTHdGUGV3MnIweFgvZy9aSk43eWMvWHpKWHpNdGIvVTVhb09QOSsyWjM3V0dQKy8wdkFuTFRpR3FPTDRmZU5iM2JacGc4OGxwZzFQOGo2eFpleW40TDlRc3crYmE5dFFwbXc3MjVlQlBKMTdIZlEyT1RlYzloWnBYMDRuL01YRzY4TnFyYU51Vlh1dHErdWJhSks4RE5qMjAwd09QOWo0NExTOXNkbnBpMC8wZVRWM3VTZFRmbXArbUN6Y2Q1TXZZeHIyMGQ0WFhXanNiemVlZGVHeHRuK2pqYkxwZzA0T2E3elVzSW1yVEdadTUvcHF6WjQxdkkraUVUVWM4aTNiZTY4ZXQ5Z3ZxY2o5TWplMVcxQWpidFczcDMrZXBDelk5LzEvWjF2MGNnMTc2YVAzOHlNZlVOTEttRVRhOXJOUDkzdWV2T1kzeUNPOWpiU1g3UVV4ckQ1Qk5RMno2MkIyOFp0ZkdvWFpxNHZYTHBpMmVENWgyc09vMXRFNFhialpPeGZGbzc3Y3JkelQvTjQwMEh0U21GNjU5eEdjRXA2czJiZmV4WGd2czdMK0lldU1MYUsrTjBjT0oxeTZmenRpK2g3cmhUN0dQMC9ELzIrZ2o0bUg2NHhvV1R5a1dXdWs1dnF6VFN2ZlNadE40bjB0ZnY0dnIrd043SjA2SDdMVFF1SStkWGhyM2FIb3RjS0NIalpucGtGME1GMUZ2L0hKZWU0UjZZdFAvWGdxWWp0MTAyVi8zUGp2Tjhsc1pyM2ZRM2ozOVdLUTdlZTJ2bXlNL284Mm1qVDZNK21Ua2p4VHpMTFUrMzA3Zjd2QXhTWEUvT1kyMDFURnQ4eHZJbHdIN29zeTZ4T3VZOS9QOU9jM3lXQjlicDRzMjNUSVcrazdiYkRHNE9uR2FacWZ0ZmkzN3Zwdm45MHE4eGh1MjFXM2VtcTRZK1NmRmh0YnB0VzIrblUvZmY4TTZDM245bGFpVDA0ZGIvWEU2anI3ZjVNdWFqdGpwbEs5bU93ZXhybW0rUCtIMXRTNGVpSjFwalYwTThUQk5ud2ZPOWpwWnA0MjIrc2d2cG45MmJSN21ZZnBlNTZmNTg1YkU2NkJOUC82SXQ4R05qZG1DOFU5TlM1eDZmYkhUYWQvZ05jUnViTEhScitPK1NuL1B0c0JPaTJ3NlhlUzJGSE93amh4bHVuRFRGcHQyMjJtRHJVL1RaWnR1R2c5VjB6azdHNjNkSjZrOVB0SFB6eFQzWTczRHQrYzAwY2Q0MzV5K0d2ZGEvWFJxa2srbG5WYkdkT04vQjUvQzlzNWxPVHdiNnRnTW1aN2I2WndIZU82dHliKzAxb2hqSFhuZmFhVHZvdjRYZWFQK2FkcU9lVnovQWR1YlEvMHY3aitueHphZEwrNDlwK1cyc21iN2o2Z1BmaGxoR3U5dFdlOWJqSlZwaWp0OTJjejA0YWFsUmp5ejdmMnhhWGRkVy9BbjJ6bHgrbUFYTitRTTAzcWJwcmYrVlQrdVR2TzgzUHVYV1h5bTAwK0x6MFBVTU1NMzB4Q2JENmI3dFhhZFQ2WmZSZzdPOXZRYVlOTnFaM044VEp3MitDWGVKdE5UbTY2M2ZudmlOZFdJVDdZMWRiOXZUSnl1Mk9uRFRldU4rOW5wc2pHM3N0ZDVHNnlkT3U1dnAyZkdzOTcwM05uK1BoWk9PMnYrZngvOFV1cUxkNkRtZUJmcWYrZlFqbnU5UDA1SC9FSDZpYkV6M2JTMWJ4cHU1OS9EUG1hbVFYYTI3MGQ3cmQyejJPYU8xUE5lUVIzeTl0UVFZeGVVL2NiNzVMVENQNmQyZUJ2cWcvZWdYZFkrY21UV1Q2MHhucU1aN25PbjZiNlIrbUw0bUYzS2F6ZXk3Yk9wSjBZOGM5TitmNGpuRE1nTFRnZHQxMDJqakx5ZFdSd3Zvczc0bDR6THoyaWpYY085blAzVWx6V3RzUG1jSDB3ZDhxL1l4Mk5nM08vWnZNVHByL01WdEFWek1rUHVkdnBvMHlHYnJobHJuaHozbittWDgrT29QN1kyL2tadDhZSHM1eUhXdzdva1E4NXhtbXRyQTNrcW4rRDl6MS9uYlhaYVphdXozdjl2L3VTNEYzTE1tUXg1SjhNOTI3QXlSM3U5c09tbTgyNzY4UWo3UmQ3Sm52Ynh5WTlrVysrbGJqbW5YYVpseHB6SWNQK1pUdHoxZXkxOXdqek44ZnpKNy9QOVdBeno5L3N4ek8rbjl2cG9YcitXT3VhYmFjY2J2VWJhNWtOK2dJKzN1MzR5L3YrbjEwaTc4WG5NMjVoUG93YmF4aGh6TzMrQUd1cDd2TGJieFJZeHp1L3d1bWNyNjN5ZTdHUHRmRHFZR3VsUEFnOVIzMzByL1R5QWVtcjcveTRmeHh6cmxueVMxM28za0N0enc5M1VYaU5mNXJqZmM2d0JURU9lNEZtV1QvZDUxclg5UmJiMUlPcmlIbWxzNC9YV09YSmwvZ0kxMk9NNFJvaHYvZ1VmTzV0VHllc1RGenluMlVhK2E0ejA1ZHd4TGpYc3c2alU5OSt3RndLd3EyRmFiUHV3QS9kR0EzbW5zYXYzMCttMnExNVgza0FPYk96bSsycmcrZHZBdXJLQk9vM1hVRmQrRzh2YmgwOG8xOWlaOFVVT3lGZDUrKzE3dUc2ZUlmNkpmYWhxdG96MDlTd1dUaHYrQ2wvZjFtS05BMzBmaWRYZGhucDAwNTVqUGREQVhHNmdiQVAyTlpBdkcvWjlYNXhMN0VNTCtKMVkyUmQ1TzF3Y3huZy96VjZuTmNjNm9RTmptQ0QvZEdDZUpmQTdzUS9XNEZkeU51M2F3ZHVTNE41T3NCN3VzQmRacDl1YU1RYitjTjkxNEw1SU1QODY5Z0ZqSGR5Qk9kQmhIeHBnYjVEWWgwNFl1NG90QkpBakV0dTN6ZkI3dFE3TW93NnNMK3k3bSs3N3NsaS91Ty9TcnZGN0xQc3ViaFhQeU9xaDNQdnM1dG5LMkw2amltZVEreDZzN2RYZTVQWGcrczZzZmRmWHJwdnV1Z3AvN2Z1dnRvK3o3K3k2UFI3dVkvY2RVZHhYOW4zWnlsL1kzMkx1MTQ3M2ZkZ2VzWXBZVm43TFBkT1ZmcDlVdmRTdm5kMCt6czd0NS9kTFZheE5xcTlsMjJhdmZRZjFBZnBoMzJXOWovc3o3RmZjZDJtZjVaN3lScFl4eGh5MDczcFdqK0tlY3l6dCtTVDNSRi93OXR2YXJmbzU3anR0MzdHTjN4dFZuK2QrRWpiWjkwVHQyUGFHNXF2dEV5emV0cmR4OVo2bnYwK1IzOHg5RnU1SjkxM2lQeEcydjdOOTV3YlA3dnVrbzdsSG1zOTJMWDU0ZHRsM1d1MmExN3QzenU5M0U2V3paOER6ZVoyZVp5YzhQOGF6OUxqU0crcHpIdWt0cFd1VkRqVG9YUG41dC9TZjRYT0xYdkpxejlJM0I5MXZFclduZHRhWDJ3djk4M05CNlo2RHZTUExMRjJ0Nmw4VXRTT2RtdlNlMGoxS3I2bDJwUk9VdmxkNlJPa25wWnVWemxKNlNlblNGRWZwSUJXdldIOFo5eHZhWXozcERtTTlaZEQzcWozWnVWZFVmbUc1bnM3SE9rQmRELzJ2S1BzZDRyR2lmS3pybDBUbGdrNDA4amRjN3l2N0x6K2xzdzI2NUFIYXljL1hOYjdTdlVrUHFmYUNmUXZML21vK1NOOG0rNEx1a25HUVhqYkVSZkdqZmRJcEtzNUJqOWxiUHBaT1VPZWxBMVE3MGsvTDdpV1R5LzFxL2lpK3NRNDR4SEd3YkdlNHZyRGN2OHByZmtvbnBYRVArc2NsVWYyVjVYcUtqL1Ivb2QxbkkxNWRqcGY4a3I1UjR4NTBnbE41blhHVG5rOXhqbldVMHZOcS9EYTYzc2Y0YUp4cGwzU1M0VDZRdlYxbGYrU2Z4a2U2T3VrcXBiY0xkcTh2MTFPN1FaODhxbHd1ekllRlpidDBySG1xZUFROVl6L2I1L2dwdnRLaHFwN2lMM3VsZDVJZUw5Wk5hNTVJSHhucXE3MnU4dm1ncSswcDIwZDd3M3VtTUg5VXZ6dnlRK01pKzY4dis2MzR5cjR3WHhSbnRiOGtzb2Z0UzQ4WC9HRDVvSWVNNXIvMG45SzlTcThudmFUYVZWeFZUOGZTS1NrK1FaZkwvb1BPODU0eVh4bmZENU1pTytUWHVqSnJQSFFjNWhmamQxVW5yODhvbDFNL1FhL0orRW1mcWZnRVBmREljanV4M2xUeks5YWJCdi9vaitLcnVNWTY0ampPNmlmV2t5cGZ5djVncitLMXBOeSs3SlQvNmtmMXBhY044V0FjTkY0aFhsM2w4L0x2Nm1qZUJYK2U0Zlhlc2wzU3I0YjYzZVZ5UWNlc2VNbi8xWnV1SDNUTjdGODZQTFVUK2w5V3RsOTZ5NDNpcUhyZGtSK3F6L2FsZTR6blVaaHZzazkreUE2MkczU2FkMFp4MExpc2kvcmR3R1BHVy9vOXhVZjJielFmQjh2OTZWajZPdWxnZzExcnluYUZlclV5UzhjWTdGN042NXh2MXd5VTdaQytWM0VJZVpuSDB2WHF2dFYxNlRPRHZsaitUK2J4K0xJZDBvV3EvNkF2SGlpM0ovK2xROVU0aDNaN3kzN0t2cUNiM0c3VGNkTDhVN3U2cm5ZVjcyWjZVT1dIb04rZFZPYTRuYURublJqWngvYWtCdzNsMkk1MGt0SVJTMGNhN050UWJpL0VpLzFvbnNoKzZTRlZUdkdKZGI3U2gwcVhxWGpKbnFDRDNERnE3OEZ5UDlKRkJuL3BwM1NOc1IzU0t3YTdvbmhKUnhyckxUZlNLMDhzSHdjZFpXUnZzQzhwSDBzWEtYdmxkOUE3OHJyMGg3Skw0eE4waVJQSzhZdjF6TklsS2w0YXA2QnZYVkUrSDlwYkhOVlRYTHZLckg2bHIxUWNwWE9VdlhFOE5lNnhMbEx6UXJwQ0hZZHlFOHB4a2gvU0x3WTlNYzlyUEVJOWxndjZSczN6L25KL3NYNDQ2RnJYbFAxUnU1cFhza3U2Uk1WWDlUUXZwTGVUamxMelBlaGhaZWNKNWZxeVYrMHJUaUVlc3JlcmZGMDZ6SEIvRHBiN0N6cGUyWEZuNUpmaXg3aUZ1QTlFMTJtSDlLQ3lVL05EZWtYcExHVlhpTnZrc3IvU0lRYS9GMFR0YVA3UkQra213M3haV3Jadkk5Mm1qblcvakNsenJPdVVYUnZwVGhlVXI4c3YyYW54N09kelVUcllXQ2VyZUVyL0d2eGNYSzRuZldjbzExYytIK0xIK2tIUHlldEJ0em1sM0s1MGt4cG42U1ZqbmFqOENNZmtXQThzWFdDd1IvM1Jic1UvNkVObEgrZVg5Sit5djM5RjJjNWdCK3NISGVlc2Nqbk5pOURmcW5JOXpidHd2RjI1SGNVL3hFUDlSSHJUWU9mVzVYYWtmNVN1TTh4amxwZmVzWi9IMGx0cW5JSnVOTzVmM0ZmMks5aC9YWlA0U1hjYTYyVFp6ODI5cktmeE9xUmNYdnJTTUU2eWcvMUoveWwvTkErbFk5VTRoSEsxeUgvcFI5bFByRXNOOFZoWVBsWmM1WS9zRC9VMDdyS2I5bXlrZzE1VmpsT29yLzRHeTNFS3h6MWxmMExjZVN3OXJmU3ZhamVNczhxUEt2ZXZjUTl4a1M1M1dkbXVZT2VzTWt1dnU5RXgvWlF1TitpWUdRZnBjY080bjlTay9vM2tTOHJsOWZzeThrUHJXZGtkNGlXN2FFZlErNDRoSDdYcCtJVnlmSDdvUHRLNGhQYWxuNlpmMHVudWtwVDkzS2pmN2FQcmxmTDE3Wkt5LzdkTUtKK1gzZXBIdXQ5Zzd4Rmx2eVlrVWJ2VWFjZTZaL2tWMnRGMTJSdTFxM21oOXFkUDlkeVZST1hacnNZaGpBZjdsZjQ1NkxsN3krMk9pMWpuVlY3MXBhdFcvL3BjakRydTRJZXVxNzB3RHZMM2lLZ2U0eC9HU1RyeE1aN2ZFZlVmeHp1T1gxUGRPYTlMNXkzOTl4bkxQVXZuZldhbjU4UFo3OVJCejdvdlZFNyt4WEU1YmFybjk3UGV1ZU05bnpEZ3VHMjl1OTUzelNmUFlYdG5qT1F4N1Z3NGwrZlo3MGxqUEd2ZXFwNzA2ZUU5bXJlbjh5emFwL2RxNTdEY09heW45MVROZm45SDc4LzBua1B2emZTZUoveGVqWTdIbG8vRCt5NnkzanZwZDIvQ2VlWlg2YVhqMzkyUlBsajF3L3U3cVAvNGQ0akM3OUh3dXQ2ejZienFYelJRYmplOEQyRzk4THMxaXN2cXNyK3FwOC8zVlU3dkZmUmVVWjg3Ni8ySnl1bDNnK0xmcDFIN3Nqc2NUL1dzOXgveUwvd2V6ZG95aC9lV0s4cDJhdnpEOWJnZDlxdlA1elVQVkUvdkNSV2ZVSDVVMlUrMXE4L2RaTC9ldzJsYzlmbC8vTjVSNVJRbmxZdmZINGIzYlh1VjdRenZJV2RGN1haRzUzbXMrUmkvNTlSOGFmYTdOS0dmdnZMeFJyL1h3dlA2dkR6VVkvK2FGOUg3dEtUOHcrL3A3R21uelR3ajhVS05Hay9tTTJiT1BYSCtLYWZONUhIRGp1Zk5PWFAyREJXWU5tOWVxWUFkK3dMbDVodno1bnhnbkxyWUt2RS81SmU4OE1Kem8ySTdwdmRNTzBOMjZPU0lHZFBtVHh2M3ZubW9qNlBub3lyWm5MbnpUNWt6MjM0MTBCUXo5YWh5eDd6b3hNZ3paNXNsTS9hZVB1dk0yYWZ1dmU4QjBmWHEzTmtuVzZlSi8rWDdoQlozSlBYYmxvYi9MVWpPak1vTHJGNW45ZnJNMlNlZk1sc1JTWHVtblRTelJ5M1BtSGtXLzkwYUFYSHhHRGQzM2ltejU4dFJuRDFqM1B3NTg2ZXB5b2pwYzNwMHhybWVQUC8vR3N1bU9zOWZBQUE9In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["dep_time"],"name":[1],"type":["int"],"align":["right"]},{"label":["dep_round"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["arr_time"],"name":[3],"type":["int"],"align":["right"]},{"label":["arr_round"],"name":[4],"type":["dbl"],"align":["right"]}],"data":[{"1":"1","2":"0","3":"328","4":"330"},{"1":"18","2":"20","3":"228","4":"230"},{"1":"31","2":"30","3":"500","4":"500"},{"1":"33","2":"35","3":"238","4":"240"},{"1":"36","2":"35","3":"223","4":"225"},{"1":"503","2":"505","3":"808","4":"810"},{"1":"520","2":"520","3":"948","4":"950"},{"1":"524","2":"525","3":"645","4":"645"},{"1":"537","2":"535","3":"926","4":"925"},{"1":"547","2":"545","3":"845","4":"845"},{"1":"549","2":"550","3":"905","4":"905"},{"1":"551","2":"550","3":"846","4":"845"},{"1":"552","2":"550","3":"857","4":"855"},{"1":"554","2":"555","3":"914","4":"915"},{"1":"554","2":"555","3":"725","4":"725"},{"1":"558","2":"560","3":"719","4":"720"},{"1":"600","2":"600","3":"729","4":"730"},{"1":"600","2":"600","3":"745","4":"745"},{"1":"600","2":"600","3":"810","4":"810"},{"1":"603","2":"605","3":"800","4":"800"},{"1":"605","2":"605","3":"906","4":"905"},{"1":"605","2":"605","3":"857","4":"855"},{"1":"611","2":"610","3":"923","4":"925"},{"1":"611","2":"610","3":"913","4":"915"},{"1":"613","2":"615","3":"923","4":"925"},{"1":"613","2":"615","3":"834","4":"835"},{"1":"619","2":"620","3":"751","4":"750"},{"1":"624","2":"625","3":"809","4":"810"},{"1":"626","2":"625","3":"928","4":"930"},{"1":"627","2":"625","3":"929","4":"930"},{"1":"627","2":"625","3":"848","4":"850"},{"1":"633","2":"635","3":"916","4":"915"},{"1":"634","2":"635","3":"757","4":"755"},{"1":"636","2":"635","3":"926","4":"925"},{"1":"638","2":"640","3":"1121","4":"1120"},{"1":"644","2":"645","3":"936","4":"935"},{"1":"649","2":"650","3":"1004","4":"1005"},{"1":"652","2":"650","3":"947","4":"945"},{"1":"653","2":"655","3":"811","4":"810"},{"1":"655","2":"655","3":"1044","4":"1045"},{"1":"655","2":"655","3":"841","4":"840"},{"1":"656","2":"655","3":"1031","4":"1030"},{"1":"657","2":"655","3":"1001","4":"1000"},{"1":"657","2":"655","3":"902","4":"900"},{"1":"701","2":"700","3":"953","4":"955"},{"1":"701","2":"700","3":"1011","4":"1010"},{"1":"701","2":"700","3":"1142","4":"1140"},{"1":"702","2":"700","3":"951","4":"950"},{"1":"703","2":"705","3":"1019","4":"1020"},{"1":"704","2":"705","3":"845","4":"845"},{"1":"704","2":"705","3":"1002","4":"1000"},{"1":"704","2":"705","3":"1005","4":"1005"},{"1":"705","2":"705","3":"944","4":"945"},{"1":"705","2":"705","3":"809","4":"810"},{"1":"706","2":"705","3":"953","4":"955"},{"1":"709","2":"710","3":"1019","4":"1020"},{"1":"709","2":"710","3":"1048","4":"1050"},{"1":"709","2":"710","3":"1020","4":"1020"},{"1":"716","2":"715","3":"1023","4":"1025"},{"1":"716","2":"715","3":"859","4":"860"},{"1":"717","2":"715","3":"841","4":"840"},{"1":"718","2":"720","3":"1000","4":"1000"},{"1":"719","2":"720","3":"1033","4":"1035"},{"1":"725","2":"725","3":"1020","4":"1020"},{"1":"726","2":"725","3":"1054","4":"1055"},{"1":"727","2":"725","3":"1024","4":"1025"},{"1":"729","2":"730","3":"1019","4":"1020"},{"1":"729","2":"730","3":"1108","4":"1110"},{"1":"731","2":"730","3":"1108","4":"1110"},{"1":"732","2":"730","3":"1027","4":"1025"},{"1":"733","2":"735","3":"957","4":"955"},{"1":"734","2":"735","3":"1016","4":"1015"},{"1":"735","2":"735","3":"1031","4":"1030"},{"1":"736","2":"735","3":"1047","4":"1045"},{"1":"738","2":"740","3":"857","4":"855"},{"1":"738","2":"740","3":"1047","4":"1045"},{"1":"739","2":"740","3":"1029","4":"1030"},{"1":"739","2":"740","3":"836","4":"835"},{"1":"740","2":"740","3":"1043","4":"1045"},{"1":"743","2":"745","3":"1014","4":"1015"},{"1":"744","2":"745","3":"1000","4":"1000"},{"1":"744","2":"745","3":"1004","4":"1005"},{"1":"745","2":"745","3":"1046","4":"1045"},{"1":"745","2":"745","3":"1012","4":"1010"},{"1":"749","2":"750","3":"946","4":"945"},{"1":"749","2":"750","3":"1049","4":"1050"},{"1":"749","2":"750","3":"938","4":"940"},{"1":"749","2":"750","3":"900","4":"900"},{"1":"750","2":"750","3":"919","4":"920"},{"1":"750","2":"750","3":"1114","4":"1115"},{"1":"753","2":"755","3":"852","4":"850"},{"1":"753","2":"755","3":"1211","4":"1210"},{"1":"754","2":"755","3":"1105","4":"1105"},{"1":"755","2":"755","3":"1009","4":"1010"},{"1":"755","2":"755","3":"853","4":"855"},{"1":"756","2":"755","3":"1053","4":"1055"},{"1":"756","2":"755","3":"1020","4":"1020"},{"1":"756","2":"755","3":"915","4":"915"},{"1":"757","2":"755","3":"1226","4":"1225"},{"1":"757","2":"755","3":"1013","4":"1015"},{"1":"759","2":"760","3":"1100","4":"1100"},{"1":"801","2":"800","3":"1111","4":"1110"},{"1":"802","2":"800","3":"959","4":"960"},{"1":"802","2":"800","3":"1111","4":"1110"},{"1":"804","2":"805","3":"1055","4":"1055"},{"1":"806","2":"805","3":"1048","4":"1050"},{"1":"807","2":"805","3":"1130","4":"1130"},{"1":"807","2":"805","3":"1033","4":"1035"},{"1":"808","2":"810","3":"1103","4":"1105"},{"1":"810","2":"810","3":"1122","4":"1120"},{"1":"810","2":"810","3":"1107","4":"1105"},{"1":"810","2":"810","3":"1153","4":"1155"},{"1":"811","2":"810","3":"1122","4":"1120"},{"1":"812","2":"810","3":"1201","4":"1200"},{"1":"814","2":"815","3":"1048","4":"1050"},{"1":"816","2":"815","3":"910","4":"910"},{"1":"817","2":"815","3":"1010","4":"1010"},{"1":"817","2":"815","3":"1301","4":"1300"},{"1":"819","2":"820","3":"1111","4":"1110"},{"1":"819","2":"820","3":"950","4":"950"},{"1":"819","2":"820","3":"1029","4":"1030"},{"1":"819","2":"820","3":"952","4":"950"},{"1":"822","2":"820","3":"954","4":"955"},{"1":"823","2":"825","3":"1046","4":"1045"},{"1":"824","2":"825","3":"1020","4":"1020"},{"1":"824","2":"825","3":"1057","4":"1055"},{"1":"826","2":"825","3":"954","4":"955"},{"1":"826","2":"825","3":"1055","4":"1055"},{"1":"827","2":"825","3":"1119","4":"1120"},{"1":"831","2":"830","3":"1044","4":"1045"},{"1":"832","2":"830","3":"1141","4":"1140"},{"1":"833","2":"835","3":"1436","4":"1435"},{"1":"835","2":"835","3":"1027","4":"1025"},{"1":"835","2":"835","3":"1148","4":"1150"},{"1":"837","2":"835","3":"1123","4":"1125"},{"1":"838","2":"840","3":"1054","4":"1055"},{"1":"840","2":"840","3":"1136","4":"1135"},{"1":"840","2":"840","3":"1141","4":"1140"},{"1":"841","2":"840","3":"959","4":"960"},{"1":"843","2":"845","3":"1236","4":"1235"},{"1":"845","2":"845","3":"1046","4":"1045"},{"1":"849","2":"850","3":"1149","4":"1150"},{"1":"849","2":"850","3":"1150","4":"1150"},{"1":"851","2":"850","3":"1142","4":"1140"},{"1":"851","2":"850","3":"1128","4":"1130"},{"1":"851","2":"850","3":"1111","4":"1110"},{"1":"853","2":"855","3":"1206","4":"1205"},{"1":"853","2":"855","3":"947","4":"945"},{"1":"853","2":"855","3":"1245","4":"1245"},{"1":"854","2":"855","3":"1240","4":"1240"},{"1":"854","2":"855","3":"1153","4":"1155"},{"1":"855","2":"855","3":"1256","4":"1255"},{"1":"855","2":"855","3":"1037","4":"1035"},{"1":"855","2":"855","3":"1200","4":"1200"},{"1":"856","2":"855","3":"1203","4":"1205"},{"1":"858","2":"860","3":"1042","4":"1040"},{"1":"859","2":"860","3":"1100","4":"1100"},{"1":"859","2":"860","3":"1201","4":"1200"},{"1":"859","2":"860","3":"1207","4":"1205"},{"1":"900","2":"900","3":"1058","4":"1060"},{"1":"900","2":"900","3":"1015","4":"1015"},{"1":"900","2":"900","3":"1150","4":"1150"},{"1":"902","2":"900","3":"1213","4":"1215"},{"1":"903","2":"905","3":"1019","4":"1020"},{"1":"904","2":"905","3":"1152","4":"1150"},{"1":"904","2":"905","3":"1103","4":"1105"},{"1":"904","2":"905","3":"1046","4":"1045"},{"1":"905","2":"905","3":"1235","4":"1235"},{"1":"909","2":"910","3":"1012","4":"1010"},{"1":"910","2":"910","3":"1352","4":"1350"},{"1":"914","2":"915","3":"1222","4":"1220"},{"1":"916","2":"915","3":"1347","4":"1345"},{"1":"918","2":"920","3":"1238","4":"1240"},{"1":"919","2":"920","3":"1211","4":"1210"},{"1":"921","2":"920","3":"1235","4":"1235"},{"1":"922","2":"920","3":"1151","4":"1150"},{"1":"923","2":"925","3":"1034","4":"1035"},{"1":"924","2":"925","3":"1029","4":"1030"},{"1":"924","2":"925","3":"1212","4":"1210"},{"1":"924","2":"925","3":"1200","4":"1200"},{"1":"925","2":"925","3":"1053","4":"1055"},{"1":"925","2":"925","3":"1214","4":"1215"},{"1":"926","2":"925","3":"1053","4":"1055"},{"1":"927","2":"925","3":"1225","4":"1225"},{"1":"927","2":"925","3":"1155","4":"1155"},{"1":"928","2":"930","3":"1303","4":"1305"},{"1":"930","2":"930","3":"1320","4":"1320"},{"1":"930","2":"930","3":"1114","4":"1115"},{"1":"930","2":"930","3":"1131","4":"1130"},{"1":"931","2":"930","3":"1158","4":"1160"},{"1":"931","2":"930","3":"1226","4":"1225"},{"1":"931","2":"930","3":"1140","4":"1140"},{"1":"933","2":"935","3":"1221","4":"1220"},{"1":"934","2":"935","3":"1539","4":"1540"},{"1":"936","2":"935","3":"1413","4":"1415"},{"1":"937","2":"935","3":"1036","4":"1035"},{"1":"939","2":"940","3":"1042","4":"1040"},{"1":"941","2":"940","3":"1120","4":"1120"},{"1":"941","2":"940","3":"1311","4":"1310"},{"1":"941","2":"940","3":"1141","4":"1140"},{"1":"943","2":"945","3":"1226","4":"1225"},{"1":"944","2":"945","3":"1107","4":"1105"},{"1":"944","2":"945","3":"1141","4":"1140"},{"1":"944","2":"945","3":"1146","4":"1145"},{"1":"945","2":"945","3":"1116","4":"1115"},{"1":"945","2":"945","3":"1304","4":"1305"},{"1":"949","2":"950","3":"1155","4":"1155"},{"1":"949","2":"950","3":"NA","4":"NA"},{"1":"950","2":"950","3":"1137","4":"1135"},{"1":"950","2":"950","3":"1105","4":"1105"},{"1":"950","2":"950","3":"1110","4":"1110"},{"1":"951","2":"950","3":"1321","4":"1320"},{"1":"951","2":"950","3":"1152","4":"1150"},{"1":"951","2":"950","3":"1159","4":"1160"},{"1":"952","2":"950","3":"1253","4":"1255"},{"1":"954","2":"955","3":"1157","4":"1155"},{"1":"954","2":"955","3":"1238","4":"1240"},{"1":"954","2":"955","3":"1122","4":"1120"},{"1":"954","2":"955","3":"1243","4":"1245"},{"1":"954","2":"955","3":"1234","4":"1235"},{"1":"956","2":"955","3":"1137","4":"1135"},{"1":"956","2":"955","3":"1123","4":"1125"},{"1":"959","2":"960","3":"1117","4":"1115"},{"1":"1000","2":"1000","3":"1322","4":"1320"},{"1":"1002","2":"1000","3":"1449","4":"1450"},{"1":"1005","2":"1005","3":"1226","4":"1225"},{"1":"1005","2":"1005","3":"1133","4":"1135"},{"1":"1007","2":"1005","3":"1353","4":"1355"},{"1":"1008","2":"1010","3":"1347","4":"1345"},{"1":"1012","2":"1010","3":"1150","4":"1150"},{"1":"1013","2":"1015","3":"1314","4":"1315"},{"1":"1013","2":"1015","3":"1228","4":"1230"},{"1":"1017","2":"1015","3":"1454","4":"1455"},{"1":"1018","2":"1020","3":"1402","4":"1400"},{"1":"1019","2":"1020","3":"1322","4":"1320"},{"1":"1019","2":"1020","3":"1218","4":"1220"},{"1":"1021","2":"1020","3":"1152","4":"1150"},{"1":"1021","2":"1020","3":"1221","4":"1220"},{"1":"1023","2":"1025","3":"1637","4":"1635"},{"1":"1023","2":"1025","3":"1147","4":"1145"},{"1":"1023","2":"1025","3":"1214","4":"1215"},{"1":"1028","2":"1030","3":"1227","4":"1225"},{"1":"1028","2":"1030","3":"1331","4":"1330"},{"1":"1029","2":"1030","3":"1325","4":"1325"},{"1":"1029","2":"1030","3":"1323","4":"1325"},{"1":"1030","2":"1030","3":"1248","4":"1250"},{"1":"1034","2":"1035","3":"1247","4":"1245"},{"1":"1034","2":"1035","3":"1233","4":"1235"},{"1":"1035","2":"1035","3":"1231","4":"1230"},{"1":"1036","2":"1035","3":"1433","4":"1435"},{"1":"1037","2":"1035","3":"1334","4":"1335"},{"1":"1038","2":"1040","3":"1334","4":"1335"},{"1":"1039","2":"1040","3":"1142","4":"1140"},{"1":"1040","2":"1040","3":"1337","4":"1335"},{"1":"1042","2":"1040","3":"1211","4":"1210"},{"1":"1042","2":"1040","3":"1156","4":"1155"},{"1":"1047","2":"1045","3":"1358","4":"1360"},{"1":"1048","2":"1050","3":"1305","4":"1305"},{"1":"1049","2":"1050","3":"1334","4":"1335"},{"1":"1050","2":"1050","3":"1246","4":"1245"},{"1":"1051","2":"1050","3":"1411","4":"1410"},{"1":"1051","2":"1050","3":"1443","4":"1445"},{"1":"1051","2":"1050","3":"1419","4":"1420"},{"1":"1052","2":"1050","3":"1357","4":"1355"},{"1":"1054","2":"1055","3":"1223","4":"1225"},{"1":"1055","2":"1055","3":"1219","4":"1220"},{"1":"1055","2":"1055","3":"1304","4":"1305"},{"1":"1056","2":"1055","3":"1345","4":"1345"},{"1":"1057","2":"1055","3":"1351","4":"1350"},{"1":"1057","2":"1055","3":"1539","4":"1540"},{"1":"1058","2":"1060","3":"1355","4":"1355"},{"1":"1059","2":"1060","3":"1353","4":"1355"},{"1":"1059","2":"1060","3":"1323","4":"1325"},{"1":"1101","2":"1100","3":"1235","4":"1235"},{"1":"1102","2":"1100","3":"1313","4":"1315"},{"1":"1102","2":"1100","3":"1457","4":"1455"},{"1":"1103","2":"1105","3":"1236","4":"1235"},{"1":"1104","2":"1105","3":"1241","4":"1240"},{"1":"1105","2":"1105","3":"1402","4":"1400"},{"1":"1107","2":"1105","3":"1321","4":"1320"},{"1":"1107","2":"1105","3":"1346","4":"1345"},{"1":"1109","2":"1110","3":"1413","4":"1415"},{"1":"1109","2":"1110","3":"1417","4":"1415"},{"1":"1110","2":"1110","3":"1300","4":"1300"},{"1":"1110","2":"1110","3":"1412","4":"1410"},{"1":"1110","2":"1110","3":"1354","4":"1355"},{"1":"1110","2":"1110","3":"1228","4":"1230"},{"1":"1111","2":"1110","3":"1447","4":"1445"},{"1":"1112","2":"1110","3":"1234","4":"1235"},{"1":"1112","2":"1110","3":"1348","4":"1350"},{"1":"1115","2":"1115","3":"1336","4":"1335"},{"1":"1115","2":"1115","3":"1402","4":"1400"},{"1":"1117","2":"1115","3":"1409","4":"1410"},{"1":"1118","2":"1120","3":"1341","4":"1340"},{"1":"1118","2":"1120","3":"1409","4":"1410"},{"1":"1121","2":"1120","3":"1421","4":"1420"},{"1":"1121","2":"1120","3":"1329","4":"1330"},{"1":"1122","2":"1120","3":"1244","4":"1245"},{"1":"1122","2":"1120","3":"1425","4":"1425"},{"1":"1122","2":"1120","3":"1330","4":"1330"},{"1":"1124","2":"1125","3":"1323","4":"1325"},{"1":"1124","2":"1125","3":"1437","4":"1435"},{"1":"1124","2":"1125","3":"1320","4":"1320"},{"1":"1124","2":"1125","3":"1238","4":"1240"},{"1":"1125","2":"1125","3":"1407","4":"1405"},{"1":"1125","2":"1125","3":"1442","4":"1440"},{"1":"1129","2":"1130","3":"1444","4":"1445"},{"1":"1130","2":"1130","3":"1431","4":"1430"},{"1":"1133","2":"1135","3":"1325","4":"1325"},{"1":"1134","2":"1135","3":"1430","4":"1430"},{"1":"1137","2":"1135","3":"1440","4":"1440"},{"1":"1138","2":"1140","3":"1258","4":"1260"},{"1":"1141","2":"1140","3":"1317","4":"1315"},{"1":"1142","2":"1140","3":"1417","4":"1415"},{"1":"1143","2":"1145","3":"1459","4":"1460"},{"1":"1143","2":"1145","3":"1430","4":"1430"},{"1":"1144","2":"1145","3":"1324","4":"1325"},{"1":"1145","2":"1145","3":"1312","4":"1310"},{"1":"1146","2":"1145","3":"1321","4":"1320"},{"1":"1149","2":"1150","3":"1623","4":"1625"},{"1":"1150","2":"1150","3":"1259","4":"1260"},{"1":"1150","2":"1150","3":"1438","4":"1440"},{"1":"1151","2":"1150","3":"1452","4":"1450"},{"1":"1152","2":"1150","3":"1328","4":"1330"},{"1":"1152","2":"1150","3":"1524","4":"1525"},{"1":"1153","2":"1155","3":"1410","4":"1410"},{"1":"1154","2":"1155","3":"1357","4":"1355"},{"1":"1155","2":"1155","3":"1258","4":"1260"},{"1":"1157","2":"1155","3":"1430","4":"1430"},{"1":"1158","2":"1160","3":"1404","4":"1405"},{"1":"1159","2":"1160","3":"1452","4":"1450"},{"1":"1200","2":"1200","3":"1307","4":"1305"},{"1":"1200","2":"1200","3":"1544","4":"1545"},{"1":"1201","2":"1200","3":"1412","4":"1410"},{"1":"1202","2":"1200","3":"1443","4":"1445"},{"1":"1203","2":"1205","3":"1307","4":"1305"},{"1":"1203","2":"1205","3":"1326","4":"1325"},{"1":"1204","2":"1205","3":"1313","4":"1315"},{"1":"1205","2":"1205","3":"1439","4":"1440"},{"1":"1207","2":"1205","3":"1430","4":"1430"},{"1":"1207","2":"1205","3":"1536","4":"1535"},{"1":"1210","2":"1210","3":"1517","4":"1515"},{"1":"1210","2":"1210","3":"1430","4":"1430"},{"1":"1210","2":"1210","3":"1410","4":"1410"},{"1":"1211","2":"1210","3":"1337","4":"1335"},{"1":"1211","2":"1210","3":"1452","4":"1450"},{"1":"1211","2":"1210","3":"1338","4":"1340"},{"1":"1215","2":"1215","3":"1435","4":"1435"},{"1":"1218","2":"1220","3":"1651","4":"1650"},{"1":"1222","2":"1220","3":"1413","4":"1415"},{"1":"1223","2":"1225","3":"1353","4":"1355"},{"1":"1224","2":"1225","3":"1540","4":"1540"},{"1":"1224","2":"1225","3":"1353","4":"1355"},{"1":"1225","2":"1225","3":"1400","4":"1400"},{"1":"1225","2":"1225","3":"1534","4":"1535"},{"1":"1226","2":"1225","3":"1401","4":"1400"},{"1":"1227","2":"1225","3":"1707","4":"1705"},{"1":"1229","2":"1230","3":"1508","4":"1510"},{"1":"1229","2":"1230","3":"1430","4":"1430"},{"1":"1233","2":"1235","3":"1526","4":"1525"},{"1":"1234","2":"1235","3":"1514","4":"1515"},{"1":"1236","2":"1235","3":"1536","4":"1535"},{"1":"1238","2":"1240","3":"1346","4":"1345"},{"1":"1240","2":"1240","3":"1346","4":"1345"},{"1":"1246","2":"1245","3":"1630","4":"1630"},{"1":"1246","2":"1245","3":"1431","4":"1430"},{"1":"1248","2":"1250","3":"1459","4":"1460"},{"1":"1249","2":"1250","3":"1349","4":"1350"},{"1":"1250","2":"1250","3":"1519","4":"1520"},{"1":"1251","2":"1250","3":"1354","4":"1355"},{"1":"1252","2":"1250","3":"1502","4":"1500"},{"1":"1252","2":"1250","3":"1439","4":"1440"},{"1":"1252","2":"1250","3":"1539","4":"1540"},{"1":"1253","2":"1255","3":"1439","4":"1440"},{"1":"1253","2":"1255","3":"1503","4":"1505"},{"1":"1255","2":"1255","3":"1359","4":"1360"},{"1":"1255","2":"1255","3":"1541","4":"1540"},{"1":"1256","2":"1255","3":"1614","4":"1615"},{"1":"1256","2":"1255","3":"1451","4":"1450"},{"1":"1257","2":"1255","3":"1437","4":"1435"},{"1":"1258","2":"1260","3":"1622","4":"1620"},{"1":"1304","2":"1305","3":"1419","4":"1420"},{"1":"1309","2":"1310","3":"1432","4":"1430"},{"1":"1312","2":"1310","3":"1608","4":"1610"},{"1":"1312","2":"1310","3":"1518","4":"1520"},{"1":"1314","2":"1315","3":"1459","4":"1460"},{"1":"1314","2":"1315","3":"1518","4":"1520"},{"1":"1315","2":"1315","3":"1613","4":"1615"},{"1":"1317","2":"1315","3":"1707","4":"1705"},{"1":"1319","2":"1320","3":"1555","4":"1555"},{"1":"1320","2":"1320","3":"1406","4":"1405"},{"1":"1320","2":"1320","3":"1621","4":"1620"},{"1":"1320","2":"1320","3":"1441","4":"1440"},{"1":"1320","2":"1320","3":"1628","4":"1630"},{"1":"1321","2":"1320","3":"1504","4":"1505"},{"1":"1321","2":"1320","3":"1651","4":"1650"},{"1":"1321","2":"1320","3":"1605","4":"1605"},{"1":"1322","2":"1320","3":"1513","4":"1515"},{"1":"1323","2":"1325","3":"1533","4":"1535"},{"1":"1324","2":"1325","3":"1624","4":"1625"},{"1":"1327","2":"1325","3":"1557","4":"1555"},{"1":"1328","2":"1330","3":"1514","4":"1515"},{"1":"1328","2":"1330","3":"1622","4":"1620"},{"1":"1328","2":"1330","3":"1511","4":"1510"},{"1":"1333","2":"1335","3":"1631","4":"1630"},{"1":"1336","2":"1335","3":"1631","4":"1630"},{"1":"1337","2":"1335","3":"1637","4":"1635"},{"1":"1337","2":"1335","3":"1456","4":"1455"},{"1":"1338","2":"1340","3":"1537","4":"1535"},{"1":"1338","2":"1340","3":"1555","4":"1555"},{"1":"1345","2":"1345","3":"1556","4":"1555"},{"1":"1347","2":"1345","3":"1621","4":"1620"},{"1":"1352","2":"1350","3":"1508","4":"1510"},{"1":"1354","2":"1355","3":"1542","4":"1540"},{"1":"1355","2":"1355","3":"1548","4":"1550"},{"1":"1356","2":"1355","3":"1649","4":"1650"},{"1":"1358","2":"1360","3":"1636","4":"1635"},{"1":"1400","2":"1400","3":"1643","4":"1645"},{"1":"1405","2":"1405","3":"1541","4":"1540"},{"1":"1405","2":"1405","3":"1556","4":"1555"},{"1":"1407","2":"1405","3":"1714","4":"1715"},{"1":"1407","2":"1405","3":"1530","4":"1530"},{"1":"1407","2":"1405","3":"1641","4":"1640"},{"1":"1408","2":"1410","3":"1511","4":"1510"},{"1":"1408","2":"1410","3":"1659","4":"1660"},{"1":"1409","2":"1410","3":"1649","4":"1650"},{"1":"1410","2":"1410","3":"1704","4":"1705"},{"1":"1410","2":"1410","3":"1550","4":"1550"},{"1":"1411","2":"1410","3":"1527","4":"1525"},{"1":"1413","2":"1415","3":"1629","4":"1630"},{"1":"1416","2":"1415","3":"1728","4":"1730"},{"1":"1420","2":"1420","3":"1704","4":"1705"},{"1":"1422","2":"1420","3":"1607","4":"1605"},{"1":"1423","2":"1425","3":"1557","4":"1555"},{"1":"1425","2":"1425","3":"1558","4":"1560"},{"1":"1425","2":"1425","3":"1656","4":"1655"},{"1":"1425","2":"1425","3":"1721","4":"1720"},{"1":"1426","2":"1425","3":"1625","4":"1625"},{"1":"1429","2":"1430","3":"1714","4":"1715"},{"1":"1431","2":"1430","3":"1740","4":"1740"},{"1":"1431","2":"1430","3":"1734","4":"1735"},{"1":"1432","2":"1430","3":"1706","4":"1705"},{"1":"1435","2":"1435","3":"1651","4":"1650"},{"1":"1436","2":"1435","3":"1731","4":"1730"},{"1":"1437","2":"1435","3":"1743","4":"1745"},{"1":"1440","2":"1440","3":"1649","4":"1650"},{"1":"1441","2":"1440","3":"1647","4":"1645"},{"1":"1442","2":"1440","3":"1749","4":"1750"},{"1":"1443","2":"1445","3":"1705","4":"1705"},{"1":"1443","2":"1445","3":"1606","4":"1605"},{"1":"1445","2":"1445","3":"1754","4":"1755"},{"1":"1445","2":"1445","3":"1603","4":"1605"},{"1":"1447","2":"1445","3":"1549","4":"1550"},{"1":"1448","2":"1450","3":"1651","4":"1650"},{"1":"1448","2":"1450","3":"1712","4":"1710"},{"1":"1449","2":"1450","3":"1747","4":"1745"},{"1":"1449","2":"1450","3":"1750","4":"1750"},{"1":"1450","2":"1450","3":"1557","4":"1555"},{"1":"1450","2":"1450","3":"1557","4":"1555"},{"1":"1451","2":"1450","3":"1551","4":"1550"},{"1":"1451","2":"1450","3":"1554","4":"1555"},{"1":"1453","2":"1455","3":"1749","4":"1750"},{"1":"1453","2":"1455","3":"1735","4":"1735"},{"1":"1453","2":"1455","3":"1707","4":"1705"},{"1":"1457","2":"1455","3":"1745","4":"1745"},{"1":"1458","2":"1460","3":"1600","4":"1600"},{"1":"1458","2":"1460","3":"1747","4":"1745"},{"1":"1459","2":"1460","3":"1801","4":"1800"},{"1":"1501","2":"1500","3":"1646","4":"1645"},{"1":"1504","2":"1505","3":"1715","4":"1715"},{"1":"1504","2":"1505","3":"1814","4":"1815"},{"1":"1504","2":"1505","3":"1801","4":"1800"},{"1":"1506","2":"1505","3":"1825","4":"1825"},{"1":"1506","2":"1505","3":"1712","4":"1710"},{"1":"1508","2":"1510","3":"1641","4":"1640"},{"1":"1509","2":"1510","3":"1827","4":"1825"},{"1":"1509","2":"1510","3":"1805","4":"1805"},{"1":"1510","2":"1510","3":"1624","4":"1625"},{"1":"1510","2":"1510","3":"1617","4":"1615"},{"1":"1510","2":"1510","3":"1615","4":"1615"},{"1":"1511","2":"1510","3":"1828","4":"1830"},{"1":"1511","2":"1510","3":"1729","4":"1730"},{"1":"1512","2":"1510","3":"1630","4":"1630"},{"1":"1513","2":"1515","3":"1724","4":"1725"},{"1":"1514","2":"1515","3":"1712","4":"1710"},{"1":"1515","2":"1515","3":"1629","4":"1630"},{"1":"1515","2":"1515","3":"1804","4":"1805"},{"1":"1517","2":"1515","3":"1635","4":"1635"},{"1":"1519","2":"1520","3":"1728","4":"1730"},{"1":"1519","2":"1520","3":"1643","4":"1645"},{"1":"1519","2":"1520","3":"1746","4":"1745"},{"1":"1520","2":"1520","3":"1744","4":"1745"},{"1":"1520","2":"1520","3":"1625","4":"1625"},{"1":"1522","2":"1520","3":"1819","4":"1820"},{"1":"1522","2":"1520","3":"1649","4":"1650"},{"1":"1523","2":"1525","3":"1833","4":"1835"},{"1":"1523","2":"1525","3":"1641","4":"1640"},{"1":"1524","2":"1525","3":"1743","4":"1745"},{"1":"1527","2":"1525","3":"1751","4":"1750"},{"1":"1527","2":"1525","3":"1718","4":"1720"},{"1":"1527","2":"1525","3":"1835","4":"1835"},{"1":"1529","2":"1530","3":"1837","4":"1835"},{"1":"1529","2":"1530","3":"1655","4":"1655"},{"1":"1529","2":"1530","3":"1903","4":"1905"},{"1":"1530","2":"1530","3":"1656","4":"1655"},{"1":"1531","2":"1530","3":"1834","4":"1835"},{"1":"1532","2":"1530","3":"1807","4":"1805"},{"1":"1533","2":"1535","3":"1814","4":"1815"},{"1":"1533","2":"1535","3":"1725","4":"1725"},{"1":"1536","2":"1535","3":"1852","4":"1850"},{"1":"1536","2":"1535","3":"1701","4":"1700"},{"1":"1540","2":"1540","3":"1727","4":"1725"},{"1":"1540","2":"1540","3":"1734","4":"1735"},{"1":"1542","2":"1540","3":"1806","4":"1805"},{"1":"1543","2":"1545","3":"1850","4":"1850"},{"1":"1543","2":"1545","3":"1855","4":"1855"},{"1":"1543","2":"1545","3":"1831","4":"1830"},{"1":"1545","2":"1545","3":"1638","4":"1640"},{"1":"1545","2":"1545","3":"1655","4":"1655"},{"1":"1545","2":"1545","3":"1713","4":"1715"},{"1":"1546","2":"1545","3":"1720","4":"1720"},{"1":"1547","2":"1545","3":"1758","4":"1760"},{"1":"1547","2":"1545","3":"1847","4":"1845"},{"1":"1547","2":"1545","3":"1746","4":"1745"},{"1":"1549","2":"1550","3":"1807","4":"1805"},{"1":"1549","2":"1550","3":"1753","4":"1755"},{"1":"1551","2":"1550","3":"1815","4":"1815"},{"1":"1553","2":"1555","3":"1930","4":"1930"},{"1":"1554","2":"1555","3":"1709","4":"1710"},{"1":"1556","2":"1555","3":"1843","4":"1845"},{"1":"1557","2":"1555","3":"1707","4":"1705"},{"1":"1558","2":"1560","3":"2020","4":"2020"},{"1":"1558","2":"1560","3":"1902","4":"1900"},{"1":"1558","2":"1560","3":"1742","4":"1740"},{"1":"1559","2":"1560","3":"1811","4":"1810"},{"1":"1559","2":"1560","3":"1848","4":"1850"},{"1":"1559","2":"1560","3":"1815","4":"1815"},{"1":"1606","2":"1605","3":"1845","4":"1845"},{"1":"1612","2":"1610","3":"1828","4":"1830"},{"1":"1613","2":"1615","3":"1929","4":"1930"},{"1":"1613","2":"1615","3":"1903","4":"1905"},{"1":"1614","2":"1615","3":"1814","4":"1815"},{"1":"1615","2":"1615","3":"1718","4":"1720"},{"1":"1615","2":"1615","3":"1744","4":"1745"},{"1":"1615","2":"1615","3":"1905","4":"1905"},{"1":"1616","2":"1615","3":"1917","4":"1915"},{"1":"1616","2":"1615","3":"1728","4":"1730"},{"1":"1616","2":"1615","3":"1721","4":"1720"},{"1":"1619","2":"1620","3":"1809","4":"1810"},{"1":"1620","2":"1620","3":"1753","4":"1755"},{"1":"1622","2":"1620","3":"1739","4":"1740"},{"1":"1622","2":"1620","3":"1833","4":"1835"},{"1":"1625","2":"1625","3":"1755","4":"1755"},{"1":"1626","2":"1625","3":"1805","4":"1805"},{"1":"1626","2":"1625","3":"1854","4":"1855"},{"1":"1626","2":"1625","3":"1725","4":"1725"},{"1":"1627","2":"1625","3":"1842","4":"1840"},{"1":"1628","2":"1630","3":"1806","4":"1805"},{"1":"1628","2":"1630","3":"1815","4":"1815"},{"1":"1629","2":"1630","3":"1910","4":"1910"},{"1":"1630","2":"1630","3":"1929","4":"1930"},{"1":"1631","2":"1630","3":"1820","4":"1820"},{"1":"1633","2":"1635","3":"2012","4":"2010"},{"1":"1633","2":"1635","3":"1938","4":"1940"},{"1":"1633","2":"1635","3":"1916","4":"1915"},{"1":"1635","2":"1635","3":"1814","4":"1815"},{"1":"1635","2":"1635","3":"1940","4":"1940"},{"1":"1636","2":"1635","3":"1844","4":"1845"},{"1":"1638","2":"1640","3":"2026","4":"2025"},{"1":"1638","2":"1640","3":"1831","4":"1830"},{"1":"1639","2":"1640","3":"1949","4":"1950"},{"1":"1640","2":"1640","3":"2010","4":"2010"},{"1":"1644","2":"1645","3":"1947","4":"1945"},{"1":"1646","2":"1645","3":"1809","4":"1810"},{"1":"1648","2":"1650","3":"2000","4":"2000"},{"1":"1650","2":"1650","3":"1834","4":"1835"},{"1":"1651","2":"1650","3":"1828","4":"1830"},{"1":"1652","2":"1650","3":"1805","4":"1805"},{"1":"1652","2":"1650","3":"1945","4":"1945"},{"1":"1653","2":"1655","3":"1952","4":"1950"},{"1":"1653","2":"1655","3":"1943","4":"1945"},{"1":"1654","2":"1655","3":"1934","4":"1935"},{"1":"1655","2":"1655","3":"1800","4":"1800"},{"1":"1655","2":"1655","3":"1802","4":"1800"},{"1":"1656","2":"1655","3":"1950","4":"1950"},{"1":"1657","2":"1655","3":"1954","4":"1955"},{"1":"1657","2":"1655","3":"1843","4":"1845"},{"1":"1657","2":"1655","3":"1931","4":"1930"},{"1":"1657","2":"1655","3":"1934","4":"1935"},{"1":"1657","2":"1655","3":"1950","4":"1950"},{"1":"1658","2":"1660","3":"1844","4":"1845"},{"1":"1659","2":"1660","3":"1913","4":"1915"},{"1":"1659","2":"1660","3":"2011","4":"2010"},{"1":"1659","2":"1660","3":"1852","4":"1850"},{"1":"1702","2":"1700","3":"2059","4":"2060"},{"1":"1703","2":"1705","3":"1918","4":"1920"},{"1":"1703","2":"1705","3":"1913","4":"1915"},{"1":"1703","2":"1705","3":"1913","4":"1915"},{"1":"1707","2":"1705","3":"1838","4":"1840"},{"1":"1709","2":"1710","3":"1924","4":"1925"},{"1":"1709","2":"1710","3":"2011","4":"2010"},{"1":"1710","2":"1710","3":"1953","4":"1955"},{"1":"1710","2":"1710","3":"1920","4":"1920"},{"1":"1710","2":"1710","3":"2014","4":"2015"},{"1":"1715","2":"1715","3":"1927","4":"1925"},{"1":"1716","2":"1715","3":"2019","4":"2020"},{"1":"1720","2":"1720","3":"2017","4":"2015"},{"1":"1722","2":"1720","3":"1845","4":"1845"},{"1":"1723","2":"1725","3":"2009","4":"2010"},{"1":"1724","2":"1725","3":"2026","4":"2025"},{"1":"1724","2":"1725","3":"2014","4":"2015"},{"1":"1725","2":"1725","3":"2031","4":"2030"},{"1":"1725","2":"1725","3":"2007","4":"2005"},{"1":"1726","2":"1725","3":"1920","4":"1920"},{"1":"1727","2":"1725","3":"2053","4":"2055"},{"1":"1728","2":"1730","3":"1854","4":"1855"},{"1":"1728","2":"1730","3":"2106","4":"2105"},{"1":"1732","2":"1730","3":"2022","4":"2020"},{"1":"1732","2":"1730","3":"2019","4":"2020"},{"1":"1733","2":"1735","3":"2059","4":"2060"},{"1":"1733","2":"1735","3":"2018","4":"2020"},{"1":"1733","2":"1735","3":"2122","4":"2120"},{"1":"1737","2":"1735","3":"1906","4":"1905"},{"1":"1739","2":"1740","3":"1911","4":"1910"},{"1":"1739","2":"1740","3":"2232","4":"2230"},{"1":"1739","2":"1740","3":"1844","4":"1845"},{"1":"1740","2":"1740","3":"2005","4":"2005"},{"1":"1740","2":"1740","3":"1923","4":"1925"},{"1":"1741","2":"1740","3":"1946","4":"1945"},{"1":"1744","2":"1745","3":"2039","4":"2040"},{"1":"1744","2":"1745","3":"2015","4":"2015"},{"1":"1745","2":"1745","3":"2047","4":"2045"},{"1":"1748","2":"1750","3":"2049","4":"2050"},{"1":"1748","2":"1750","3":"2027","4":"2025"},{"1":"1749","2":"1750","3":"2138","4":"2140"},{"1":"1749","2":"1750","3":"2053","4":"2055"},{"1":"1750","2":"1750","3":"2059","4":"2060"},{"1":"1751","2":"1750","3":"2041","4":"2040"},{"1":"1751","2":"1750","3":"2112","4":"2110"},{"1":"1752","2":"1750","3":"2102","4":"2100"},{"1":"1752","2":"1750","3":"2053","4":"2055"},{"1":"1752","2":"1750","3":"2002","4":"2000"},{"1":"1752","2":"1750","3":"1946","4":"1945"},{"1":"1754","2":"1755","3":"2033","4":"2035"},{"1":"1754","2":"1755","3":"2038","4":"2040"},{"1":"1755","2":"1755","3":"1942","4":"1940"},{"1":"1755","2":"1755","3":"2039","4":"2040"},{"1":"1756","2":"1755","3":"1925","4":"1925"},{"1":"1756","2":"1755","3":"2100","4":"2100"},{"1":"1757","2":"1755","3":"1954","4":"1955"},{"1":"1757","2":"1755","3":"2103","4":"2105"},{"1":"1759","2":"1760","3":"2017","4":"2015"},{"1":"1759","2":"1760","3":"2057","4":"2055"},{"1":"1802","2":"1800","3":"2053","4":"2055"},{"1":"1802","2":"1800","3":"2024","4":"2025"},{"1":"1803","2":"1805","3":"2057","4":"2055"},{"1":"1805","2":"1805","3":"1927","4":"1925"},{"1":"1809","2":"1810","3":"2247","4":"2245"},{"1":"1809","2":"1810","3":"2150","4":"2150"},{"1":"1813","2":"1815","3":"1951","4":"1950"},{"1":"1815","2":"1815","3":"2023","4":"2025"},{"1":"1815","2":"1815","3":"2313","4":"2315"},{"1":"1815","2":"1815","3":"2131","4":"2130"},{"1":"1818","2":"1820","3":"2221","4":"2220"},{"1":"1819","2":"1820","3":"2028","4":"2030"},{"1":"1820","2":"1820","3":"2136","4":"2135"},{"1":"1820","2":"1820","3":"2106","4":"2105"},{"1":"1820","2":"1820","3":"2014","4":"2015"},{"1":"1822","2":"1820","3":"2112","4":"2110"},{"1":"1822","2":"1820","3":"2120","4":"2120"},{"1":"1822","2":"1820","3":"2035","4":"2035"},{"1":"1822","2":"1820","3":"1924","4":"1925"},{"1":"1823","2":"1825","3":"2126","4":"2125"},{"1":"1823","2":"1825","3":"2024","4":"2025"},{"1":"1824","2":"1825","3":"2142","4":"2140"},{"1":"1825","2":"1825","3":"2143","4":"2145"},{"1":"1825","2":"1825","3":"2056","4":"2055"},{"1":"1825","2":"1825","3":"2102","4":"2100"},{"1":"1826","2":"1825","3":"2135","4":"2135"},{"1":"1828","2":"1830","3":"2240","4":"2240"},{"1":"1830","2":"1830","3":"2006","4":"2005"},{"1":"1830","2":"1830","3":"1933","4":"1935"},{"1":"1831","2":"1830","3":"2057","4":"2055"},{"1":"1832","2":"1830","3":"2201","4":"2200"},{"1":"1833","2":"1835","3":"2047","4":"2045"},{"1":"1833","2":"1835","3":"2111","4":"2110"},{"1":"1834","2":"1835","3":"2123","4":"2125"},{"1":"1837","2":"1835","3":"2235","4":"2235"},{"1":"1837","2":"1835","3":"2131","4":"2130"},{"1":"1839","2":"1840","3":"2009","4":"2010"},{"1":"1839","2":"1840","3":"2154","4":"2155"},{"1":"1839","2":"1840","3":"1945","4":"1945"},{"1":"1841","2":"1840","3":"2237","4":"2235"},{"1":"1841","2":"1840","3":"2048","4":"2050"},{"1":"1842","2":"1840","3":"2131","4":"2130"},{"1":"1845","2":"1845","3":"2235","4":"2235"},{"1":"1845","2":"1845","3":"2201","4":"2200"},{"1":"1846","2":"1845","3":"2210","4":"2210"},{"1":"1846","2":"1845","3":"2209","4":"2210"},{"1":"1848","2":"1850","3":"2136","4":"2135"},{"1":"1849","2":"1850","3":"2111","4":"2110"},{"1":"1849","2":"1850","3":"2137","4":"2135"},{"1":"1849","2":"1850","3":"1949","4":"1950"},{"1":"1849","2":"1850","3":"2101","4":"2100"},{"1":"1850","2":"1850","3":"2007","4":"2005"},{"1":"1851","2":"1850","3":"2210","4":"2210"},{"1":"1851","2":"1850","3":"2151","4":"2150"},{"1":"1852","2":"1850","3":"2045","4":"2045"},{"1":"1854","2":"1855","3":"2155","4":"2155"},{"1":"1854","2":"1855","3":"2019","4":"2020"},{"1":"1856","2":"1855","3":"2018","4":"2020"},{"1":"1900","2":"1900","3":"2035","4":"2035"},{"1":"1900","2":"1900","3":"2145","4":"2145"},{"1":"1901","2":"1900","3":"2211","4":"2210"},{"1":"1905","2":"1905","3":"2108","4":"2110"},{"1":"1911","2":"1910","3":"2158","4":"2160"},{"1":"1915","2":"1915","3":"2238","4":"2240"},{"1":"1915","2":"1915","3":"2159","4":"2160"},{"1":"1916","2":"1915","3":"2228","4":"2230"},{"1":"1922","2":"1920","3":"2050","4":"2050"},{"1":"1922","2":"1920","3":"2027","4":"2025"},{"1":"1924","2":"1925","3":"2049","4":"2050"},{"1":"1925","2":"1925","3":"2215","4":"2215"},{"1":"1926","2":"1925","3":"2305","4":"2305"},{"1":"1926","2":"1925","3":"2211","4":"2210"},{"1":"1927","2":"1925","3":"2028","4":"2030"},{"1":"1928","2":"1930","3":"2128","4":"2130"},{"1":"1929","2":"1930","3":"2059","4":"2060"},{"1":"1930","2":"1930","3":"2143","4":"2145"},{"1":"1930","2":"1930","3":"2106","4":"2105"},{"1":"1930","2":"1930","3":"2234","4":"2235"},{"1":"1933","2":"1935","3":"2214","4":"2215"},{"1":"1935","2":"1935","3":"2258","4":"2260"},{"1":"1936","2":"1935","3":"2109","4":"2110"},{"1":"1937","2":"1935","3":"2211","4":"2210"},{"1":"1940","2":"1940","3":"2102","4":"2100"},{"1":"1940","2":"1940","3":"2101","4":"2100"},{"1":"1940","2":"1940","3":"2225","4":"2225"},{"1":"1941","2":"1940","3":"2102","4":"2100"},{"1":"1942","2":"1940","3":"2226","4":"2225"},{"1":"1942","2":"1940","3":"2150","4":"2150"},{"1":"1943","2":"1945","3":"2249","4":"2250"},{"1":"1944","2":"1945","3":"2124","4":"2125"},{"1":"1946","2":"1945","3":"2118","4":"2120"},{"1":"1946","2":"1945","3":"2310","4":"2310"},{"1":"1947","2":"1945","3":"2054","4":"2055"},{"1":"1949","2":"1950","3":"2227","4":"2225"},{"1":"1949","2":"1950","3":"2224","4":"2225"},{"1":"1953","2":"1955","3":"2148","4":"2150"},{"1":"1954","2":"1955","3":"2255","4":"2255"},{"1":"1957","2":"1955","3":"2245","4":"2245"},{"1":"1957","2":"1955","3":"2055","4":"2055"},{"1":"1957","2":"1955","3":"32","4":"30"},{"1":"1958","2":"1960","3":"2147","4":"2145"},{"1":"2000","2":"2000","3":"1537","4":"1535"},{"1":"2001","2":"2000","3":"2258","4":"2260"},{"1":"2001","2":"2000","3":"2231","4":"2230"},{"1":"2002","2":"2000","3":"2102","4":"2100"},{"1":"2003","2":"2005","3":"2248","4":"2250"},{"1":"2008","2":"2010","3":"2327","4":"2325"},{"1":"2011","2":"2010","3":"2321","4":"2320"},{"1":"2012","2":"2010","3":"2346","4":"2345"},{"1":"2012","2":"2010","3":"2216","4":"2215"},{"1":"2015","2":"2015","3":"2303","4":"2305"},{"1":"2015","2":"2015","3":"2326","4":"2325"},{"1":"2016","2":"2015","3":"2350","4":"2350"},{"1":"2018","2":"2020","3":"2313","4":"2315"},{"1":"2019","2":"2020","3":"2240","4":"2240"},{"1":"2020","2":"2020","3":"2229","4":"2230"},{"1":"2021","2":"2020","3":"2154","4":"2155"},{"1":"2021","2":"2020","3":"2122","4":"2120"},{"1":"2022","2":"2020","3":"59","4":"60"},{"1":"2024","2":"2025","3":"8","4":"10"},{"1":"2027","2":"2025","3":"2312","4":"2310"},{"1":"2028","2":"2030","3":"2325","4":"2325"},{"1":"2029","2":"2030","3":"2320","4":"2320"},{"1":"2029","2":"2030","3":"2313","4":"2315"},{"1":"2029","2":"2030","3":"2312","4":"2310"},{"1":"2030","2":"2030","3":"2304","4":"2305"},{"1":"2036","2":"2035","3":"2318","4":"2320"},{"1":"2036","2":"2035","3":"5","4":"5"},{"1":"2036","2":"2035","3":"2255","4":"2255"},{"1":"2037","2":"2035","3":"2332","4":"2330"},{"1":"2039","2":"2040","3":"6","4":"5"},{"1":"2043","2":"2045","3":"2345","4":"2345"},{"1":"2046","2":"2045","3":"12","4":"10"},{"1":"2048","2":"2050","3":"139","4":"140"},{"1":"2050","2":"2050","3":"2349","4":"2350"},{"1":"2050","2":"2050","3":"2342","4":"2340"},{"1":"2051","2":"2050","3":"2214","4":"2215"},{"1":"2052","2":"2050","3":"19","4":"20"},{"1":"2053","2":"2055","3":"3","4":"5"},{"1":"2055","2":"2055","3":"2205","4":"2205"},{"1":"2055","2":"2055","3":"2337","4":"2335"},{"1":"2055","2":"2055","3":"2343","4":"2345"},{"1":"2056","2":"2055","3":"2229","4":"2230"},{"1":"2056","2":"2055","3":"2348","4":"2350"},{"1":"2057","2":"2055","3":"2334","4":"2335"},{"1":"2102","2":"2100","3":"2316","4":"2315"},{"1":"2104","2":"2105","3":"2338","4":"2340"},{"1":"2105","2":"2105","3":"2213","4":"2215"},{"1":"2109","2":"2110","3":"2212","4":"2210"},{"1":"2110","2":"2110","3":"19","4":"20"},{"1":"2112","2":"2110","3":"154","4":"155"},{"1":"2114","2":"2115","3":"39","4":"40"},{"1":"2115","2":"2115","3":"2339","4":"2340"},{"1":"2116","2":"2115","3":"2228","4":"2230"},{"1":"2116","2":"2115","3":"2251","4":"2250"},{"1":"2118","2":"2120","3":"2252","4":"2250"},{"1":"2119","2":"2120","3":"2346","4":"2345"},{"1":"2121","2":"2120","3":"36","4":"35"},{"1":"2127","2":"2125","3":"2247","4":"2245"},{"1":"2133","2":"2135","3":"2238","4":"2240"},{"1":"2133","2":"2135","3":"20","4":"20"},{"1":"2134","2":"2135","3":"14","4":"15"},{"1":"2135","2":"2135","3":"16","4":"15"},{"1":"2137","2":"2135","3":"19","4":"20"},{"1":"2143","2":"2145","3":"2245","4":"2245"},{"1":"2146","2":"2145","3":"33","4":"35"},{"1":"2149","2":"2150","3":"26","4":"25"},{"1":"2151","2":"2150","3":"39","4":"40"},{"1":"2151","2":"2150","3":"1110","4":"1110"},{"1":"2155","2":"2155","3":"2358","4":"2360"},{"1":"2155","2":"2155","3":"2316","4":"2315"},{"1":"2159","2":"2160","3":"42","4":"40"},{"1":"2200","2":"2200","3":"17","4":"15"},{"1":"2200","2":"2200","3":"2311","4":"2310"},{"1":"2200","2":"2200","3":"2333","4":"2335"},{"1":"2201","2":"2200","3":"2341","4":"2340"},{"1":"2202","2":"2200","3":"2359","4":"2360"},{"1":"2205","2":"2205","3":"2330","4":"2330"},{"1":"2206","2":"2205","3":"2307","4":"2305"},{"1":"2207","2":"2205","3":"2347","4":"2345"},{"1":"2207","2":"2205","3":"2322","4":"2320"},{"1":"2209","2":"2210","3":"55","4":"55"},{"1":"2210","2":"2210","3":"24","4":"25"},{"1":"2211","2":"2210","3":"21","4":"20"},{"1":"2212","2":"2210","3":"7","4":"5"},{"1":"2213","2":"2215","3":"2315","4":"2315"},{"1":"2221","2":"2220","3":"2339","4":"2340"},{"1":"2224","2":"2225","3":"2325","4":"2325"},{"1":"2225","2":"2225","3":"2336","4":"2335"},{"1":"2230","2":"2230","3":"2345","4":"2345"},{"1":"2231","2":"2230","3":"2338","4":"2340"},{"1":"2233","2":"2235","3":"101","4":"100"},{"1":"2234","2":"2235","3":"48","4":"50"},{"1":"2243","2":"2245","3":"317","4":"315"},{"1":"2244","2":"2245","3":"118","4":"120"},{"1":"2251","2":"2250","3":"339","4":"340"},{"1":"2305","2":"2305","3":"45","4":"45"},{"1":"2311","2":"2310","3":"134","4":"135"},{"1":"2312","2":"2310","3":"30","4":"30"},{"1":"2312","2":"2310","3":"121","4":"120"},{"1":"2317","2":"2315","3":"16","4":"15"},{"1":"2324","2":"2325","3":"23","4":"25"},{"1":"2326","2":"2325","3":"39","4":"40"},{"1":"2333","2":"2335","3":"234","4":"235"},{"1":"2346","2":"2345","3":"216","4":"215"},{"1":"2352","2":"2350","3":"436","4":"435"},{"1":"2358","2":"2360","3":"113","4":"115"},{"1":"NA","2":"NA","3":"NA","4":"NA"},{"1":"NA","2":"NA","3":"NA","4":"NA"},{"1":"NA","2":"NA","3":"NA","4":"NA"},{"1":"NA","2":"NA","3":"NA","4":"NA"},{"1":"NA","2":"NA","3":"NA","4":"NA"},{"1":"8","2":"10","3":"241","4":"240"},{"1":"12","2":"10","3":"320","4":"320"},{"1":"14","2":"15","3":"253","4":"255"},{"1":"19","2":"20","3":"303","4":"305"},{"1":"25","2":"25","3":"251","4":"250"},{"1":"27","2":"25","3":"457","4":"455"},{"1":"33","2":"35","3":"312","4":"310"},{"1":"34","2":"35","3":"147","4":"145"},{"1":"41","2":"40","3":"138","4":"140"},{"1":"49","2":"50","3":"255","4":"255"},{"1":"51","2":"50","3":"518","4":"520"},{"1":"58","2":"60","3":"239","4":"240"},{"1":"101","2":"100","3":"232","4":"230"},{"1":"104","2":"105","3":"356","4":"355"},{"1":"110","2":"110","3":"223","4":"225"},{"1":"120","2":"120","3":"419","4":"420"},{"1":"142","2":"140","3":"428","4":"430"},{"1":"506","2":"505","3":"931","4":"930"},{"1":"516","2":"515","3":"757","4":"755"},{"1":"517","2":"515","3":"756","4":"755"},{"1":"521","2":"520","3":"755","4":"755"},{"1":"543","2":"545","3":"724","4":"725"},{"1":"549","2":"550","3":"848","4":"850"},{"1":"550","2":"550","3":"744","4":"745"},{"1":"550","2":"550","3":"839","4":"840"},{"1":"551","2":"550","3":"830","4":"830"},{"1":"552","2":"550","3":"841","4":"840"},{"1":"553","2":"555","3":"807","4":"805"},{"1":"553","2":"555","3":"841","4":"840"},{"1":"555","2":"555","3":"755","4":"755"},{"1":"555","2":"555","3":"915","4":"915"},{"1":"556","2":"555","3":"847","4":"845"},{"1":"557","2":"555","3":"823","4":"825"},{"1":"558","2":"560","3":"913","4":"915"},{"1":"558","2":"560","3":"833","4":"835"},{"1":"558","2":"560","3":"702","4":"700"},{"1":"559","2":"560","3":"817","4":"815"},{"1":"559","2":"560","3":"817","4":"815"},{"1":"559","2":"560","3":"735","4":"735"},{"1":"600","2":"600","3":"847","4":"845"},{"1":"601","2":"600","3":"743","4":"745"},{"1":"602","2":"600","3":"829","4":"830"},{"1":"602","2":"600","3":"838","4":"840"},{"1":"603","2":"605","3":"751","4":"750"},{"1":"607","2":"605","3":"754","4":"755"},{"1":"607","2":"605","3":"857","4":"855"},{"1":"608","2":"610","3":"840","4":"840"},{"1":"608","2":"610","3":"937","4":"935"},{"1":"612","2":"610","3":"856","4":"855"},{"1":"612","2":"610","3":"832","4":"830"},{"1":"613","2":"615","3":"758","4":"760"},{"1":"613","2":"615","3":"744","4":"745"},{"1":"616","2":"615","3":"908","4":"910"},{"1":"617","2":"615","3":"1001","4":"1000"},{"1":"620","2":"620","3":"859","4":"860"},{"1":"620","2":"620","3":"915","4":"915"},{"1":"621","2":"620","3":"729","4":"730"},{"1":"621","2":"620","3":"803","4":"805"},{"1":"626","2":"625","3":"747","4":"745"},{"1":"627","2":"625","3":"1014","4":"1015"},{"1":"628","2":"630","3":"915","4":"915"},{"1":"629","2":"630","3":"946","4":"945"},{"1":"632","2":"630","3":"907","4":"905"},{"1":"636","2":"635","3":"1105","4":"1105"},{"1":"637","2":"635","3":"951","4":"950"},{"1":"639","2":"640","3":"915","4":"915"},{"1":"640","2":"640","3":"818","4":"820"},{"1":"641","2":"640","3":"919","4":"920"},{"1":"642","2":"640","3":"920","4":"920"},{"1":"643","2":"645","3":"805","4":"805"},{"1":"646","2":"645","3":"937","4":"935"},{"1":"646","2":"645","3":"807","4":"805"},{"1":"648","2":"650","3":"939","4":"940"},{"1":"649","2":"650","3":"958","4":"960"},{"1":"650","2":"650","3":"839","4":"840"},{"1":"651","2":"650","3":"925","4":"925"},{"1":"653","2":"655","3":"955","4":"955"},{"1":"656","2":"655","3":"957","4":"955"},{"1":"657","2":"655","3":"924","4":"925"},{"1":"657","2":"655","3":"855","4":"855"},{"1":"658","2":"660","3":"1016","4":"1015"},{"1":"658","2":"660","3":"929","4":"930"},{"1":"658","2":"660","3":"926","4":"925"},{"1":"659","2":"660","3":"839","4":"840"},{"1":"659","2":"660","3":"926","4":"925"},{"1":"659","2":"660","3":"934","4":"935"},{"1":"659","2":"660","3":"1035","4":"1035"},{"1":"700","2":"700","3":"850","4":"850"},{"1":"701","2":"700","3":"928","4":"930"},{"1":"701","2":"700","3":"808","4":"810"},{"1":"701","2":"700","3":"859","4":"860"},{"1":"702","2":"700","3":"934","4":"935"},{"1":"703","2":"705","3":"1029","4":"1030"},{"1":"704","2":"705","3":"949","4":"950"},{"1":"711","2":"710","3":"840","4":"840"},{"1":"711","2":"710","3":"1313","4":"1315"},{"1":"712","2":"710","3":"942","4":"940"},{"1":"713","2":"715","3":"1004","4":"1005"},{"1":"713","2":"715","3":"847","4":"845"},{"1":"714","2":"715","3":"1041","4":"1040"},{"1":"717","2":"715","3":"954","4":"955"},{"1":"717","2":"715","3":"1022","4":"1020"},{"1":"718","2":"720","3":"1005","4":"1005"},{"1":"719","2":"720","3":"818","4":"820"},{"1":"720","2":"720","3":"1038","4":"1040"},{"1":"721","2":"720","3":"1022","4":"1020"},{"1":"721","2":"720","3":"1108","4":"1110"},{"1":"722","2":"720","3":"856","4":"855"},{"1":"722","2":"720","3":"1036","4":"1035"},{"1":"722","2":"720","3":"931","4":"930"},{"1":"723","2":"725","3":"1037","4":"1035"},{"1":"725","2":"725","3":"1004","4":"1005"},{"1":"725","2":"725","3":"1022","4":"1020"},{"1":"726","2":"725","3":"1001","4":"1000"},{"1":"726","2":"725","3":"1005","4":"1005"},{"1":"727","2":"725","3":"1001","4":"1000"},{"1":"727","2":"725","3":"835","4":"835"},{"1":"729","2":"730","3":"1020","4":"1020"},{"1":"729","2":"730","3":"1025","4":"1025"},{"1":"729","2":"730","3":"831","4":"830"},{"1":"730","2":"730","3":"1010","4":"1010"},{"1":"732","2":"730","3":"1010","4":"1010"},{"1":"733","2":"735","3":"1013","4":"1015"},{"1":"733","2":"735","3":"1033","4":"1035"},{"1":"734","2":"735","3":"1008","4":"1010"},{"1":"734","2":"735","3":"1033","4":"1035"},{"1":"734","2":"735","3":"1052","4":"1050"},{"1":"736","2":"735","3":"1055","4":"1055"},{"1":"736","2":"735","3":"1037","4":"1035"},{"1":"738","2":"740","3":"1140","4":"1140"},{"1":"740","2":"740","3":"1036","4":"1035"},{"1":"741","2":"740","3":"1000","4":"1000"},{"1":"741","2":"740","3":"916","4":"915"},{"1":"742","2":"740","3":"1021","4":"1020"},{"1":"743","2":"745","3":"1055","4":"1055"}],"options":{"columns":{"min":{},"max":[10],"total":[4]},"rows":{"min":[10],"max":[10],"total":[435352]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


## 13.5   General Transformations
### 13.5.1    Ranks

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6NiwibmNvbCI6Niwic3VtbWFyeSI6eyJBIHRpYmJsZSI6WyI2IMOXIDYiXX19LCJyZGYiOiJINHNJQUFBQUFBQUFCblZTc1U3RE1CQjEwcVNsZ2JaSThCRXdORXNYdGpBZ1BnQ0IxSzF5RTFPaUprN2tPTkN0L0FhTS9BMGIvOUFGTmtiRTBIQjI3TFN4eEVuT3U3eTc4NzA3K2VacU92R21Ia0tvZ3h6SFFoMFhYT1RlM1Y2UEx4QnliUGl4a0lQNkFsZVFkQUpPRjg1UVlQQ05wRjBpQXc4VW50YTRsbm05Ti9nTVZMMEZ4NVpkb1l2bytGeW5tdkVtUjhXSEtpNHQrRER3VTZIU3RmNXArdFo2MzErRXZRYWJpYlFHdnhTdjYvN1hhN2YxdGhia1VweVNBcHhqV2RSc3JYWUdMSHVhMFRLZEUzYTJPdGRrUkdoQlpnelQ1WTRjNVlTRmhIS0RQZ3JMbE15aXVPQTc3akNOYVpQV1Z0T0hmcjVXSk1hd2hlU3FxbjVOMldHQ0N5MWJrMTZFT2ZidkdkVEQzOVlvNldVNWp6TUtSYlorRVB2RkZqT0lVVW1Ga21nY1BwUjBLVjVXSzl6SjZVTDBWSHZXNzhCU1YrLzVRb1ZkR1N2dUVycUlLZEhqSkhoT0VuMXpSQjZWTzRSOXlIWDRPWXNwMTNNQ1cvZzg0MWlYZUdHV2FFWk9qclovNnp0b2dDVURBQUE9In0= -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["x"],"name":[1],"type":["dbl"],"align":["right"]},{"label":["row_number(x)"],"name":[2],"type":["int"],"align":["right"]},{"label":["dense_rank(x)"],"name":[3],"type":["int"],"align":["right"]},{"label":["percent_rank(x)"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["cume_dist(x)"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["min_rank(x)"],"name":[6],"type":["int"],"align":["right"]}],"data":[{"1":"1","2":"1","3":"1","4":"0.00","5":"0.2","6":"1"},{"1":"2","2":"2","3":"2","4":"0.25","5":"0.6","6":"2"},{"1":"2","2":"3","3":"2","4":"0.25","5":"0.6","6":"2"},{"1":"3","2":"4","3":"3","4":"0.75","5":"0.8","6":"4"},{"1":"5","2":"5","3":"4","4":"1.00","5":"1.0","6":"5"},{"1":"NA","2":"NA","3":"NA","4":"NA","5":"NA","6":"NA"}],"options":{"columns":{"min":{},"max":[10],"total":[6]},"rows":{"min":[10],"max":[10],"total":[6]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


### 13.5.2    Offsets
something about shifting the data input a certain amount to it's original positions. Use for, wenn shiftig, or internal comparisons.

### 13.5.3    Consecutive identifiers
For grouping whenever a specified change appears

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-frame-begin eyJtZXRhZGF0YSI6eyJjbGFzc2VzIjpbInRibF9kZiIsInRibCIsImRhdGEuZnJhbWUiXSwibnJvdyI6MTQsIm5jb2wiOjIsInN1bW1hcnkiOnsiQSB0aWJibGUiOlsiMTQgw5cgMiJdfX0sInJkZiI6Ikg0c0lBQUFBQUFBQUJuVlEyMHJFTUJDZDlLWmJjRm5RVC9EQmx4YVcraUFvdWcvaUI0akN2c2EyMW1JM0tXMnFQdnJKNGdkc25YUm52QVFNVE03TVNjNU1jbTZ2MTFtOGpnSEFoeUFRNEllWVFuaC9kNU9jQVFRZUZnSUNtRmw4dzB1SG1GaHlUakd0cTQ4ZHJxaGU3Uk1lRVI0VG5oQ21oRXZDalBDVThKendndkNTSjhIQjc3bk9FditFOXhOL1BoUXF1U2w3VEJiVDRZNE1UTDBwK1VMVjZhRjFWTE5PdjZhc3RNL3gzbkVieC9IVGJaODNzdWYyVE1hRk5ESjk3RkNQMWRhUjdPblcxRnFoeUxOR1I0NVlkQTZ4R0pSOVNaSGtUNE42VHJLbGMrNjNxckpEeVFnMlVKQ0puSk14M2tqeWlPUlJxYXBhZmJ2UnlJZXk0YzVGK1VMcEhBMlovRWpicmxhR1A0cHNueHB0SkV2aVhEZk1URitIN1JjKzB1VWdmZ0lBQUE9PSJ9 -->

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["time"],"name":[1],"type":["dbl"],"align":["right"]},{"label":["group"],"name":[2],"type":["int"],"align":["right"]}],"data":[{"1":"0","2":"0"},{"1":"1","2":"0"},{"1":"2","2":"0"},{"1":"3","2":"0"},{"1":"5","2":"0"},{"1":"10","2":"1"},{"1":"12","2":"1"},{"1":"15","2":"1"},{"1":"17","2":"1"},{"1":"19","2":"1"},{"1":"20","2":"1"},{"1":"27","2":"2"},{"1":"28","2":"2"},{"1":"30","2":"2"}],"options":{"columns":{"min":{},"max":[10],"total":[2]},"rows":{"min":[10],"max":[10],"total":[14]},"pages":{}}}
  </script>
</div>

<!-- rnb-frame-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


###   13.5.4 Exercises
1.

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBmaW5kIDEwIG1vc3QgZGVsYXllZCBmbGlnaHRzXG5mbGlnaHRzIHw+IG11dGF0ZShcbiAgIyBhZGQgcmFua2luZyBhcyBjb2x1bW4sIHVzZSBkZXNjIHNvIG1vc3QgZGVsYXkgaXMgZmlyc3QgcGxhY2VcbiAgZGVsYXl0ZXN0ID0gbWluX3JhbmsoZGVzYyhkZXBfZGVsYXkpKVxuKSB8PlxuICAjIHNob3cgY29sdW1ucyBvZiBpbnRlcmVzdFxuICBzZWxlY3QoZGVwX2RlbGF5LCBkZWxheXRlc3QpIHw+IFxuICAjIGZpbHRlciBvbmx5IHRvcCAxMFxuICBmaWx0ZXIoZGVsYXl0ZXN0IDw9IDEwKSB8PiBcbiAgIyBvcmRlciAvIHNvcnRcbiAgYXJyYW5nZShkZWxheXRlc3QpXG5gYGAifQ== -->

```r
# find 10 most delayed flights
flights |> mutate(
  # add ranking as column, use desc so most delay is first place
  delaytest = min_rank(desc(dep_delay))
) |>
  # show columns of interest
  select(dep_delay, delaytest) |> 
  # filter only top 10
  filter(delaytest <= 10) |> 
  # order / sort
  arrange(delaytest)
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

2.    which plane `tailnum` has the worst on-time record?

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBsb29raW5nIGZvciB3b3JzdCBhcnJpdmFsIGRlbGF5XG5mbGlnaHRzIHw+IHNlbGVjdChcbiAgYXJyX2RlbGF5LFxuICB0YWlsbnVtXG4pIHw+IFxuICBhcnJhbmdlKGRlc2MoYXJyX2RlbGF5KSlcblxuIyBva2F5LCBidXQgbm90IHJlZHVjZWQgdG8gdGhlIG9uZSByb3cgSSdtIGxvb2tpbmcgZm9yXG4jIGFkZCByYW5raW5nIGNvbHVtblxuZmxpZ2h0cyB8PiBtdXRhdGUoXG4gIGFycl9kZWxheV9ybmsgPSBtaW5fcmFuayhkZXNjKGFycl9kZWxheSkpXG4pIHw+IFxuICAjIGZpbHRlciBkaXJlY3RseSwgc28gbm8gbmVlZCB0byBvcmRlclxuICBmaWx0ZXIoYXJyX2RlbGF5X3JuayA9PSAxKSB8PiBcbiAgIyBzaG93IHRhaWxudW1iZXJcbiAgc2VsZWN0KHRhaWxudW0sIGFycl9kZWxheSwgYXJyX2RlbGF5X3JuaylcblxuYGBgIn0= -->

```r
# looking for worst arrival delay
flights |> select(
  arr_delay,
  tailnum
) |> 
  arrange(desc(arr_delay))

# okay, but not reduced to the one row I'm looking for
# add ranking column
flights |> mutate(
  arr_delay_rnk = min_rank(desc(arr_delay))
) |> 
  # filter directly, so no need to order
  filter(arr_delay_rnk == 1) |> 
  # show tailnumber
  select(tailnum, arr_delay, arr_delay_rnk)

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

3.    What time of day has the *least* delay `dep_delay`?

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBuZWVkIHRvIGdyb3VwIGJ5LCBvciBhdCBsZWFzdCBzZWxlY3QgdGltZSBvZiBkYXlcbiMgYSBuZWVkIHRvIHJlZHVjZSBzb21ld2hhdCwgb3IgaXQgZ2l2ZXMgbWUgZXZlcnkgZGlmZmVyZW50IG1pbnV0ZSBhcyBhIHNpbmdlIHBvaW50XG5cbm1vc3RfZGVsYXlfaGggPC0gZmxpZ2h0cyB8PiBcbiAgIyBleHRyYWN0IGhvdXIgZnJvbSBISE1NIGZvcm1hdFxuICBtdXRhdGUoc2NoZWRfZGVwX2hoID0gc2NoZWRfZGVwX3RpbWUgJS8lIDEwMCkgfD4gXG4gICMgZ3JvdXAgYnkgc2luZ2xlIGhvdXJzXG4gIGdyb3VwX2J5KHNjaGVkX2RlcF9oaCkgfD5cbiAgIyBjYWxjdWxhdGUgbWVhbiBkZWxheVxuICBzdW1tYXJpemUoZGVsYXkgPSBtZWFuKGRlcF9kZWxheSwgbmEucm0gPSBUUlVFKSwgbiA9IG4oKSkgfD5cbiAgIyBzb3J0IGJ5IGFzY2VuZGluZyBtZWFuIGRlbGF5XG4gIGFycmFuZ2UoZGVzYyhkZWxheSkpXG5tb3N0X2RlbGF5X2hoXG5cbiMgdmlzdWFsaXplXG5tb3N0X2RlbGF5X2hoIHw+IFxuICBnZ3Bsb3QoYWVzKHNjaGVkX2RlcF9oaCwgZGVsYXkpKSArXG4gIGdlb21fcG9pbnQoYWVzKHNpemUgPSBuKSkgK1xuICBnZW9tX2xpbmUoKVxuXG4jIyBjYWxjdWxhdGVkIHRoZSBtb3N0IGRlbGF5LCBidXQgdGhlIHF1ZXN0aW9uIHdhcyBhYm91dCB0aGUgbGVhc3QgZGVsYXksIHNvIGxlYXZlIG91dCBkZXNjIGluIHRoZSBhcnJhbmdlIHBhcnRcbmxlYXN0X2RlbGF5X2hoIDwtIG1vc3RfZGVsYXlfaGggfD4gXG4gIGFycmFuZ2UoZGVsYXkpXG5sZWFzdF9kZWxheV9oaFxuXG4jIGlmIG5vdCBpbnRlcmVzdCBpbiByZWxhdGlvbiBidXQgdGhhdCBvbmUgdmFsdWUgb25seSB0cnlcbmZsaWdodHMgfD4gXG4gIG11dGF0ZShzY2hlZF9kZXBfaGggPSBzY2hlZF9kZXBfdGltZSAlLyUgMTAwKSB8PiBcbiAgZ3JvdXBfYnkoc2NoZWRfZGVwX2hoKSB8PiBcbiAgc3VtbWFyaXNlKGRlbGF5ID0gbWVhbihkZXBfZGVsYXksIG5hLnJtID0gVFJVRSkpIHw+XG4gICMgYWRkIHJhbmtpbmdcbiAgbXV0YXRlKGRlbGF5X3JuayA9IG1pbl9yYW5rKGRlbGF5KSkgfD4gIFxuICAjIGZpbHRlciBmb3IgZmlyc3QgcmFua1xuICBmaWx0ZXIoZGVsYXlfcm5rID09IDEpXG5cbiMgbWF5YmUgc2xpY2Ugd291bGQgYmUgbW9yZSBlZmZpY2llbnRcbmZsaWdodHMgfD4gXG4gIG11dGF0ZShzY2hlZF9kZXBfaGggPSBzY2hlZF9kZXBfdGltZSAlLyUgMTAwKSB8PiBcbiAgZ3JvdXBfYnkoc2NoZWRfZGVwX2hoKSB8PiBcbiAgc3VtbWFyaXNlKGRlbGF5ID0gbWVhbihkZXBfZGVsYXksIG5hLnJtID0gVFJVRSkpIHw+IFxuICBzbGljZV9taW4oZGVsYXksIG4gPSAxKVxuIyB5ZWFoLCBsb29rcyBiZXR0ZXJcbmBgYCJ9 -->

```r
# need to group by, or at least select time of day
# a need to reduce somewhat, or it gives me every different minute as a singe point

most_delay_hh <- flights |> 
  # extract hour from HHMM format
  mutate(sched_dep_hh = sched_dep_time %/% 100) |> 
  # group by single hours
  group_by(sched_dep_hh) |>
  # calculate mean delay
  summarize(delay = mean(dep_delay, na.rm = TRUE), n = n()) |>
  # sort by ascending mean delay
  arrange(desc(delay))
most_delay_hh

# visualize
most_delay_hh |> 
  ggplot(aes(sched_dep_hh, delay)) +
  geom_point(aes(size = n)) +
  geom_line()

## calculated the most delay, but the question was about the least delay, so leave out desc in the arrange part
least_delay_hh <- most_delay_hh |> 
  arrange(delay)
least_delay_hh

# if not interest in relation but that one value only try
flights |> 
  mutate(sched_dep_hh = sched_dep_time %/% 100) |> 
  group_by(sched_dep_hh) |> 
  summarise(delay = mean(dep_delay, na.rm = TRUE)) |>
  # add ranking
  mutate(delay_rnk = min_rank(delay)) |>  
  # filter for first rank
  filter(delay_rnk == 1)

# maybe slice would be more efficient
flights |> 
  mutate(sched_dep_hh = sched_dep_time %/% 100) |> 
  group_by(sched_dep_hh) |> 
  summarise(delay = mean(dep_delay, na.rm = TRUE)) |> 
  slice_min(delay, n = 1)
# yeah, looks better
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

3.A   Hour 23 has the most average delay, yet the least number of delayed flights. The most reliable highest delay would be hour 19. Maybe check cancelled flights aswell.
3.B   Hour 6 is the time with the least departement delay.

4.    What does `flights |> group_by(dest) |> filter (row_number() < 4)` do?
What does `flights |> group_by(dest) |> filter(row_number(dep_delay)) < 4`do?

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyByb3dfbnVtYmVyKCkgPCA0IGdpdmVzIG1lIHRoZSBmaXJzdCBmb3VyIHJvd3M/XG5mbGlnaHRzIHw+IFxuICAjZ3JvdXBzIGJ5IGRlc3RpbmF0aW9uXG4gIGdyb3VwX2J5KGRlc3QpIHw+IFxuICAjIGZpbHRlcnMgYWxsIHRoZSByb3dzIHRoYXQgaGF2ZSBhIHJhbmsgbGVzcyB0aGFuIDRcbiAgZmlsdGVyKHJvd19udW1iZXIoKSA8IDQpXG4jIHdoYXQgZ2V0cyByYW5rZWQ/XG5mbGlnaHRzIHw+IFxuICBncm91cF9ieShkZXN0KSB8PiBcbiAgbXV0YXRlKHJhbmsgPSByb3dfbnVtYmVyKCkpIHw+IFxuICBzZWxlY3QoeWVhciwgZGVzdCwgcmFuaykgfD5cbiAgZmlsdGVyKHJhbmsgPCA0KSB8PiBcbiAgYXJyYW5nZShkZXN0KVxuIyBnb3RjaGFcbiMgaXQgZ2l2ZXMgb3V0IHRoZSBmaXJzdCB0aHJlZSByb3dzIG9mIGVhY2ggZ3JvdXAuIEluIHRoaXMgY2FzZSBpdCBnaXZlcyB0aGUgZmlyc3QgdGhyZWUgcm93cyBmb3IgZWFjaCBkZXN0aW5hdGlvbi5cblxuIyByb3dfbnVtYmVyKHZhcmlhYmxlKSBnaXZlcyB0aGUgZm91ciBoaWdoZXN0IGRlcF9kZWxheSBmb3IgZWFjaCBkZXN0aW5hdGlvbi5cblxuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD4gXG4gIGZpbHRlcihyb3dfbnVtYmVyKGRlc2MoZGVwX2RlbGF5KSkgPCA0KSB8PiBcbiAgIyBhcnJhbmdlIGJ5IGRlc3RpbmF0aW9uIHRvIGNoZWNrIGl0IHRoZXJlIGFyZSB0aHJlZSByb3cgZWFjaFxuICBhcnJhbmdlKGRlc3QsIGRlc2MoZGVwX2RlbGF5KSkgfD4gXG4gIHNlbGVjdChkZXN0LCBkZXBfZGVsYXkpXG5cbmBgYCJ9 -->

```r
# row_number() < 4 gives me the first four rows?
flights |> 
  #groups by destination
  group_by(dest) |> 
  # filters all the rows that have a rank less than 4
  filter(row_number() < 4)
# what gets ranked?
flights |> 
  group_by(dest) |> 
  mutate(rank = row_number()) |> 
  select(year, dest, rank) |>
  filter(rank < 4) |> 
  arrange(dest)
# gotcha
# it gives out the first three rows of each group. In this case it gives the first three rows for each destination.

# row_number(variable) gives the four highest dep_delay for each destination.

flights |> 
  group_by(dest) |> 
  filter(row_number(desc(dep_delay)) < 4) |> 
  # arrange by destination to check it there are three row each
  arrange(dest, desc(dep_delay)) |> 
  select(dest, dep_delay)

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

5.    For each destination, compute the total minutes of delay. For each flight, compute the proportion of the total delay for its destination.

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBUb3RhbCBkZWxheSBwZXIgZGVzdFxuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD4gXG4gIHN1bW1hcmlzZSh0b3RhbF9kZWxheSA9IHN1bShkZXBfZGVsYXksIG5hLnJtID0gVFJVRSkpXG5cbiMgcHJvcG9ydGlvbiBvZiB0b3RhbCBkZWxheSBmb3IgZWFjaCBmbGlnaHRzIGRlc3RpbmF0aW9uXG5mbGlnaHRzIHw+IFxuICBncm91cF9ieShkZXN0KSB8PiBcbiAgbXV0YXRlKHN1bV9kZWxheSA9IHN1bShkZXBfZGVsYXksIG5hLnJtID0gVFJVRSksXG4gICAgICAgICBwcm9wX2RlbGF5ID0gZGVwX2RlbGF5IC8gc3VtX2RlbGF5KSB8PiBcbiAgc2VsZWN0KGRlc3QsIHN1bV9kZWxheSwgcHJvcF9kZWxheSwgZGVwX2RlbGF5KSB8PiBcbiAgYXJyYW5nZShkZXN0KVxuIyB0aGF0J3MgZm9yIGV2ZXJ5IHNpbmdsZSBmbGlnaHRcblxuIyB0cnkgZm9yIGVhY2ggdGFpbG51bVxuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD5cbiAgbXV0YXRlKGRlc3RfZGVsID0gc3VtKGRlcF9kZWxheSwgbmEucm0gPSBUUlVFKSkgfD4gXG4gIGdyb3VwX2J5KHRhaWxudW0sIGRlc3QpIHw+IFxuICBzdW1tYXJpemUoXG4gICAgcHJvcF9kZWwgPSBzdW0oZGVwX2RlbGF5LG5hLnJtID0gVFJVRSkgLyBtZWFuKGRlc3RfZGVsKSxcbiAgICBzdW1fZGVsID0gbWVhbihkZXN0X2RlbCkpIHw+XG4gIGFycmFuZ2UoZGVzdClcbiNzZWVtcyBzZW5zaWJsZSwgYnV0IGRvZXNuJ3QgZmVlbCBzbW9vdGhcbiNzaG91bGQgY2hlY2ssIGlmIHRoZXkgY29tcHV0ZSB0byAxLCBzb21lZGF5IG1heWJlXG5cbmBgYCJ9 -->

```r
# Total delay per dest
flights |> 
  group_by(dest) |> 
  summarise(total_delay = sum(dep_delay, na.rm = TRUE))

# proportion of total delay for each flights destination
flights |> 
  group_by(dest) |> 
  mutate(sum_delay = sum(dep_delay, na.rm = TRUE),
         prop_delay = dep_delay / sum_delay) |> 
  select(dest, sum_delay, prop_delay, dep_delay) |> 
  arrange(dest)
# that's for every single flight

# try for each tailnum
flights |> 
  group_by(dest) |>
  mutate(dest_del = sum(dep_delay, na.rm = TRUE)) |> 
  group_by(tailnum, dest) |> 
  summarize(
    prop_del = sum(dep_delay,na.rm = TRUE) / mean(dest_del),
    sum_del = mean(dest_del)) |>
  arrange(dest)
#seems sensible, but doesn't feel smooth
#should check, if they compute to 1, someday maybe

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->


6.    Use `lag()`, explore how the average flight delay for an hour is related to the average delay for the previous hour.

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuZmxpZ2h0cyB8PiBcbiAgbXV0YXRlKGhvdXIgPSBkZXBfdGltZSAlLyUgMTAwKSB8PiBcbiAgZ3JvdXBfYnkoeWVhciwgbW9udGgsIGRheSwgaG91cikgfD4gXG4gIHN1bW1hcml6ZShcbiAgICBkZXBfZGVsYXkgPSBtZWFuKGRlcF9kZWxheSwgbmEucm0gPSBUUlVFKSxcbiAgICBuID0gbigpLFxuICAgIC5ncm91cHMgPSBcImRyb3BcIlxuICApIHw+IFxuICBmaWx0ZXIobiA+IDUpIHw+IFxuICAjIGFkZCBhIGxhZyBsaW5lIHRvIGJlIGNvbXBhcmVkIHRvXG4gIG11dGF0ZShsYWdsaW5lID0gbGFnKGRlcF9kZWxheSxcbiAgICAgICAgICAgICAjZGVmYXVsdCB0byBjYW5jZWwgTkEgZm9yIGZpcnN0IHJvd1xuICAgICAgICAgICAgIGRlZmF1bHQgPSBmaXJzdChkZXBfZGVsYXkpKVxuICAgICAgICAgKSB8PiBcbiAgIyBjYWxjdWxhdGUgZGlmZmVyZW5jZSBmcm9tIHRoYXRcbiAgbXV0YXRlKG92ZXJoYW5nID0gZGVwX2RlbGF5IC0gbGFnbGluZSlcblxuIyBzaG91bGQgZ3JvdXAgYnkgaG91cnMgdG8gZ2V0IG1vcmUgbWVhbmluZ2Z1bCB2YWx1ZXNcbmZsaWdodHMgfD4gXG4gIG11dGF0ZShob3VyID0gZGVwX3RpbWUgJS8lIDEwMCkgfD4gXG4gIGdyb3VwX2J5KHllYXIsIG1vbnRoLCBkYXksIGhvdXIpIHw+IFxuICBzdW1tYXJpemUoXG4gICAgZGVwX2RlbGF5ID0gbWVhbihkZXBfZGVsYXksIG5hLnJtID0gVFJVRSksXG4gICAgbiA9IG4oKSxcbiAgICAuZ3JvdXBzID0gXCJkcm9wXCJcbiAgKSB8PiBcbiAgZmlsdGVyKG4gPiA1KSB8PiBcbiAgI2dyb3VwIGJ5IGhvdXIsIGFzIGRlcF9kZWxheSB3YXMgY2FsY3VsYXRlZCBmb3IgZWFjaCBkYXlcbiAgZ3JvdXBfYnkoaG91cikgfD4gXG4gIHN1bW1hcmlzZShcbiAgICBtZWFuX2RlbGF5ID0gbWVhbihkZXBfZGVsYXksIG5hLnJtID0gVFJVRSlcbiAgKSB8PiBcbiAgIyBjcmVhdGUgb2Zmc2V0IGNvbHVtbnNcbiAgbXV0YXRlKFxuICAgIHJlc2lkdWFsX2RlbGF5ID0gbWVhbl9kZWxheSAtIGxhZyhcbiAgICAgIG1lYW5fZGVsYXksXG4gICAgICAjIGNhbmNlbCBOQSBmb3IgZmlyc3Qgcm93XG4gICAgICBkZWZhdWx0ID0gbGFzdChtZWFuX2RlbGF5LCBuYV9ybSA9IFRSVUUpXG4gICAgICApLFxuICAgICMgY2hlY2sgcHJvcG9ydGlvblxuICAgIHByb3BfcmVzaWR1YWxfZGVsYXkgPSByZXNpZHVhbF9kZWxheSAvIG1lYW5fZGVsYXlcbiAgKVxuYGBgIn0= -->

```r
flights |> 
  mutate(hour = dep_time %/% 100) |> 
  group_by(year, month, day, hour) |> 
  summarize(
    dep_delay = mean(dep_delay, na.rm = TRUE),
    n = n(),
    .groups = "drop"
  ) |> 
  filter(n > 5) |> 
  # add a lag line to be compared to
  mutate(lagline = lag(dep_delay,
             #default to cancel NA for first row
             default = first(dep_delay))
         ) |> 
  # calculate difference from that
  mutate(overhang = dep_delay - lagline)

# should group by hours to get more meaningful values
flights |> 
  mutate(hour = dep_time %/% 100) |> 
  group_by(year, month, day, hour) |> 
  summarize(
    dep_delay = mean(dep_delay, na.rm = TRUE),
    n = n(),
    .groups = "drop"
  ) |> 
  filter(n > 5) |> 
  #group by hour, as dep_delay was calculated for each day
  group_by(hour) |> 
  summarise(
    mean_delay = mean(dep_delay, na.rm = TRUE)
  ) |> 
  # create offset columns
  mutate(
    residual_delay = mean_delay - lag(
      mean_delay,
      # cancel NA for first row
      default = last(mean_delay, na_rm = TRUE)
      ),
    # check proportion
    prop_residual_delay = residual_delay / mean_delay
  )
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

7.    Suspiciously fast flights

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBmaW5kIHN1cyBmbGlnaHRzXG5mbGlnaHRzIHw+XG4gIGdyb3VwX2J5KGRlc3QpIHw+XG4gIG11dGF0ZShkZXN0X21lYW4gPSBtZWFuKGFpcl90aW1lLCBuYS5ybSA9IFRSVUUpLFxuICAgICAgICAgLmdyb3VwcyA9IFwiZHJvcFwiKSB8PlxuICBtdXRhdGUocHJvcF9zcGVlZCA9IGFpcl90aW1lIC8gZGVzdF9tZWFuKSB8PlxuICBhcnJhbmdlKHByb3Bfc3BlZWQpIHw+XG4gIHNlbGVjdChwcm9wX3NwZWVkLCBhaXJfdGltZSwgZGVzdF9tZWFuLCBkZXN0KVxuICBcbiMgY29tcHV0ZSBhaXIgdGltZSByZWxhdGl2ZSB0byBzaG9ydGVzdCBmbGlnaHQgdG8gdGhhdCBkZXN0aW5hdGlvblxuZmxpZ2h0cyB8PlxuICBncm91cF9ieShkZXN0KSB8PlxuICBtdXRhdGUoZmFzdGVzdCA9IG1pbihhaXJfdGltZSksIC5ncm91cHMuID0gXCJkcm9wXCIpIHw+XG4gIG11dGF0ZShwcm9wX2Zhc3Rlc3QgPSBhaXJfdGltZSAvIGZhc3Rlc3QpIHw+XG4gIGFycmFuZ2UocHJvcF9mYXN0ZXN0LCBkZXN0KSB8PlxuICBzZWxlY3QoZmxpZ2h0LCBkZXN0LCBwcm9wX2Zhc3Rlc3QsIGFpcl90aW1lKVxuXG4jIHdoaWNoIGZsaWdodHMgd2VyZSB0aGUgbW9zdCBkZWxheWVkIGluIHRoZSBhaXI/XG5mbGlnaHRzIHw+XG4gIGdyb3VwX2J5KGZsaWdodCkgfD5cbiAgbXV0YXRlKG1lYW5fYWlyID0gbWVhbihhaXJfdGltZSwgbmEucm0gPSBUUlVFKSxcbiAgICAgICAgIC5ncm91cHMgPSBcImRyb3BcIikgfD5cbiAgbXV0YXRlKFxuICAgIGRlbGF5X3Byb3AgPSAoYWlyX3RpbWUgLyBtZWFuX2FpciksXG4gICAgZGVsYXlfdGltZSA9IChhaXJfdGltZSAtIG1lYW5fYWlyKVxuICApIHw+XG4gIGFycmFuZ2UoZGVzYyhkZWxheV9wcm9wKSkgfD5cbiAgc2VsZWN0KGZsaWdodCwgZGVzdCwgZGVsYXlfcHJvcCwgbWVhbl9haXIsIGFpcl90aW1lLCBkZWxheV90aW1lKVxuXG5gYGAifQ== -->

```r
# find sus flights
flights |>
  group_by(dest) |>
  mutate(dest_mean = mean(air_time, na.rm = TRUE),
         .groups = "drop") |>
  mutate(prop_speed = air_time / dest_mean) |>
  arrange(prop_speed) |>
  select(prop_speed, air_time, dest_mean, dest)
  
# compute air time relative to shortest flight to that destination
flights |>
  group_by(dest) |>
  mutate(fastest = min(air_time), .groups. = "drop") |>
  mutate(prop_fastest = air_time / fastest) |>
  arrange(prop_fastest, dest) |>
  select(flight, dest, prop_fastest, air_time)

# which flights were the most delayed in the air?
flights |>
  group_by(flight) |>
  mutate(mean_air = mean(air_time, na.rm = TRUE),
         .groups = "drop") |>
  mutate(
    delay_prop = (air_time / mean_air),
    delay_time = (air_time - mean_air)
  ) |>
  arrange(desc(delay_prop)) |>
  select(flight, dest, delay_prop, mean_air, air_time, delay_time)

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

8. Carrier Ranking

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBmaW5kIGRlc3QgdGhhdCBoYXZlIGF0IGxlYXN0IHR3byBjYXJyaWVyc1xuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD5cbiAgZmlsdGVyKG5fZGlzdGluY3QoY2FycmllcikgPiAxKSB8PiBcbiAgZ3JvdXBfYnkoZGVzdCwgY2FycmllcikgfD5cbiAgc3VtbWFyaXNlKGRlbGF5X3BfYWlydGltZSA9IG1lYW4oZGVwX2RlbGF5IC8gYWlyX3RpbWUsICBuYS5ybSA9IFRSVUUpKSB8PlxuICBhcnJhbmdlKGRlc3QsIGRlbGF5X3BfYWlydGltZSlcbiMgc3RpbGwgdWdseSB3aXRoIHRoZSBtYW55IGRpZ2l0cywgYnV0IHdvcmtzLlxuICBcbmBgYCJ9 -->

```r
# find dest that have at least two carriers
flights |> 
  group_by(dest) |>
  filter(n_distinct(carrier) > 1) |> 
  group_by(dest, carrier) |>
  summarise(delay_p_airtime = mean(dep_delay / air_time,  na.rm = TRUE)) |>
  arrange(dest, delay_p_airtime)
# still ugly with the many digits, but works.
  
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

##    13.6 Numeric summaries
`mean()` might be inacurate when data is skewed.
`median()` finds the point that splits all the obersvatios in half and is less prone to skewed data

use `min()` and `max()` with outliers in mind. If Data has outliers try `quantile()´ to find those values that are just higher or lower as e.g. 95% of the data.

calculate *spread* with `sd()` or `IQR()`, to either check how the values diverge on average from the average, or which value range represents e.g. 50% of the data.

*distribution* means which "shape" the values have if plotted. Bias or Skew, aswell as normal, or other distributions can be seen here. Helpful to see which computation would be applicable for the dataset.

###   13.6.7 Exercises
1.    brainstorm at least 5 ways to asses delay characteristics of flights
  a.    standard deviation of delay for each flight, as it compares the individual values with the mean
  b.    compare mean delays of flights with overall mean delay
  c.    check the difference between arrival and departure delay so see where flights have the most trouble
  d.    check the means throughout the year
  e.    if there a heavy outliers maybe use median or even IQR
  f.    check mean delay for flights and destinations, to see whether the airport might be the issue
  g.    use `planes` data to find correlations between delay and for e.g. manufacture year or seat number.

2.    Which dest has greatest var in airspeed?

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuIyBjYWxjdWxhdGUgYWlyIHNwZWVkIGZyb20gZGlzdGFuY2UvYWlyX3RpbWVcbmZsaWdodHMgfD5cbiAgZ3JvdXBfYnkoZGVzdCwgZmxpZ2h0KSB8PlxuICBzdW1tYXJpc2UoYWlyX3RpbWUgPSBtZWFuKGRpc3RhbmNlIC8gYWlyX3RpbWUsIG5hLnJtID0gVFJVRSksIG4oKSkgfD5cbiAgc3VtbWFyaXNlKHNkX2Fpcl90aW1lID0gc2QoYWlyX3RpbWUsIG5hLnJtID0gVFJVRSksIG4gPSBuKCkpIHw+XG4gIGFycmFuZ2UoZGVzYyhzZF9haXJfdGltZSkpXG4jIyBpIGNhbiBkbyBiZXR0ZXJcbmZsaWdodHMgfD4gXG4gIGdyb3VwX2J5KGRlc3QpIHw+IFxuICBzdW1tYXJpc2Uoc2RfYWlyX3RpbWUgPSBzZChkaXN0YW5jZSAvIGFpcl90aW1lLCBuYS5ybSA9IFRSVUUpLCBuID0gbigpKSB8PiBcbiAgYXJyYW5nZShkZXNjKHNkX2Fpcl90aW1lKSlcbiMjIGdldHRpbmcgZXZlbiBzb21lIG90aGVyIHZhbHVlcywgaW50ZXJlc3RpbmcsIGJ1dCBhdCBsZWFzdCB0aGUgc2FtZSBhbW91bnQgb2YgZGVzdGluYXRpb25zIDotKVxuIyMjIGNvbXBhcmUgU0QgYW5kIElRUlxuZmxpZ2h0cyB8PiBcbiAgZ3JvdXBfYnkoZGVzdCkgfD4gXG4gIHN1bW1hcmlzZShzZF9haXJfdGltZSA9IHNkKGRpc3RhbmNlIC8gYWlyX3RpbWUsIG5hLnJtID0gVFJVRSksXG4gICAgICAgICAgICBJUVJfYWlyX3RpbWUgPSBJUVIoZGlzdGFuY2UgLyBhaXJfdGltZSwgbmEucm0gPSBUUlVFKSxcbiAgICAgICAgICAgIG4gPSBuKCkpIHw+IFxuICBhcnJhbmdlKGRlc2Moc2RfYWlyX3RpbWUpKVxuXG4jIHRyeSB0byBhY2Nlc3MgZGlmZmVyZW50IGRmXG5mbGlnaHRzIHw+IFxuICBncm91cF9ieShkZXN0KSB8PiBcbiAgc3VtbWFyaXNlKHNkX3NwZWVkID0gc2QocGxhbmVzJHNwZWVkKSlcbiMjIHllYWggbm8gd2F5IHRvIGZpbmQgdGhlIGNvcnJlc3BvbmRpbmcgcGxhbmUgbGlrZSB0aGlzLCBzbyBkaXN0YW5jZSAvIGFpcnRpbWUgaXQgaXMuXG5cbiMgbm93IG1ha2UgdGhlIHNjYWxlIGZvciBzcGVlZCB0byBtcGhcbmZsaWdodHMgfD4gXG4gIGdyb3VwX2J5KGRlc3QpIHw+IFxuICBzdW1tYXJpc2Uoc2RfbXBoID0gc2QoZGlzdGFuY2UgLyAoYWlyX3RpbWUgLyA2MCksIG5hLnJtID0gVFJVRSksXG4gICAgICAgICAgICBtZWFuX21waCA9IG1lYW4oZGlzdGFuY2UgLyAoYWlyX3RpbWUgLyA2MCksIG5hLnJtID0gVFJVRSkpIHw+ICMgZmluZCB0b3AgMTBcbiAgc2xpY2VfbWF4KG9yZGVyX2J5ID0gc2RfbXBoLCBuID0gMTApICMgc2xpY2UgbWF4IGFscmVhZHkgdXNlcyB0aGUgZGVzYyBvcmRlciwgbmljZSFcbiAgXG5gYGAifQ== -->

```r
# calculate air speed from distance/air_time
flights |>
  group_by(dest, flight) |>
  summarise(air_time = mean(distance / air_time, na.rm = TRUE), n()) |>
  summarise(sd_air_time = sd(air_time, na.rm = TRUE), n = n()) |>
  arrange(desc(sd_air_time))
## i can do better
flights |> 
  group_by(dest) |> 
  summarise(sd_air_time = sd(distance / air_time, na.rm = TRUE), n = n()) |> 
  arrange(desc(sd_air_time))
## getting even some other values, interesting, but at least the same amount of destinations :-)
### compare SD and IQR
flights |> 
  group_by(dest) |> 
  summarise(sd_air_time = sd(distance / air_time, na.rm = TRUE),
            IQR_air_time = IQR(distance / air_time, na.rm = TRUE),
            n = n()) |> 
  arrange(desc(sd_air_time))

# try to access different df
flights |> 
  group_by(dest) |> 
  summarise(sd_speed = sd(planes$speed))
## yeah no way to find the corresponding plane like this, so distance / airtime it is.

# now make the scale for speed to mph
flights |> 
  group_by(dest) |> 
  summarise(sd_mph = sd(distance / (air_time / 60), na.rm = TRUE),
            mean_mph = mean(distance / (air_time / 60), na.rm = TRUE)) |> # find top 10
  slice_max(order_by = sd_mph, n = 10) # slice max already uses the desc order, nice!
  
```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->

3.    Explore EGE. Did Airport move location? Find another Variable to explain distance difference.

<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxubGlicmFyeShueWNmbGlnaHRzMjMpXG5mbGlnaHRzIHw+IFxuICBmaWx0ZXIoZGVzdCA9PSBcIkVHRVwiKSB8PiBcbiAgZ2dwbG90KGFlcyh4ID0gbW9udGgsIHkgPSBkaXN0YW5jZSwgY29sb3IgPSBvcmlnaW4pKSArIFxuICBnZW9tX3BvaW50KClcbiMgYWhoIG1heWJlIGluIDIwMjMgdGhlcmUgaXMgbm8gZGlmZmVyZW5jZSBhbnltb3JlXG4jIGxvYWQgZmxpZ2h0czIyXG5saWJyYXJ5KG55Y2ZsaWdodHMxMylcbmZsaWdodHMgfD4gXG4gIGZpbHRlcihkZXN0ID09IFwiRUdFXCIpIHw+IFxuICBnZ3Bsb3QoYWVzKHggPSBtb250aCwgeSA9IGRpc3RhbmNlLCBjb2xvciA9IG9yaWdpbikpICsgXG4gIGdlb21fcG9pbnQoKVxuIyBiZXR3ZWVuIGphbnVhcnkgYW5kIGZlYnJ1YXJ5IHRoZSBkaXN0YW5jZSBjaGFuZ2VkXG4jIGNoZWNrIHRoZSBhaXJwb3J0cyBkZlxuP2FpcnBvcnRzXG4jbGF0LCBsb24gc2VlIHdoYXQgY2hhbmdlZFxuYWlycG9ydHMgfD4gXG4gIGZpbHRlcihmYWEgPT0gXCJFR0VcIilcbiMgbm8gb25seSBvbmUgZW50cnlcblxuIyBkb24ndCBrbm93IHdoaWNoIG90aGVyIHZhcmlhYmxlIG1pZ2h0IGhhdmUgbWVhbmluZ1xuIyBjYXJyaWVyIG1heWJlP1xuZmxpZ2h0cyB8PiBcbiAgZmlsdGVyKGRlc3QgPT0gXCJFR0VcIikgfD4gXG4gIGdncGxvdChhZXMoeCA9IG1vbnRoLCB5ID0gbl9kaXN0aW5jdCh0YWlsbnVtKSkpICsgXG4gIGdlb21fcG9pbnQoKVxuIyBpIGRvbnQga25vd1xuXG5gYGAifQ== -->

```r
library(nycflights23)
flights |> 
  filter(dest == "EGE") |> 
  ggplot(aes(x = month, y = distance, color = origin)) + 
  geom_point()
# ahh maybe in 2023 there is no difference anymore
# load flights22
library(nycflights13)
flights |> 
  filter(dest == "EGE") |> 
  ggplot(aes(x = month, y = distance, color = origin)) + 
  geom_point()
# between january and february the distance changed
# check the airports df
?airports
#lat, lon see what changed
airports |> 
  filter(faa == "EGE")
# no only one entry

# don't know which other variable might have meaning
# carrier maybe?
flights |> 
  filter(dest == "EGE") |> 
  ggplot(aes(x = month, y = n_distinct(tailnum))) + 
  geom_point()
# i dont know

```

<!-- rnb-source-end -->

<!-- rnb-chunk-end -->


<!-- rnb-text-begin -->






<!-- rnb-text-end -->

