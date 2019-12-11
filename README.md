# SudokuNCExplainer

SudokuNCExplainer is my modifications to SudokuExplainer to also solve (and rate) Non-Consecutive sudokus (SudokuNC).

SudokuNCExplainer solves most SudokuNCs, i.e. those that require only sudoku solving techniques.

SudokuNCExplainer does **not** solve more difficult SudokuNCs, specially those that require NC solving techniques.

SudokuNCExplainer can generate a puzzle<sup>1</sup>, the Symmetry type is set to None, and the Difficulty level is set to Diabolical at Maximum difficulty - it takes many minutes to generate a SudokuNC puzzle - be patient ...

Also, the generated puzzles have unique solutions, **but they are not minimal** - because of changes to the generator code, and some very slow Nested Forcing Chains techniques have been commented out.

Finally, some GUI functionality applies well to Sudoku grids, but less well to Sudoku NC grids, e.g. Analyse (F9), Check Validity button - both can give erroneous results!

## Usage - GUI
java.exe -jar SudokuNCExplainer.jar

![](/images/sample1.jpg)

The puzzle is taken from [here](http://forum.enjoysudoku.com/djape-sample-non-consecutive-t33093.html):
```
.7.....4..........69.....251.......7..47536..3.......291.....36..........3.....9. ED=1.2/1.2/1.2
```

## Usage - serate
java.exe -Xrs -Xmx500m -cp SudokuNCExplainer.jar diuf.sudoku.test.serate --format="%g ED=%r/%p/%d" --input=puzzles.txt --output=output.txt

## Usage - hints
java.exe -Xrs -Xmx500m -cp SudokuNCExplainer.jar diuf.sudoku.test.hints --input=puzzle.txt

## Usage - pencilmarks
java.exe -Xrs -Xmx500m -cp SudokuNCExplainer.jar diuf.sudoku.test.pencilmarks --input=puzzle.txt


## Sudoku NC Solving Techniques

Pair Consecutive Claimimg
```
     C1   C2   C3
   +----------------+-
R1 | 678  78   378  |
R2 | 4    2    5    |
R3 | 167  79   1379 |
   +----------------+
   |

If r1c2=7, then r1c13<>7,8
If r1c2=8, then r1c13<>7,8
So 7,8 can be removed from r1c13
```

Pair Middle Claimimg
```
     C1   C2   C3
   +----------------+-
R1 | 135  79   48   |
R2 | 135  29   6    |
R3 | 135  279  48   |
   +----------------+
   |

If r1c2 = 7, then r1c3<>7,8
If r1c2 = 9, then r1c3<>8,9
So 8 can be removed from r1c3
```

Pair Triplet Claimimg
```
     C1   C2   C3
   +----------------+-
R1 | 127  127  127  |
R2 | 4    9    5    |
R3 | 5    3    8    |
   +----------------+
   |

If r1c2=1, then r1c13<>1,2 resulting r1c13=7
If r1c2=2, then r1c13<>1,2 resulting r1c13=7
So 1,2 can be removed from r1c2
```

<sup>1</sup> SudokuNCExplainer has generated puzzles ranging from ED=1.2/1.2/1.2 to ED=10.8/1.2/1.2.

.

