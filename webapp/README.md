# Bet5K Web App

`index.html` is a static Telegram Web App wrapper. It does not imitate or
replace PARI: after the permission prompt it opens the original affiliate URL
from `PARI_AFFILIATE_URL` (with the user's Telegram ID in `sub_1`). The wrapper
shows four onboarding steps, reads the Telegram name/avatar, validates Client ID
and sends a confirmed ID back to the bot with `Telegram.WebApp.sendData`.
Publish the `webapp/` directory at a public HTTPS URL and set that full URL in `.env`:

```env
WEB_APP_URL=https://your-domain.example/bet5k/index.html
```

The bot adds `flow`, URL-encoded `target`, and the next PARI destinations
automatically. The page requests Telegram write access on the first PARI launch,
then opens the destination. When a user confirms Client ID, the bot stores a
normal pending registration and notifies the administrator with a Web App source
marker. Match links use the same wrapper; in channels Telegram receives a normal
URL button because native `web_app` buttons are supported only in private chats.

