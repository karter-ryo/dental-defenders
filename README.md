# Dental Defenders

A single-file, retro arcade shooter for Smile Serenity Dental Care.

Brush back waves of sugar, plaque, and cavities. Survive long enough to submit
your score and join the Smile Serenity mailing list for dental tips and
exclusive offers.

## Run it

Open `index.html` in any modern browser — desktop or mobile. No build step, no
dependencies, no server required. The logo is inlined as base64, so the file
is fully self-contained.

## Controls

- **Move**: `←` / `→` or `A` / `D`
- **Fire**: `Space` or `↑`
- **Pause**: `P`
- **Restart**: `R`
- **Mute**: `M`

On touch devices: drag anywhere on the field to move, tap the on-screen FIRE
button to shoot.

## Score submission

When the player runs out of lives, the Game Over screen invites them to save
their score, which subscribes them to the Smile Serenity Mailchimp audience
(double opt-in handled by Mailchimp).

Submission mode is controlled by `FORM_CONFIG` near the top of the script tag
in `index.html`:

| `mode`        | What happens                                                                 |
| ------------- | ---------------------------------------------------------------------------- |
| `'mailchimp'` | Native form POST to the configured Mailchimp embedded form (currently live). |
| `'webhook'`   | JSON POST to `webhookUrl` (Wix Velo, Zapier, Formspree, etc.).               |
| `'local'`     | Stores scores in `localStorage` only — useful while testing.                 |

## Deploy on Wix

1. In the Wix Editor, add an **HTML iframe / Embed Code** element where you
   want the game to live.
2. Paste the entire contents of `index.html` into the "HTML Code" option.
3. Save & publish.

To pipe submissions through a Wix Velo HTTP function instead of Mailchimp,
switch `FORM_CONFIG.mode` to `'webhook'` and set `webhookUrl` to the function
URL.
