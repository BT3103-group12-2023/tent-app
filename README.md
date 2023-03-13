# tent-app

## Architecture

### Frontend

#### Sitemap

- `/`
  - `/home` = landing page
  - `/auth` = authentication page (sign in, sign up)
  - `/student-listings` = student listings page
  - `/tutor-listings` = tutor listings page
  - `/tutor/[id]` = public profile page
  - `/me` = personal profile page

### Backend

#### Schema

- **"users"**
  - _general user attributes_
    - id
    - phoneNumber
    - telegramHandle
    - email
  - _tutor profile attributes_
    - isTutor
    - gender
    - education
    - experience
    - levels
    - subjects
    - region
  - **"reviews"**
    - id
    - dateCreated
    - body
    - rating
    - tutorId
    - reviewerId
- **"student-listings"**
  - id
  - dateCreated
  - subject
  - level
  - region
  - description
  - rates
  - userId
- **"tutor-listings"**
  - id
  - dateCreated
  - subject
  - level
  - region
  - description
  - rates
  - tutorId

## Project actions

### Run End-to-End Tests with [Playwright](https://playwright.dev)

```sh
# Install browsers for the first run
npx playwright install

# When testing on CI, must build the project first
npm run build

# Runs the end-to-end tests
npm run test:e2e
# Runs the tests only on Chromium
npm run test:e2e -- --project=chromium
# Runs the tests of a specific file
npm run test:e2e -- tests/example.spec.ts
# Runs the tests in debug mode
npm run test:e2e -- --debug
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
