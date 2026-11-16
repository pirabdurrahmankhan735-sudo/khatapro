# KhataPro – Smart Business Ledger

Offline Android app (Kotlin, Jetpack Compose, Material 3, MVVM, Room, DataStore) for shopkeepers.
Package: `com.khatapro.ledger` · Default currency PKR · Urdu (RTL) primary, English secondary.

**Current phase: 1 (foundation).** See `PROJECT_PROGRESS.md` for what is done and what is not,
and `BUILD_INSTRUCTIONS.md` to build it.

## Structure
```
app/src/main/java/com/khatapro/ledger/
  data/db/           Room entities, DAOs, database
  data/repository/   LedgerRepository (all money rules), SettingsRepository (DataStore)
  domain/            Money, Validation, LedgerCalculator, AppError/Outcome
  util/              DateUtils (Asia/Karachi, DD-MM-YYYY)
  ui/theme/          Navy / Emerald / Gold theme
  ui/components/     Reusable components
  ui/navigation/     Bottom bar + NavHost
  ui/dashboard|customers|transactions|reports|settings/
```

## Money rules (do not break in later phases)
- Money is `Long` paisa. Never Float/Double.
- Balances are never stored; always computed from non-voided transactions.
- Transactions are never deleted, only voided. Amount cannot be edited (void and re-enter).
- A payment larger than the customer's balance is rejected, so balances never go negative.
- Each save carries a unique request id, so a double tap cannot create a duplicate.
- Database changes need an explicit Room `Migration`. Never use destructive migration.
