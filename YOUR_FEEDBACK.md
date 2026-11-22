The overall experience was good, although there were few hurdles which made the development journey little difficult.

I have sent the following 4 suggestions in the General Protocols group:
1. VM version mismatch: Engine unlock verification uses the BCH2023_05 VM (520-byte stack limit) despite the template declaring BCH2026_05 support. - Nov 20, 12:20 PM
2. Blaze token genesis UX: UTXO picker allows selecting non-:0 outputs for genesis actions and throws a generic token mismatch error instead of filtering to :0 or showing a pre-flight warning. - Nov 20, 1:05 PM
3. omitChangeAmounts ignored: Engine still adds automatic satoshi change even when "omitChangeAmounts": { "satoshis": true } is set. - Nov 20, 3:00 PM
4. Multi-role testing DX: EntityMultipleRolesWithFollowUpUnsupportedError blocks solo devs from testing multi-party follow-up actions from a single wallet/account. - Nov 20, 12:22 PM

The feature which i like was Actionable Transaction Diagnostics: Blaze’s real-time validation warnings, script step debugging, and sequence/timelock breakdowns make it straightforward to inspect transaction structure and catch invalid inputs or missing signatures before broadcasting on Chipnet. 

