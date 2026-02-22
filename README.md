# Gnosis AI — Landing Site

Static marketing and support website for the [Gnosis AI](https://gnosisai.app) iOS/watchOS voice AI assistant.

## Pages

- **[Home](https://gnosisai.app/)** — App features, screenshots, App Store download link
- **[Privacy Policy](https://gnosisai.app/privacy.html)** — How we handle user data (CCPA/CPRA compliant)
- **[Support](https://gnosisai.app/support.html)** — Contact form and frequently asked questions

## Tech Stack

- Plain HTML, CSS, and JavaScript — no framework, no build step
- Hosted on GitHub Pages with custom domain (`gnosisai.app`)
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

Push to `main`. GitHub Pages deploys automatically. Changes are live at [gnosisai.app](https://gnosisai.app) within minutes.

## Related Repos

| Repo | Description |
|------|-------------|
| [gnosisai-iosapp](https://github.com/cloudreyes/gnosisai-iosapp) | iOS/watchOS app (Swift, SwiftUI, Firebase) |
| [gnosisai-backend](https://github.com/cloudreyes/gnosisai-backend) | GCP + Firebase backend infrastructure (Terraform) |

## License

Copyright 2026 Sandy Brook DevWorks LLC. All rights reserved.
