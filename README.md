# CogniWatch — Landing Site

Static marketing and support website for the [CogniWatch](https://cogniwatch.sandybrook.io) iOS/watchOS voice AI assistant.

## Pages

- **[Home](https://cogniwatch.sandybrook.io/)** — App features, screenshots, App Store download link
- **[Privacy Policy](https://cogniwatch.sandybrook.io/privacy.html)** — How we handle user data (CCPA/CPRA compliant)
- **[Support](https://cogniwatch.sandybrook.io/support.html)** — Contact form and frequently asked questions

## Tech Stack

- Plain HTML, CSS, and JavaScript — no framework, no build step
- Hosted on GitHub Pages with custom domain (`cogniwatch.sandybrook.io`)
- Responsive design with dark/light mode support
- Google Fonts (Inter)

## Development

Edit HTML files directly. No dependencies to install.

To preview locally:

```bash
python3 -m http.server 8080
```

Then open [http://localhost:8080](http://localhost:8080).

## Deployment

Push to `main`. GitHub Pages deploys automatically. Changes are live at [cogniwatch.sandybrook.io](https://cogniwatch.sandybrook.io) within minutes.

## Related Repos

| Repo | Description |
|------|-------------|
| [gnosisai-iosapp](https://github.com/cloudreyes/gnosisai-iosapp) | iOS/watchOS app (Swift, SwiftUI, Firebase) |
| [gnosisai-backend](https://github.com/cloudreyes/gnosisai-backend) | GCP + Firebase backend infrastructure (Terraform) |

## License

Copyright 2026 Sandy Brook DevWorks LLC. All rights reserved.
