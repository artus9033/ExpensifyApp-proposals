# Notes for /verify

## The app
- Standalone New Expensify for Android (`adhoc` flavor, package `com.expensify.chat.adhoc`, no
  Expensify Classic), talking to Expensify's staging servers, so it needs network. The first launch
  can sit on the splash screen for a few seconds; wait for the app instead of relaunching it.
- It opens signed out, on the sign-in screen. Without an account, only that screen is reachable:
  scrolling down it shows a footer of links and a language picker (English / Español), which switches
  the app's language at once, without signing in.
- The app always uses its narrow (phone) layout on Android, whatever the screen size. Copy that only
  appears on wide layouts is not shown here.
- Labelled text inputs expose their label on more than one element, so a `label=` selector for a
  field can match twice. Target the field by the `id` a snapshot shows for it.

## Limits
- Do not sign in or create an account. Never submit a real-looking email address or phone number in
  "Phone or email": on staging, Continue then sends a real sign-in code. Submitting a value that is
  clearly neither (e.g. `not-an-email`) is safe: the app rejects it on the device without contacting
  the server. Do not press the Apple or Google buttons. If a claim needs a signed-in account, report
  it as not reachable.
- Footer links open a browser. Do not follow them; if one opens, use system back to return.
- Dismiss Android system prompts (notification permission, "app isn't optimized") and carry on.
