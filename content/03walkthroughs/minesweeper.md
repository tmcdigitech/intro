---
title: Minesweeper
weight: 9
---

Minesweeper originated in the 1960s but reached an enormous audience when a port was included in the standard install of Windows 3.1 in 1992.

{{< figure caption="Minesweeper, as seen in Windows 98" src="https://upload.wikimedia.org/wikipedia/en/3/31/Minesweeper_in_Windows_98_Expert_Level.png" >}}

Here is a link to [Google's web-based implementation](https://g.co/kgs/ygYsnr).

# Keeping track of the board

This game will keep track of the board state using
text.

At the start of the game, the board will only contain ` ` (a safe square) and `x` (a bomb). The user can assert that a square is safe, or that it has a bomb. If they assert it has a bomb, we won't tell them if they are wrong or right, but we need to keep track of it ourselves. We replace:
- `.` with `?` (a safe square that they think has a bomb), and
- `x` with `X` (a bomb square that they think has a bomb).

If they assert that a square is safe, either it was a safe square, and we replace:
- `.` with `o`,

or they have triggered a bomb, and the game ends.

Here is a possible 10x10 board in its initial state:

```python
board = ["......x...",
         ".x........",
         ".x.....x..",
         "..........",
         "....x.....",
         "....xx....",
         "..........",
         "..x....x..",
         ".....x...."]
```

We can now try drawing the board.

```

```
