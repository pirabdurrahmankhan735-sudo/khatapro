# KhataPro – Project Progress

Last updated: 2026-11-15 · Phase 1 · Database version 1 · App version 0.1.0

## BUILD STATUS: NOT BUILT, NOT COMPILED, NOT RUN
The authoring environment had no Android SDK, Gradle, Kotlin compiler, emulator or internet.
All code is hand-written and only statically checked (XML validity, string resources, bracket balance).
Expect to fix a few compile errors on the first Sync/Build. Send them to Claude and they will be fixed.

## Existing project inspection
No earlier KhataPro project or ZIP was supplied, so Phase 1 was created from scratch.

## Phase 1 completed (written, unverified)
- Gradle Kotlin DSL project, Compose, Material 3, MVVM, Room, Coroutines/Flow, DataStore, Navigation
- Manual dependency container (Hilt deliberately not used yet)
- Room DB v1: `customers`, `transactions` (unique mobile, FK RESTRICT, unique request id, indexes)
- Customers: add, edit, list, search (name/mobile), details, delete-with-rules
  (unpaid balance blocks deletion; customers with history are archived; empty ones are removed)
- Transactions: credit given, payment received, date, description, history, running balance,
  edit date/description, void with confirmation
- Dashboard: customer count, total receivable, customers with dues, recent transactions, quick actions
  (all values from the database)
- Reports (basic): receivable, this-month and all-time credit/payments, largest dues
- Settings: Urdu/English switch, Light/Dark/System theme, currency label (PKR default), version info
- Design system: navy/emerald/gold theme, reusable components, Urdu RTL and English LTR
- Unit tests (JVM) and instrumented repository tests (see TESTING_REPORT.md)
- GitHub Actions workflow (`.github/workflows/build.yml`, written but never run), PRIVACY_POLICY.md draft, CHANGELOG.md, docs/GITHUB_SETUP.md

## Decisions and deviations (please read)
- "Application settings" are stored in DataStore, not a Room table. This is the recommended place for
  preferences and avoids two copies of the same data. A DB settings table can be added later if needed.
- Payables are not supported (no supplier/purchase transaction type yet), so the dashboard shows receivables only.
- Overpayment is rejected to guarantee no negative balances. Advance payments need a future design (Phase 2+).
- Currency is a display label only; amounts are never converted.
- Urdu uses the device's default Urdu font. A bundled Nastaliq font (Noto Nastaliq Urdu) was not added
  because fonts could not be downloaded here; planned for the UI polish phase.
- `gradle-wrapper.jar` and `gradlew` scripts are missing (could not be generated offline).
  Android Studio does not need them. See BUILD_INSTRUCTIONS.md.

## Not done (later phases)
Products/inventory, sales/POS, invoices/PDF, purchases/suppliers, expenses, employees, accounting,
charts, backup/restore, export, app lock/PIN, release signing in CI, final privacy policy, Play Store listing,
launcher icon artwork for Play Store (512px), bundled Urdu font.

## Continuing to Phase 2
1. Build and run Phase 1 in Android Studio; fix and report any errors.
2. Upload `KhataPro_Phase1_Updated.zip` (or the latest ZIP if you changed anything) with the Phase 2 prompt.
3. Claude continues from that ZIP and adds a new Room migration (v1 to v2) for new tables.
