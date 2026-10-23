# Security — heroku-buildpack-submodule

> **Status: INCOMPLETE (stub, 2026-09-24).** Created so every repo has one. Fill in the TODOs; see the fable repo's `security.md` for a complete example.

## 1. Status
Deployed Firebase rules, from an org-wide audit on 2026-09-24 (project, release, classification):
- TODO: no Firebase project found; list every datastore and its access controls.

Rules files in this repo: none found.

TODO: table of local / staging / production × Firestore / Storage / other stores: deployed == repo? test mode? last verified.

## 2. Principle
Staging runs exactly the rules production will run. Rules change in the repo, deploy to staging first from CI, get tested there, then the same file is promoted to production. Never edit rules in the console; never use test mode.

## 3. Data inventory
TODO: each collection / bucket / table: contents, sensitivity (public / internal / personal / secret), encrypted?, written by client or server.

## 4. Auth and authorization
TODO: sign-in methods, how roles/admins are identified (and whether users can write that field), email-verification assumptions, service accounts.

## 5. Client access map
TODO: what client SDKs read/write directly; everything else goes through the server.

## 6. Rules
TODO: what the rules allow, how they are tested (emulator tests, test-mode lint).

## 7. Secrets and keys
TODO: where each secret lives (names only) and who can rotate it.

## 8. Automated checks
TODO: rules tests on PR, test-mode lint, deploy rules from CI, deployed-vs-repo drift check, dependency audit, secret scanning. Missing ones go in open risks.

## 9. Open risks
TODO: numbered, severity, one-line exploit, proposed fix.

## 10. How to verify
```bash
T=$(gcloud auth print-access-token)
curl -s -H "Authorization: Bearer $T" -H "x-goog-user-project: $P" "https://firebaserules.googleapis.com/v1/projects/$P/releases"
```
