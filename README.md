# XO Milestone Escrow — final submission

This folder contains only the files intended for the final bounty submission.

## Submission files

| File | Purpose |
| --- | --- |
| `xo-template.json` | The final XO template. |
| `xo-invitation.json` | The open mint invitation to import in Blaze. |
| `xo-invitation-summary.json` | Values and IDs used while testing. |
| `TEST_STEPS.md` | Step-by-step reproduction instructions. |
| `YOUR_FEEDBACK.md` | Personal 500-word feedback. You must write this yourself. |
| `evidence/` | Raw executed invitations from Blaze. |

## Important IDs

Template ID:

```text
5e40d3c5662384b3d381b6b0eecf1d39b05abdd1cd3eb4b9109403867a48f292
```

Open invitation ID:

```text
d2c788026af3dce4ac8c27100590c355
```

Invitation expiry:

```text
2026-12-06T04:00:27.366Z
```

This is intentionally longer than the one-week judging period.

Network:

```text
Chipnet only
```

Demo amount:

```text
1,000,000 sats = 0.01 BCH
```

## Reproduce

1. Open `https://blaze.xo.cash/`.
2. Select **Chipnet**.
3. Import `xo-invitation.json`.
4. Accept as the client role.
5. Fund the wallet with about `0.011 BCH` of Chipnet test coins.
6. Follow `TEST_STEPS.md`.

The funding UTXO used for mint must be output index `0`.

## Evidence status

The `evidence/` folder contains raw executed invitations for:

```text
mint
lock
submit
partialRelease
release
```
