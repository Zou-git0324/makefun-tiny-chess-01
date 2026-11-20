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

Root move ordering (2026-11-20): after each iterative-deepening pass, root
moves are now sorted by the score that pass gave them, best first, instead of
only moving the best move to the front. Move order changes search efficiency
only, never legality: perft(3) from the start position is still 8902, and the
mate-in-1 test still finds h5f7. Practice Elo (kit trials 0-2): 1545 / 1279 /
1099, mean 1308.
