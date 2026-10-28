# New Expensify (Android, standalone NewDot)

- The build is the `adhoc` flavor of standalone New Expensify (no Expensify Classic / OldDot), package
  `com.expensify.chat.adhoc`, pointed at the staging environment from `.env.staging`.
- It launches on the sign-in screen. Most flows need a signed-in account; if the pull request's claim
  cannot be reached without one, report it as not reachable instead of creating an account.
- Main navigation: the bottom tab bar (Inbox, Reports, Workspaces, Account) and the green "+" button
  for creating expenses, chats and reports. Settings live under Account.
- Ignore the Android "app isn't optimized" or notification permission prompts; dismiss them.
