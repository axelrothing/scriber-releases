# Data and services

Scriber stores vocabulary, review history, and preferences in local SQLite. User API keys and cloud refresh credentials are encrypted for the current Windows user. Clipboard text and writing activity are not part of cloud vocabulary sync.

Writing assistance sends your selected text and request to OpenAI using your API key. Review OpenAI's API data controls and usage pricing before sending sensitive text. Scriber does not include shared API credentials, and your OpenAI usage costs belong to your account.

Optional sync uses Firebase Authentication for email/password sign-in and a production Convex deployment for your account's vocabulary, review events, shared preferences, and recovery history. Libraries are account-scoped. Recovery history is retained for approximately 30 days; operational receipts and deletion records can remain longer to support retries and stale-device safety. Device-local credentials, startup preferences, service configuration, and excluded applications do not synchronize.

Update discovery and downloads contact GitHub anonymously for Stable. GitHub receives ordinary network metadata such as your IP address. Internal Dev access uses separately stored private credentials and a private feed.

Local diagnostics record operational outcomes and timings. Disable diagnostics in settings if desired. Inspect reports before attaching them to a public issue. Never submit API keys, access tokens, clipboard contents, vocabulary databases, or encrypted credential files publicly.
