# Leander Mathisen — Personal Resume Website

A modern, responsive portfolio website showcasing my experience, education, projects, and contact information. Hosted on AWS S3 + CloudFront with automated CI/CD.

## Tech Stack

- **HTML5** / **CSS3** — semantic markup, CSS Grid, Flexbox, custom properties
- **JavaScript** — IntersectionObserver for scroll animations, native smooth scrolling
- **Google Fonts** — [Inter](https://fonts.google.com/specimen/Inter)
- **Font Awesome 6** — icons

No frameworks or build tools required — pure static site.

## Running Locally

Open `index.html` directly in your browser:

```bash
open index.html
```

Or serve with a local HTTP server:

```bash
python3 -m http.server 8000
```

Then visit [http://localhost:8000](http://localhost:8000).

## Deployment

The site is hosted on **AWS S3** behind **CloudFront** and deployed automatically via **GitHub Actions** on every push to `master`.

The workflow (`.github/workflows/deploy.yml`) uses **OIDC** to authenticate with AWS — no long-lived access keys are stored. On each deploy it:
1. Syncs all site files to the S3 bucket
2. Invalidates the CloudFront cache so changes go live immediately

### Required GitHub Secrets

| Secret | Description |
|--------|-------------|
| `AWS_ROLE_ARN` | IAM role ARN with S3 and CloudFront permissions |
| `AWS_REGION` | AWS region (e.g. `us-east-1`) |
| `AWS_S3_BUCKET` | S3 bucket name |
| `CLOUDFRONT_DISTRIBUTION_ID` | CloudFront distribution ID |

## Project Structure

```
├── index.html                # Main HTML page
├── style.css                 # All styles (responsive, animations)
├── images/
│   ├── background.jpg        # Hero background (Seattle skyline)
│   ├── profilepicture.jpg    # Profile photo
│   ├── Logo.png              # Site logo / favicon
│   ├── microsoft-logo.png    # Microsoft company logo
│   ├── dgs-logo.png          # Digital Global Systems logo
│   └── uoft-logo.png         # University of Toronto crest
├── Leander_Mathisen_Resume.pdf
└── .github/
    └── workflows/
        └── deploy.yml        # CI/CD pipeline (S3 sync + CloudFront invalidation)
```

## License

This is a personal portfolio site. Feel free to use the structure as a template for your own.
