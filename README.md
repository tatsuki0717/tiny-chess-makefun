# tiny-chess-01 entry

Original compact chess engine in a single `main.py` (4,066 bytes), built for
the make.fun bounty "Build the strongest chess engine in 4 KB of Python".
MIT licensed (see LICENSE).

Design: 0x88 board; negamax alpha-beta with iterative deepening on a fixed
node budget (70,000 nodes/move — deterministic, no clock, fixed-seed
Zobrist); quiescence over captures, promotions and check evasions;
transposition table with exact/lower/upper bound flags; TT-move and
MVV-LVA move ordering; check extensions; material + piece-square-table
evaluation with a midgame/endgame king blend; repetition and the 50-move
rule score 0 inside search. Python 3.13 standard library only; the engine
talks to the environment at `MAKEFUN_ENV_URL` and accesses nothing else.

`main.py` is produced from the readable source `engine_src.py` (kept beside
the repo, uncommitted) with the make.fun kit, as a separate step after the
source's last change:

    node cli/makefun.mjs compress engine_src.py --out main.py

Local practice results (kit trial-0 / trial-1, 6 games each vs the house
gauntlet): Elo 1364 (3W 1D 2L) and Elo 1654 (5W 0D 1L) for this build.
