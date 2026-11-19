# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/yylt00-dev/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/yylt00-dev/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in a single 4 KB Python file: negamax with alpha-beta pruning, quiescence search, a transposition table, null-move pruning and late-move reductions, on a fixed node budget so every move is deterministic. The engine source is LZMA-compressed inside main.py and unpacks itself at startup (standard library only). It plays games through the make.fun environment API.

## Round 2

The round-1 entry graded 1,099 on the practice instance, below the 1,154 floor. The fix was the transposition table: round 1 keyed entries by exact depth, so a stored result was reused only at the one depth it was computed at. Entries now store (depth, value, move, flag) and are reused whenever the stored depth covers the current node, with mate scores re-based to the probing ply. On the kit's local practice trials the strengthened engine scored 1,364 and 1,451 (two different opening sets) against the round-1 engine's 1,099, and its slowest move dropped from 7.8s to 6.6s of the 10s limit. Two further ideas were tested and rejected on the same trials: quiescence delta pruning (1,191) and a larger node budget of 44,000 (1,279, and slower worst-case moves).

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=e7064d5m&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
