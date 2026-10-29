# Notes for /verify

## The app
- Standalone New Expensify for Android (`adhoc` flavor, package `com.expensify.chat.adhoc`, no
  Expensify Classic), talking to Expensify's staging servers, so it needs network. The first launch
  can sit on the splash screen for a few seconds; wait for the sign-in screen instead of relaunching.
- It opens signed out, on the sign-in screen. On a phone that screen shows, top to bottom: the
  Expensify logo, a header ("Travel and expense, at the speed of chat"), a one-line subtitle, a
  "Phone or email" field with a "Continue" button, and "Sign in with" Apple and Google buttons. There
  is no "Welcome!" header on a phone; it only appears on wide screens.
- Scrolling down the sign-in screen reaches a footer of links, and below them a language picker
  (English / Español). Changing it switches the app's language at once, without signing in.

## Driving it
- The "Phone or email" field: target it with `id="username"`. `label="Phone or email"` matches two
  elements and fails.
- Evidence: quote the exact text of one element as `snapshot -i` (or a plain `snapshot`) prints it.
  Quotes from `snapshot --raw` are not accepted. To show a text is gone, take a `snapshot -i` of the
  screen and quote the text that replaced it.
- Steps in a recording: `wait` needs a duration in ms, for example `wait 1500`.

## Limits
- Do not sign in or create an account. Never submit a real-looking email address or phone number in
  "Phone or email": on staging, Continue then sends a real sign-in code. Submitting a value that is
  clearly neither (e.g. `not-an-email`) is safe: the app rejects it on the device without contacting
  the server. Do not press the Apple or Google buttons. If a claim needs a signed-in account, report
  it as not reachable.
- Footer links open a browser. Do not follow them; if one opens, use system back to return.
- Dismiss Android system prompts (notification permission, "app isn't optimized") and carry on.
