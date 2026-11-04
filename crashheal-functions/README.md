# Crashheal alert functions

Forwards new Crashlytics issues (fatal, non-fatal, ANR, regressions) to the Crashheal GitHub workflow in `OWNER/REPO`.
It's a separate Functions *codebase*, so deploying it never touches your other functions.

```bash
cd crashheal-functions
firebase functions:secrets:set CRASHHEAL_GITHUB_TOKEN   # fine-grained PAT: OWNER/REPO, Contents: read & write
firebase deploy --only functions:crashheal
```

Cloud Functions need the Blaze (pay-as-you-go) plan. These run only when Crashlytics raises an alert, so they normally stay inside the free tier.
Alerts fire for *new* issues; the daily sweep in the workflow covers the existing backlog.
