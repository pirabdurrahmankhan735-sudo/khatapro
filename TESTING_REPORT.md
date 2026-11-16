# Testing Report – Phase 1

## What was actually run
Nothing was compiled or executed. No Android SDK, Gradle, Kotlin compiler, emulator or internet was available.

## Static checks performed
- All XML files parse as valid XML.
- Every `R.string.*` used in code exists in both English and Urdu strings (94 each).
- Brackets balance in every Kotlin file.

## Tests written (NOT yet run)
JVM unit tests (`app/src/test`): MoneyTest (parsing, Urdu digits, formatting, no float drift),
ValidationTest (mobile formats, names), LedgerCalculatorTest (running balance, voided rows), DateUtilsTest.

Instrumented tests (`app/src/androidTest`, in-memory Room): duplicate mobile rejected, balance =
credits minus payments, overpayment rejected, duplicate request id ignored, invalid amount/date rejected,
void keeps history, cannot void credit if balance would go negative, delete/archive rules.

## Not tested
Navigation, Urdu/English layouts, language switching, dark theme, dashboard and report values on screen,
database upgrade (only version 1 exists). These need a real run on a device.
