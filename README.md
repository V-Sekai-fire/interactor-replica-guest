# interactor-replica-guest

A shared object as four replicas of one deterministic guest: an input is applied when three of four reports agree, and a state is valid when the digests agree.

## What is here

- `replica.sgd`: the agreement on inputs and digests, and the transfer of state to a replica that differs.
- `tests/replica_gate.gd`: four replicas of a MuJoCo guest for a stated number of sends, with three planted faults.
- `docs/replica.md`: the rule, the calls and the controls.

    godot --headless --path . -s tests/replica_gate.gd -- <mujoco.double.elf> [--sends=N] [--control=altered|split|badstate]

## The other parts

Each part of the presence slice is a repository of its own in `V-Sekai-fire`, and they are checked
out side by side.

| Repository | What it holds |
| --- | --- |
| `interactor-packets-guest` | the Packet codec and the order of a body's 21 parts |
| `interactor-zone-router-guest` | the model of a zone that only routes, and the trace a relay replays |
| `interactor-observer-guest` | one client's check of what the zone relays: hashes, tags and verdicts |
| `interactor-curve-guest` | curve playback between sends |
| `interactor-replica-guest` | a shared object as four replicas |
| `interactor-anny-follow-guest` | the avatar posed from the muscle skeleton |
| `transport-zone-relay` | the relay in C, on sockets, with its load generator |
| `interactor-presence-gates` | the gates that join the parts on a real body, the videos and the ledger |

## Rules of the source

Guests are SafeGDScript and gates are GDScript run on a double-precision editor with the sandbox
built in. A gate prints a `RESULT:` line and has controls that must fail. Comments are at most 3%
of a file's lines, which `tools/comment_density.exs` of `interactor-presence-gates` checks, and
the explanation is in the documentation.

## Licence

MIT; see `LICENSE`.
