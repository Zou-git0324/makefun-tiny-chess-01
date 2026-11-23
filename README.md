# makefun-tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/zou-git0324/makefun-tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/zou-git0324/makefun-tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A tiny chess engine in 4 KB of Python: a 0x88 board, alpha-beta search with quiescence, a transposition table and killer moves, searched to a fixed node budget so every trial replays the same moves. It plays the make.fun house gauntlet through the trial env. `main.py` is the whole engine, packed with the kit's lzma compressor.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:8080 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=qxtjtv0g&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>

## Revision

Round 2 (2026-11-20): the round-1 entry scored 997 on the platform's practice
trial, below the 1,154 floor, so the engine was strengthened. Changes: LMR
(late-move reductions), futility pruning at the frontier, check extensions, a
fix for the black passed-pawn bonus (it was inverted), per-file pawn extremes
for a faster eval, a king endgame taper, and repetition-draw scoring against
the game history. The node budget stays at 50,000 a move and the search is
still deterministic. Move order changes search efficiency only, never
legality: perft(3) from the start position is still 8902, and the mate-in-1
test still finds h5f7. Practice Elo (kit trials 0-2, local): 1451 / 1279 /
1099, mean 1276.

Round 5 (2026-11-23): the engine was rewritten on a Zobrist/transposition-table
base with killer moves, a history heuristic, null-move pruning (reduction 3),
iterative deepening to a 100,000-node budget, root PVS, repetition-draw scoring
and draw-avoidance (contempt). Search fixes: lazy legality (no legality test
until after make, +34% speed), quiescence now returns the mate score when in
check (it used to stand-pat), and LMR is skipped while in check. Practice Elo
(kit trials 0-2, local): 1545 / 1654 / 1545, mean 1581. perft(3) still 8902,
mate-in-1 still h5f7.
