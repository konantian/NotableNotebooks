---
title: 'Lecture 6 - Profiling python3 code, improving the performance'
tags: [Notebooks/Cmput 496]
created: '2019-04-11T00:55:23.350Z'
modified: '2019-04-11T19:03:21.978Z'
---

# Lecture 6 - Profiling python3 code, improving the performance
### Limits of Optimization
  * 80% of the improvement can come from 20% of the code
  * Amdahl's Law 
  $\text { limit }=\frac{1}{(1-p)+p / s}$
    * p = percentage of program that is speeded up(被优化部分运行时间所占总程序运行时间的比例)
    * s = speedup for that part(被优化部分速度提升的程度)
  * Example:
  80% of program speeded up,so p = 0.8
  s = 100 speedup for the optimized function
  Speedup limit for the whole program:
  $\text { limit }=\frac{1}{(1-p)+p / s}=\frac{1}{(1-0.8)+0.8 / 100} \approx 4.81$
  * Simplified version:
  $\text { limit } \approx \frac{1}{1-p}=5$


### Profiling
  * Profiler can be on the function level or instruction level
  * Ver few optimization are win-win. The speed foten comes at the cost of code complexity
  * Knuth: Premature optimization is the root of all evil
