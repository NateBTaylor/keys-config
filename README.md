# keys-config

Remote configuration for the **Keys** iOS app. Edit these files on GitHub and
the app picks up the change on the next launch — no App Store release needed.

## `home_banner.json`

Drives the dynamic banner at the top of the Home screen. Change `id` whenever
you want a dismissed banner to reappear for everyone. Set `active: false` to
hide it entirely.

**Types** (`type` field):

- `announcement` — title + message, optional link button (`actionLabel` + `actionURL`). No input.
- `feedback` / `input` — free-text response box.
- `choice` — multiple choice (`choices`); `allowMultiple` for multi-select, `allowOther` for an "Other…" box.

Responses are sent to PostHog as the `home_banner_responded` event.

### Examples

Free-response feedback:
```json
{
  "id": "2026-06-feedback", "active": true, "emoji": "💬",
  "title": "We'd love your input",
  "message": "Tell us what you want next in Keys.",
  "type": "feedback",
  "prompt": "Got a request? Tell us what you'd love to see.",
  "placeholder": "Type your idea…",
  "submitLabel": "Send"
}
```

Multiple choice:
```json
{
  "id": "2026-07-poll", "emoji": "🎹",
  "title": "What should we build next?",
  "type": "choice",
  "prompt": "Pick what matters most to you.",
  "choices": ["More songs", "Better practice tools", "Sheet music export"],
  "allowMultiple": false,
  "allowOther": true
}
```

Plain announcement with a link:
```json
{
  "id": "2026-08-update", "emoji": "🎉",
  "title": "Sheet music export is here",
  "message": "Export any song to PDF from the player.",
  "type": "announcement",
  "actionLabel": "See what's new",
  "actionURL": "https://bestdaylabs.com"
}
```
