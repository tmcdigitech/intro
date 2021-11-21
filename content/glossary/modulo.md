---
title: modulo %
---

When we are dividing numbers, typically we want
to know the answer as a decimal (assuming things
don't divide exactly), but often we want to know
the answer with a remainder. For example,
{{< katex >}}6\div4=1.5{{< /katex >}},
but we could also express it as{{< katex >}}
6\div4=1\ \textrm{rem}\ 2{{< /katex >}}.
The **modulo** operator (`%` in nearly every
language) will return the remainder part of a
division, so `6 % 4` &rarr; `2`.

In Python, you can also find the whole number part of the quotient using a double division sign, `//`, so `6 // 4` &rarr; `1`. And a single division sign will give you the answer as a decimal, so `6 / 4` &rarr; `1.5`.

So in summary:

- {{< katex >}}6\div4=1.5{{< /katex >}}, and
    - `6 / 4` evaluates to `1.5`,

- {{< katex >}}6\div4=1\ \textrm{rem}\ 2{{< /katex >}}, and
    - `6 // 4` evaluates to `1`, and
    - `6 % 4` evaluates to `2`.

## Use in timing/counting loops

Modulo is used often in loops to create timers.

Consider this code fragment:
```python
print("i, i%4")
print("------")
for i in range(10):
    print(f"{i}, {i%4}")
```

The output will be:
```plain
i | i%4
-------
0 | 0
1 | 1
2 | 2
3 | 3
4 | 0
5 | 1
6 | 2
7 | 3
8 | 0
9 | 1
```

You can see that the value of i%4 cycles between the values `0`, `1`, `2`, `3`.

We can use this in a loop to trigger an event every *n* cycles.

To print out the first 100 numbers, but print
*buzz* every 7th instead, we could do this:
```python
for i in range(100):
    if i%7 == 0:
        print("buzz")
    else:
        print(i)
```

If you have an infinite loop, you can use a similar approach to have any number of timers which operate independently:

```python
timer1 = 0
timer2 = 0
while True:
    # some loop body code ...

    if timer1==0:
        print('tick')
    
    if timer2==0:
        print('tock')

    # ... more loop body code ...

    # ...

    # ... at the bottom of the loop
    timer1 = (timer1 + 1) % 7
    timer2 = (timer2 + 1) % 13
```

Here `timer1` will reset every 7 cycles
(and hence trigger the `print('tick')` line),
and `timer2` will reset every 13 cycles
(and hence trigger the `print('tock')` line).