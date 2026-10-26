# Stackly Finance

A 13-page finance website built with vanilla HTML, CSS and JavaScript. No frameworks, no build step.

## Folder structure (flat)

```
stackly-finance/
├── index.html              Home
├── about.html              About Us
├── services.html           Services overview
├── personal-loans.html     Personal Loans
├── home-auto-loans.html    Home & Auto Loans
├── insurance.html          Insurance
├── investments.html        Investments & Mutual Funds
├── calculator.html         Loan / EMI Calculator
├── pricing.html            Pricing / Plans
├── blog.html               Blog / Insights
├── faq.html                FAQ (accordion)
├── contact.html            Contact (validated form)
├── login.html              Log in / Sign up (User or Admin)
├── user-dashboard.html     User dashboard
├── admin-dashboard.html    Admin dashboard
├── 404.html                Target for social icons and placeholder footer links
├── style.css               Shared styles (luxury theme at the bottom)
├── script.js               Shared script (navbar, footer, calculator, forms, auth)
├── logo-light.webp         Stackly logo for dark backgrounds (header, footer)
├── logo-color.webp         Stackly logo in original colours for light backgrounds
├── favicon.png             Browser tab icon
└── *.webp                  All images, each under 100 KB
```

## How it works

- `script.js` injects the navbar and footer on every page. Each page sets `<body data-page="...">` to highlight its nav link. To change the menu or footer, edit the `NAV`, `PRODUCTS` and footer markup at the top of `script.js`.
- **Logo:** the navbar and footer load `logo-light.webp` (white wordmark, for the dark header and footer). `logo-color.webp` keeps the original navy and mint for light backgrounds. Both were cut out of the supplied logo, which was a low-resolution JPEG, so send an SVG or a high-resolution PNG for a sharper result.
- **Footer:** the eight navbar links sit in one row; social icons and all other footer links point to `404.html`.
- **Login / Sign up** is a front-end demo with two account types, User and Admin. After login, a User goes to `user-dashboard.html` and an Admin goes to `admin-dashboard.html`. Each dashboard redirects away if you are not logged in or have the wrong role. Accounts are stored in this browser only (`localStorage`, passwords hashed with SHA-256); a real site needs a server. Demo logins (password `Stackly@2026!`): `user@stackly.demo` and `admin@stackly.demo`. Creating an Admin account needs the access code `STACKLY-ADMIN-2026`, which is visible in `script.js`, so this is not real security.
- **Password policy:** at least 10 characters with upper case, lower case, number and symbol; no spaces, no three repeated characters, no common words, and no part of your name or email. A live strength meter and checklist guide the user.
- The contact form validates every field inline but does not send email. To receive messages, point the form at a service such as Formspree or your own API.
- Replace placeholder content before launch: contact details, statistics, testimonials, team names, rates and fees.

## Run locally

Open `index.html` in a browser, or serve the folder: `python3 -m http.server 8000` and visit http://localhost:8000.

## Deploy to GitHub Pages

1. Create a new repository on GitHub (for example `stackly-finance`).
2. Put all files at the **root** of the repository (keep the flat structure, no subfolder):
   ```
   git init
   git add .
   git commit -m "Stackly Finance website"
   git branch -M main
   git remote add origin https://github.com/<your-username>/stackly-finance.git
   git push -u origin main
   ```
3. In the repository go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose branch `main` and folder `/ (root)`, then **Save**.
5. Wait a minute or two. The site appears at `https://<your-username>.github.io/stackly-finance/`.

All links are relative, so the site works under the repository sub-path.

## Responsive check

Verified with Playwright (Chromium) at 375px, 768px and 1440px: all pages load with no horizontal scroll and no JavaScript errors, the hamburger menu opens at 375px, and the active nav link is highlighted on every page.
