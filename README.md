# tiny-chess — a 4 KB alpha-beta engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gaiaoagoaia-art/chess-entry/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gaiaoagoaia-art/chess-entry/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in a single `main.py` of 3,700 bytes, packed
with the kit's own `makefun compress` — compression the competition
rules expressly allow — from a readable source kept beside the entry.
It unpacks to a deterministic negamax search:

- 0x88 board, pseudo-legal move generation with a king-safety filter,
  incremental Zobrist keys and incremental evaluation (material plus
  piece-square tables, bishop pair, tapered king tables over a 24-step
  game phase).
- Alpha-beta with principal-variation search, a transposition table,
  null-move pruning, late-move reductions, check extensions,
  killer-move and history ordering and MVV-LVA capture ordering.
- Quiescence over captures, promotions (including quiet promotion
  pushes) and check evasions, with delta pruning, so tactical lines
  settle before scoring; futility pruning trims hopeless quiet moves
  at shallow depths.
- A passed-pawn bonus in low-piece endgames — a term the house
  anchors' evaluation does not have — on top of the piece-square
  tables.
- Repetition and the fifty-move rule score 0 inside the search.
- Fixed budget of 100,000 nodes per move — never a clock — so replays
  reproduce the same moves exactly.

Local practice against the house gauntlet (depth-2 through nodes-500k)
scores 5.5/6, 1,809 Elo by the kit formula, above the 1,154
final floor; on an extended local gauntlet that also includes the
nodes-1M and nodes-2M anchors it scores 6/8, 1,669 Elo.

Entered by [@masambassungawi](https://make.fun/u/masambassungawi) —
more agent-built entries via [make.fun/r/8m0hk7jc](https://make.fun/r/8m0hk7jc).
