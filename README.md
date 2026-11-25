# Nuxt UI v3 Starter

## 1. Description

A Nuxt 3 starter application built on Nuxt UI v3, created during ITI study. It provides the base setup (Nuxt UI components, Pinia state, Zod validation, ESLint) for building a Nuxt app.

## 2. Technologies and Versions

- Nuxt ^3.16.0
- @nuxt/ui ^3.0.0
- Pinia ^3.0.1 with @pinia/nuxt ^0.10.1
- Zod ^3.24.2
- @iconify-json/lucide ^1.2.30 and @iconify-json/simple-icons ^1.2.28
- TypeScript ^5.8.2, @nuxt/eslint ^1.2.0 with ESLint ^9.22.0

## 3. Requirements and Dependencies

- Node.js installed
- Dependencies are installed with `npm install` (see `package.json`); `nuxt prepare` runs automatically after install

## 4. Installation and Run Steps

```bash
git clone https://github.com/MostafaNegm222/Nuxt-Project-ITI.git
cd Nuxt-Project-ITI
npm install
npm run dev        # dev server on http://localhost:3000
```

Production:

```bash
npm run build
npm run preview
```

## 5. Environment Variables

None required.

## 6. Usage and Main Features

- Nuxt 3 app scaffold with Nuxt UI v3 components and icons ready to use.
- Pinia store support and Zod schemas available for state and validation.
- Linting with `npm run lint` / `npm run lint:fix`.

## 7. Screenshots / Demo

No live demo; see the Nuxt deployment docs to publish a build.

## 8. Running Tests

No automated tests are configured.
