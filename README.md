# 🎭 Playwright: Web Automation Testing From Zero to Hero

Playwright - test automation framework developed by Microsoft.  
Modern, highly customizable, and reliable.

Hands-on Playwright course repo – from setup to advanced test automation (POM, API, CI/CD, Docker)

This repository follows the course **Playwright: Web Automation Testing From Zero to Hero** by *Artem Bondar*.  
It includes progressive lessons, starting from scratch and moving toward advanced Playwright concepts.


## 📑 Table of Contents

- [🎭 Playwright: Web Automation Testing From Zero to Hero](#-playwright-web-automation-testing-from-zero-to-hero)
- [🚀 How to Get Started](#-how-to-get-started)
  - [1. Clone the repository](#1-clone-the-repository)
  - [2. Install Playwright browsers](#2-install-playwright-browsers)
- [📂 Repository Structure](#-struttura-della-repo)
- [📚 What I will practice](#-what-i-will-practice)
- [📦 Repo Layout](#-repo-layout)
- [⚡ CI/CD with GitHub Actions](#-cicd-with-github-actions)
- [📜 Example Test](#-esempio-test-testsexamplespects)
  - [Running Tests](#running-tests)
  - [Viewing Reports](#viewing-reports)
  - [Example Test](#example-test)
  - [Running a Single Test](#running-a-single-test)
  - [Notes](#notes)
- [🧑‍💻 Who Is This For?](#-who-is-this-for)
- [📄 License](#-license)


## 🚀 How to Get Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/playwright-zero-to-hero.git
cd playwright-zero-to-hero
```

### 2. Install Playwright browsers

For a fresh setup, run the Playwright initializer (recommended):

```bash
npm init playwright@latest
```

This will guide you through setting up Playwright (config file, browsers, example tests, CI setup, etc.).

If you already have a project and only need Playwright Test, install it as a dev dependency:

```bash
npm install -D @playwright/test
npx playwright install
```


## 📂 Struttura della repo

```
playwright-zero-to-hero/
├── .github/
│   └── workflows/
│       └── ci.yml           # Esempio GitHub Action per eseguire i test
├── tests/
│   ├── example.spec.ts      # Primo test di esempio
│   └── helpers/             # Helper functions (es: custom matchers)
├── pages/
│   └── login.page.ts        # Esempio di Page Object Model
├── fixtures/
│   └── test-data.json       # Dati fittizi per test
├── config/
│   ├── playwright.config.ts # Configurazione Playwright
│   └── env.example          # Template variabili ambiente
├── package.json
├── tsconfig.json
├── README.md
└── .gitignore
```

## 📚 What I will practice

* JavaScript fundamentals for Playwright beginners
* Install, run, debug tests, analyze reports and results
* Locator strategies and Playwright best practices
* Interacting with UI components: inputs, radio buttons, checkboxes, lists, tooltips, date pickers, tables, sliders, iFrames
* Page Object Model (POM) architecture with Playwright
* API testing with Playwright: mocking, requests, intercepts, authentication
* Advanced topics:

  * Global setup and teardown
  * Visual testing
  * Mobile device emulation
  * Fixtures
  * Environment variables
  * Test execution in Docker

## 📦 Repo Layout

* `tests/` → All test specs
* `pages/` → Page Object Model classes
* `fixtures/` → Test data & mock JSON
* `config/` → Playwright config and env templates
* `.github/workflows/` → Example CI pipeline


## ⚡ CI/CD with GitHub Actions

A sample workflow file is included: `.github/workflows/ci.yml`
It runs Playwright tests automatically on pushes and pull requests.



## 📜 Esempio test (`tests/example.spec.ts`)

```ts
import { test, expect } from '@playwright/test';

test('homepage has title and links to docs', async ({ page }) => {
  await page.goto('https://playwright.dev/');

  // Expect a title
  await expect(page).toHaveTitle(/Playwright/);

  // Click the get started link
  await page.getByRole('link', { name: 'Get started' }).click();

  // Expect URL to contain intro
  await expect(page).toHaveURL(/.*intro/);
});
````

### Running Tests

Run all tests (headless by default):
```bash
npx playwright test
```

Run in UI mode:

```bash
npx playwright test --ui
```

Run tests in a visible browser (headed mode):
```bash
npx playwright test --headed
```

Run tests only in Chromium (headless):
```bash
npx playwright test --project=chromium
```

Run tests only in Chromium (headed):
```bash
npx playwright test --project=chromium --headed
```

Run a specific test file in Chromium (headed):
```bash
npx playwright test example.spec.ts --project=chromium --headed
```

Run a single test by its title (filter with -g):
```bash
npx playwright test -g "has title" --project=chromium
```

Viewing Reports

After the tests complete, you can view the interactive HTML report:

```Bash
npx playwright show-report
```

This will open a dashboard in your browser with detailed test results.


### Example Test

```ts
test.skip('has title', async ({ page }) => {
  await page.goto('https://playwright.dev/');

  // Expect a title "to contain" a substring.
  await expect(page).toHaveTitle(/Playwright/);
});
````

#### Explanation

* `test.skip` → marks the test as **skipped** (it won’t run).
  Useful when you want to keep the test code but temporarily disable it.
  You can remove `.skip` to enable the test.


### Running a Single Test

You can use `test.only` to focus on a single test while skipping all others.  
This is useful during development when you want to debug or verify just one scenario.

```ts
test.only('has title', async ({ page }) => { 
  await page.goto('https://playwright.dev/');

  // Expect a title "to contain" a substring.
  await expect(page).toHaveTitle(/Playwright/);
});
```

### Explanation

- test.only → runs only this test, ignoring all other tests in the suite.

- page.goto('https://playwright.dev/') → navigates to the Playwright homepage.

- expect(page).toHaveTitle(/Playwright/) → checks that the page title contains the word “Playwright”.

⚠️ Remember to remove .only before committing code, otherwise your CI pipeline will run only this test and skip the rest.

#### Notes

By default, Playwright installs Chromium, Firefox, and WebKit.

All configuration (browsers, timeouts, reporters, testDir, etc.) can be adjusted inside playwright.config.ts.


## 🧑‍💻 Who Is This For?

✨ **MEEEEEEE!!!** (I’m learning Playwright step by step 💙)  
…but also for:

- 🐣 QA Engineers starting with Playwright  
- 🔄 SDETs and Automation Engineers transitioning from other frameworks  
- 👩‍💻 Developers who want to quickly understand Playwright best practices  
- 🌱 Playwright beginners who want to grow their skills  


## 📄 License

MIT
