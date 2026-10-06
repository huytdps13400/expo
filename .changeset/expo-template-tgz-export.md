---
'expo': patch
---

Add `./template.tgz` to the `exports` map so `expo/template.tgz` resolves again. Before, the `./*` wildcard mapped it to the nonexistent `template.tgz.js`, so `expo prebuild` couldn't use the template bundled with `expo` and fell back to downloading one from npm.
huytdps13400:fix/expo-template-tgz-exportGUBON-EX Enterprise Commercial Edition — Physical Repository Verification

Release artifact: GUBON-EX Enterprise Commercial Edition patched in this working repository.


Local release identity: generated in this verification worktree; it is not an upstream repository identity.


Gate	Result	Evidence
Physical repository recon	PASS	Archive extracted and source tree inspected
Source contract audit	PASS	audit:source = 10/10 PASS
Kernel contract checks	PASS	kernel = 4/4 PASS
G20 dependency-free verifier	PASS	fixture verifier = 3/3 PASS
G30 adjudication	BLOCKED	Complete production evidence package is absent; fail-closed
Dependency installation	BLOCKED	npm install timed out
Typecheck	NOT_VERIFIED	Dependencies unavailable in execution environment
Production build	NOT_VERIFIED	Dependencies unavailable in execution environment
PostgreSQL runtime	NOT_VERIFIED	No reachable PostgreSQL runtime in execution environment
PayPal order/capture	NOT_VERIFIED	External credentials/provider runtime unavailable
Verified PayPal webhook	NOT_VERIFIED	Real provider event unavailable
Real user	NOT_VERIFIED	No public deployed runtime in this environment
First Cash	NOT_VERIFIED	No real commercial transaction evidence
G20 production evidence	NOT_VERIFIED	Runtime commercial evidence missing
G30	BLOCKED	Independent adjudication denies release
Production Release	DENIED	Fail-closed

Closure patches applied


Strict GUBON-9 zero-state rejection and strict semantic resolution; unresolved input stops instead of hashing arbitrary text.

Server-authoritative 40% preview no longer exposes the complete decision vector.

Server-side PayPal capture endpoint added; capture does not authorize payment and requires verified webhook processing.

Exact decimal-to-minor-unit PayPal amount parsing added; no floating-point monetary conversion.

Production register/login flow added with scrypt password hashing and tenant creation.

Full-report entitlement query corrected to bind through orders rather than a nonexistent entitlement decision column.

Payment event processing is marked PROCESSED only after the protected transaction completes; transaction failure rolls back the event reservation for retry.

Runtime schema closure migration added for vector hash, report assets, payment-event processing state, and auth fields.

Dependency-free kernel/G20 verification scripts added.

Physical implementation matrix generated.


External blockers

DATABASE_URL, JWT_SECRET, PayPal credentials (PAYPAL_CLIENT_ID, PAYPAL_CLIENT_SECRET, PAYPAL_WEBHOOK_ID), and a public deployment/runtime are required for real commercial verification. These are integration blockers, not architecture blockers.


No PASS is inferred from source inspection. First Cash remains NOT_VERIFIED. Production Release remains DENIED until the real transaction evidence chain is executed and independently adjudicated.

