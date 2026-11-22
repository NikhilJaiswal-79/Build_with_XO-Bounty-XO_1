# Blaze reproduction steps

Use **Chipnet only**.

## 0. Files

Use these files:

```text
xo-template.json
xo-invitation.json
xo-invitation-summary.json
evidence/
```

---

## 1. Setup

1. Open `https://blaze.xo.cash/`.
2. Select **Chipnet**.
3. Get `0.01–0.02` Chipnet BCH from:
   - `https://tbch.googol.cash/` → choose **Chipnet**
   - or `https://chipnet.bch.ninja/`
4. Import `xo-invitation.json`.
5. Accept as **client**.
6. Copy the receive address shown by Blaze.
7. Send fake Chipnet BCH to that address.
8. Wait for the coins to appear in Blaze.
9. Use a funding coin with outpoint index `0`.
10. If the coin is index `1`, use another coin or get fresh coins.

---

## 2. Mint

1. Open `mintingOutput`.
2. Set `tokenCategory` to the txid of the funding coin at output index `0`.
3. Let Blaze add change.
4. Click **Execute** / **Broadcast**.
5. Click **Copy Invitation** / **Save Invitation**.
6. Save as:

```text
evidence/mint-executed.json
```

7. Record the transaction ID.

---

## 3. Lock

1. Open the **minting NFT** coin.
2. Choose **lock**.
3. Fill:
   - `lockedSatoshis` = `1000000`
   - `refundDeadline` = value from `xo-invitation-summary.json`
   - `milestoneHash` = value from `xo-invitation-summary.json`
   - `tokenCategory` = same txid used in mint
4. Add the mint change coin as funding.
5. Let Blaze add change.
6. Click **Execute** / **Broadcast**.
7. Click **Copy Invitation** / **Save Invitation**.
8. Save as:

```text
evidence/lock-executed.json
```

9. Record the transaction ID.

---

## 4. Submit

1. Open the locked money output.
2. It must show state `0000`.
3. Choose **submit**.
4. Add the **developer badge** coin as the second input.
5. Click **Execute** / **Broadcast**.
6. Click **Copy Invitation** / **Save Invitation**.
7. Save as:

```text
evidence/submit-executed.json
```

8. Record the transaction ID.

---

## 5. Partial release

1. Open the locked money output.
2. It must show state `0001`.
3. Choose **Partial Release to Developer**.
4. Fill:
   - `currentEscrowSatoshis` = `1000000`
   - `payoutNow` = `300000`
   - `remainingSatoshis` = `700000`
   - `currentStateCommitment` = `0001`
5. Add the **client badge** coin as the second input.
6. Let Blaze add change/fee input if asked.
7. Click **Execute** / **Broadcast**.
8. Click **Copy Invitation** / **Save Invitation**.
9. Save as:

```text
evidence/partial-release-executed.json
```

10. Record the transaction ID.

For another partial release:

```text
currentEscrowSatoshis = previous remainingSatoshis
payoutNow + remainingSatoshis = currentEscrowSatoshis
```

---

## 6. Release

1. Open the locked money output.
2. It must show state `0001`.
3. Choose **release**.
4. Add the **client badge** coin as the second input.
5. If releasing after the `300000` partial release, set:

```text
lockedSatoshis = 700000
```

6. Let Blaze add change/fee input if asked.
7. Click **Execute** / **Broadcast**.
8. Click **Copy Invitation** / **Save Invitation**.
9. Save as:

```text
evidence/release-executed.json
```

10. Record the transaction ID.

---

## 7. Refund

Use this after the refund deadline has passed.

1. Do a new `mint` and `lock`.
2. For a quick test, use a `refundDeadline` about 5 minutes in the future.
3. Wait until the deadline passes.
4. Open the locked money output.
5. Choose **refund**.
6. Add the **client badge** coin as the second input.
7. Click **Execute** / **Broadcast**.
8. Click **Copy Invitation** / **Save Invitation**.
9. Save as:

```text
evidence/refund-executed.json
```

---

## 8. Arbiter pays developer

1. Open a locked money output showing state `0001`.
2. Choose **resolveToDeveloper**.
3. Add the **arbiter badge** coin as the second input.
4. Click **Execute** / **Broadcast**.
5. Click **Copy Invitation** / **Save Invitation**.
6. Save as:

```text
evidence/resolve-executed.json
```

---

## 9. Arbiter refund

Use this after the refund deadline has passed.

1. Open the locked money output.
2. Choose **arbiterRefund**.
3. Add the **arbiter badge** coin as the second input.
4. Click **Execute** / **Broadcast**.
5. Click **Copy Invitation** / **Save Invitation**.
6. Save as:

```text
evidence/arbiter-refund-executed.json
```

---

## 10. Badge transfer

For each badge:

### Client badge

1. Open the **client badge** coin.
2. Choose **transferClientBadge**.
3. Set:
   - `badgeCommitment` = `01`
   - `recipientLockingScript` = any valid locking script hex
4. Click **Execute** / **Broadcast**.
5. Save the raw invitation as:

```text
evidence/transfer-client-executed.json
```

### Developer badge

1. Open the **developer badge** coin.
2. Choose **transferDeveloperBadge**.
3. Set:
   - `badgeCommitment` = `02`
   - `recipientLockingScript` = any valid locking script hex
4. Click **Execute** / **Broadcast**.
5. Save the raw invitation as:

```text
evidence/transfer-developer-executed.json
```

### Arbiter badge

1. Open the **arbiter badge** coin.
2. Choose **transferArbiterBadge**.
3. Set:
   - `badgeCommitment` = `03`
   - `recipientLockingScript` = any valid locking script hex
4. Click **Execute** / **Broadcast**.
5. Save the raw invitation as:

```text
evidence/transfer-arbiter-executed.json
```

---

## 11. Debug check

After each executed action:

1. Copy the raw executed invitation from **Copy Invitation** / **Raw Extended JSON**.
2. Paste it into Blaze **Inspector** / **Debug**.
3. Take a screenshot.
4. Save the screenshot in `evidence/`.

Use these names:

```text
evidence/mint-debug.png
evidence/lock-debug.png
evidence/submit-debug.png
evidence/partial-release-debug.png
evidence/release-debug.png
```

Do not paste the human-readable preview.

---

## 12. Button name differences

Use these equivalents:

```text
Import Invitation = Paste Invitation
Execute = Broadcast = Run
Save Invitation = Copy Invitation = Export
Inspect = Debug = Details
```
