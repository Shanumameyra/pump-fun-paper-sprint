# Pump.fun Paper Sprint: Any Bot Can Win

[![make.fun](https://make.fun/badge/u-boothlord-pump-fun-paper-sprint-any-bot-can-f83c389b.svg)](https://make.fun/bounty/u-boothlord-pump-fun-paper-sprint-any-bot-can-f83c389b)
[![rank](https://make.fun/badge/u-boothlord-pump-fun-paper-sprint-any-bot-can-f83c389b/Shanumameyra/pump-fun-paper-sprint/rank.svg)](https://make.fun/bounty/u-boothlord-pump-fun-paper-sprint-any-bot-can-f83c389b)
[![reward](https://make.fun/badge/u-boothlord-pump-fun-paper-sprint-any-bot-can-f83c389b/Shanumameyra/pump-fun-paper-sprint/reward.svg)](https://make.fun/bounty/u-boothlord-pump-fun-paper-sprint-any-bot-can-f83c389b)

**Sprint Momentum** — a paper-trading bot for the pump.fun bonding-curve
replay (`agent-fun/replay/v2`). The grader runs `node /bot/main.ts` on
Node 22; the bot talks to the harness over stdin/stdout through the
vendored SDK shim (`vendor/makefun-bot.ts`, a byte-identical copy of the
kit's `sdk/ts/makefun-bot.ts`).

Strategy: buy a curve only once it has proved itself — old enough to have
survived the launch dump, price rising on real buy pressure from several
distinct wallets, sitting near its recent high. First buy is 0.05 SOL;
the bot pyramids only while the price keeps rising above the last buy, up
to 1 SOL per coin and 6 SOL total exposure. Every position carries a
20% stop-loss, a 30% trailing stop once up 5%, a fade exit when sellers
take over, and a 1500-slot time limit, so position slots free up for the
next coin. A tiny 0.02 SOL pacing probe keeps the run on pace for the
20-coin minimum bar when momentum alone is quiet. Fully deterministic:
no clock, no randomness, only replay-stream inputs.
