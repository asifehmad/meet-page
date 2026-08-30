# meet.asifahmad.net

Source for **[meet.asifahmad.net](https://meet.asifahmad.net)**, a small public availability
page used to arrange research meetings and conversations.

It shows a read-only embedded Google Calendar and is hosted on **GitHub Pages** with a
custom subdomain.

---

## Features

- Embedded public Google Calendar, updated automatically
- Times rendered in **the visitor's own timezone**, detected at page load
- Light / dark theme with system-preference support, applied before first paint
- Locally generated QR code (`qr.svg`) — no third-party QR service at runtime
- Print stylesheet, so printing the page produces a tidy office-door notice
- Fully static: no backend, no build step, no tracking

---

## Status

From **21 September 2026** I am based at the **University of Leicester, United Kingdom**,
as a PhD researcher in Computer Science. Office and campus details will be added to the page
once confirmed; until then all meetings are held online.

---

## Structure

Everything lives in a single self-contained `index.html` — markup, styles, and script — plus
the generated QR code. Design tokens deliberately mirror
[asifahmad.net](https://asifahmad.net) so the two pages read as one site.

| File | Purpose |
| --- | --- |
| `index.html` | The entire page |
| `qr.svg` | QR code pointing at `https://meet.asifahmad.net` |
| `CNAME` | Custom domain for GitHub Pages |

---

## Regenerating the QR code

`qr.svg` only needs regenerating if the URL changes:

```bash
python3 -m pip install qrcode
python3 - <<'PY'
import qrcode
qr = qrcode.QRCode(error_correction=qrcode.constants.ERROR_CORRECT_M, box_size=1, border=2)
qr.add_data("https://meet.asifahmad.net")
qr.make(fit=True)
qr.make_image().save("qr.png")
PY
```

---

## Privacy

Only a dedicated public calendar is embedded. No private events, authentication tokens, or
API keys are exposed.

---

## Related

- Personal webpage: <https://asifahmad.net>

---

## License

Provided for personal and academic use. Feel free to adapt the structure for your own
availability page.
