# Nexus Platform Source Bundle

This file contains the complete handoff source and documentation for the Nexus platform. Recreate the project by copying each section into the matching path.

## README.md

```md
# Nexus Platform

Full-stack investor and entrepreneur collaboration platform.

## Final Output

- Functional web app with authentication, profiles, meetings, video calling, document chamber, payment simulation, and security features.
- Frontend and backend repository structure.
- Deployment-ready frontend and backend configuration.
- API documentation and Postman collection.
- Final demo presentation material.

## Tech Stack

- Frontend: React, Vite, Tailwind CSS, React Router, Lucide icons
- Backend: Node.js HTTP API
- Storage: Browser localStorage for frontend demo state, in-memory API data for backend demo
- Security demo: sanitized request bodies, scrypt password hashing, signed JWT-style tokens, mock 2FA, role-protected profile update route, security headers

## Run Frontend

``\`bash
cd client
npm install
npm run dev
``\`

Frontend URL:

``\`text
http://127.0.0.1:5173/
``\`

## Run Backend

``\`bash
cd sever
npm run dev
``\`

Backend URL:

``\`text
http://127.0.0.1:5000/
``\`

## Demo Login

Entrepreneur:

``\`text
Email: ayesha@nexus.test
Password: demo123
``\`

Investor:

``\`text
Email: daniel@nexus.test
Password: demo123
Mock OTP: 913428
``\`

## Main App Routes

- `/` - dashboard
- `/login` - authentication
- `/register` - profile creation
- `/meetings` - meeting scheduling calendar workflow
- `/documents` - document chamber with e-signature metadata
- `/videocall` - video room demo
- `/payments` - payment simulation, transaction history, security, deployment checklist
- `/api-docs` - API documentation route map
- `/presentation` - final demo presentation

## Handoff Documents

- [API documentation](docs/API_DOCUMENTATION.md)
- [Deployment guide](docs/DEPLOYMENT.md)
- [Final deliverables](docs/FINAL_DELIVERABLES.md)
- [Demo presentation](docs/DEMO_PRESENTATION.md)
- [Postman collection](docs/Nexus.postman_collection.json)

```

## render.yaml

```yaml
services:
  - type: web
    name: nexus-platform-api
    env: node
    rootDir: sever
    buildCommand: npm install
    startCommand: npm start
    envVars:
      - key: JWT_SECRET
        generateValue: true

```

## package.json

```json
{
  "dependencies": {
    "axios": "^1.16.1",
    "framer-motion": "^12.38.0",
    "react-router-dom": "^7.15.1"
  }
}

```

## client/.gitignore

```
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

node_modules
dist
dist-ssr
*.local

# Editor directories and files
.vscode/*
!.vscode/extensions.json
.idea
.DS_Store
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

```

## client/eslint.config.js

```js
import js from '@eslint/js'
import globals from 'globals'
import reactHooks from 'eslint-plugin-react-hooks'
import reactRefresh from 'eslint-plugin-react-refresh'
import { defineConfig, globalIgnores } from 'eslint/config'

export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{js,jsx}'],
    extends: [
      js.configs.recommended,
      reactHooks.configs.flat.recommended,
      reactRefresh.configs.vite,
    ],
    languageOptions: {
      globals: globals.browser,
      parserOptions: { ecmaFeatures: { jsx: true } },
    },
  },
])

```

## client/index.html

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>client</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>

```

## client/package.json

```json
{
  "name": "client",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "axios": "^1.16.1",
    "framer-motion": "^12.38.0",
    "lucide-react": "^1.16.0",
    "react": "^19.2.6",
    "react-dom": "^19.2.6",
    "react-icons": "^5.6.0",
    "react-router-dom": "^7.15.1"
  },
  "devDependencies": {
    "@eslint/js": "^10.0.1",
    "@types/react": "^19.2.14",
    "@types/react-dom": "^19.2.3",
    "@vitejs/plugin-react": "^6.0.1",
    "autoprefixer": "^10.5.0",
    "eslint": "^10.3.0",
    "eslint-plugin-react-hooks": "^7.1.1",
    "eslint-plugin-react-refresh": "^0.5.2",
    "globals": "^17.6.0",
    "postcss": "^8.5.14",
    "tailwindcss": "^3.4.19",
    "vite": "^8.0.12"
  }
}

```

## client/postcss.config.js

```js
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}

```

## client/README.md

```md
# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

```

## client/tailwind.config.js

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
    
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}


```

## client/vercel.json

```json
{
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}

```

## client/vite.config.js

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
})

```

## client/public/favicon.svg

```xml
<svg xmlns="http://www.w3.org/2000/svg" width="48" height="46" fill="none" viewBox="0 0 48 46"><path fill="#863bff" d="M25.946 44.938c-.664.845-2.021.375-2.021-.698V33.937a2.26 2.26 0 0 0-2.262-2.262H10.287c-.92 0-1.456-1.04-.92-1.788l7.48-10.471c1.07-1.497 0-3.578-1.842-3.578H1.237c-.92 0-1.456-1.04-.92-1.788L10.013.474c.214-.297.556-.474.92-.474h28.894c.92 0 1.456 1.04.92 1.788l-7.48 10.471c-1.07 1.498 0 3.579 1.842 3.579h11.377c.943 0 1.473 1.088.89 1.83L25.947 44.94z" style="fill:#863bff;fill:color(display-p3 .5252 .23 1);fill-opacity:1"/><mask id="a" width="48" height="46" x="0" y="0" maskUnits="userSpaceOnUse" style="mask-type:alpha"><path fill="#000" d="M25.842 44.938c-.664.844-2.021.375-2.021-.698V33.937a2.26 2.26 0 0 0-2.262-2.262H10.183c-.92 0-1.456-1.04-.92-1.788l7.48-10.471c1.07-1.498 0-3.579-1.842-3.579H1.133c-.92 0-1.456-1.04-.92-1.787L9.91.473c.214-.297.556-.474.92-.474h28.894c.92 0 1.456 1.04.92 1.788l-7.48 10.471c-1.07 1.498 0 3.578 1.842 3.578h11.377c.943 0 1.473 1.088.89 1.832L25.843 44.94z" style="fill:#000;fill-opacity:1"/></mask><g mask="url(#a)"><g filter="url(#b)"><ellipse cx="5.508" cy="14.704" fill="#ede6ff" rx="5.508" ry="14.704" style="fill:#ede6ff;fill:color(display-p3 .9275 .9033 1);fill-opacity:1" transform="matrix(.00324 1 1 -.00324 -4.47 31.516)"/></g><g filter="url(#c)"><ellipse cx="10.399" cy="29.851" fill="#ede6ff" rx="10.399" ry="29.851" style="fill:#ede6ff;fill:color(display-p3 .9275 .9033 1);fill-opacity:1" transform="matrix(.00324 1 1 -.00324 -39.328 7.883)"/></g><g filter="url(#d)"><ellipse cx="5.508" cy="30.487" fill="#7e14ff" rx="5.508" ry="30.487" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(89.814 -25.913 -14.639)scale(1 -1)"/></g><g filter="url(#e)"><ellipse cx="5.508" cy="30.599" fill="#7e14ff" rx="5.508" ry="30.599" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(89.814 -32.644 -3.334)scale(1 -1)"/></g><g filter="url(#f)"><ellipse cx="5.508" cy="30.599" fill="#7e14ff" rx="5.508" ry="30.599" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="matrix(.00324 1 1 -.00324 -34.34 30.47)"/></g><g filter="url(#g)"><ellipse cx="14.072" cy="22.078" fill="#ede6ff" rx="14.072" ry="22.078" style="fill:#ede6ff;fill:color(display-p3 .9275 .9033 1);fill-opacity:1" transform="rotate(93.35 24.506 48.493)scale(-1 1)"/></g><g filter="url(#h)"><ellipse cx="3.47" cy="21.501" fill="#7e14ff" rx="3.47" ry="21.501" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(89.009 28.708 47.59)scale(-1 1)"/></g><g filter="url(#i)"><ellipse cx="3.47" cy="21.501" fill="#7e14ff" rx="3.47" ry="21.501" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(89.009 28.708 47.59)scale(-1 1)"/></g><g filter="url(#j)"><ellipse cx=".387" cy="8.972" fill="#7e14ff" rx="4.407" ry="29.108" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(39.51 .387 8.972)"/></g><g filter="url(#k)"><ellipse cx="47.523" cy="-6.092" fill="#7e14ff" rx="4.407" ry="29.108" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(37.892 47.523 -6.092)"/></g><g filter="url(#l)"><ellipse cx="41.412" cy="6.333" fill="#47bfff" rx="5.971" ry="9.665" style="fill:#47bfff;fill:color(display-p3 .2799 .748 1);fill-opacity:1" transform="rotate(37.892 41.412 6.333)"/></g><g filter="url(#m)"><ellipse cx="-1.879" cy="38.332" fill="#7e14ff" rx="4.407" ry="29.108" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(37.892 -1.88 38.332)"/></g><g filter="url(#n)"><ellipse cx="-1.879" cy="38.332" fill="#7e14ff" rx="4.407" ry="29.108" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(37.892 -1.88 38.332)"/></g><g filter="url(#o)"><ellipse cx="35.651" cy="29.907" fill="#7e14ff" rx="4.407" ry="29.108" style="fill:#7e14ff;fill:color(display-p3 .4922 .0767 1);fill-opacity:1" transform="rotate(37.892 35.651 29.907)"/></g><g filter="url(#p)"><ellipse cx="38.418" cy="32.4" fill="#47bfff" rx="5.971" ry="15.297" style="fill:#47bfff;fill:color(display-p3 .2799 .748 1);fill-opacity:1" transform="rotate(37.892 38.418 32.4)"/></g></g><defs><filter id="b" width="60.045" height="41.654" x="-19.77" y="16.149" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="7.659"/></filter><filter id="c" width="90.34" height="51.437" x="-54.613" y="-7.533" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="7.659"/></filter><filter id="d" width="79.355" height="29.4" x="-49.64" y="2.03" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="e" width="79.579" height="29.4" x="-45.045" y="20.029" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="f" width="79.579" height="29.4" x="-43.513" y="21.178" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="g" width="74.749" height="58.852" x="15.756" y="-17.901" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="7.659"/></filter><filter id="h" width="61.377" height="25.362" x="23.548" y="2.284" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="i" width="61.377" height="25.362" x="23.548" y="2.284" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="j" width="56.045" height="63.649" x="-27.636" y="-22.853" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="k" width="54.814" height="64.646" x="20.116" y="-38.415" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="l" width="33.541" height="35.313" x="24.641" y="-11.323" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="m" width="54.814" height="64.646" x="-29.286" y="6.009" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="n" width="54.814" height="64.646" x="-29.286" y="6.009" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="o" width="54.814" height="64.646" x="8.244" y="-2.416" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter><filter id="p" width="39.409" height="43.623" x="18.713" y="10.588" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feBlend in="SourceGraphic" in2="BackgroundImageFix" result="shape"/><feGaussianBlur result="effect1_foregroundBlur_2002_17158" stdDeviation="4.596"/></filter></defs></svg>
```

## client/public/icons.svg

```xml
<svg xmlns="http://www.w3.org/2000/svg">
  <symbol id="bluesky-icon" viewBox="0 0 16 17">
    <g clip-path="url(#bluesky-clip)"><path fill="#08060d" d="M7.75 7.735c-.693-1.348-2.58-3.86-4.334-5.097-1.68-1.187-2.32-.981-2.74-.79C.188 2.065.1 2.812.1 3.251s.241 3.602.398 4.13c.52 1.744 2.367 2.333 4.07 2.145-2.495.37-4.71 1.278-1.805 4.512 3.196 3.309 4.38-.71 4.987-2.746.608 2.036 1.307 5.91 4.93 2.746 2.72-2.746.747-4.143-1.747-4.512 1.702.189 3.55-.4 4.07-2.145.156-.528.397-3.691.397-4.13s-.088-1.186-.575-1.406c-.42-.19-1.06-.395-2.741.79-1.755 1.24-3.64 3.752-4.334 5.099"/></g>
    <defs><clipPath id="bluesky-clip"><path fill="#fff" d="M.1.85h15.3v15.3H.1z"/></clipPath></defs>
  </symbol>
  <symbol id="discord-icon" viewBox="0 0 20 19">
    <path fill="#08060d" d="M16.224 3.768a14.5 14.5 0 0 0-3.67-1.153c-.158.286-.343.67-.47.976a13.5 13.5 0 0 0-4.067 0c-.128-.306-.317-.69-.476-.976A14.4 14.4 0 0 0 3.868 3.77C1.546 7.28.916 10.703 1.231 14.077a14.7 14.7 0 0 0 4.5 2.306q.545-.748.965-1.587a9.5 9.5 0 0 1-1.518-.74q.191-.14.372-.293c2.927 1.369 6.107 1.369 8.999 0q.183.152.372.294-.723.437-1.52.74.418.838.963 1.588a14.6 14.6 0 0 0 4.504-2.308c.37-3.911-.63-7.302-2.644-10.309m-9.13 8.234c-.878 0-1.599-.82-1.599-1.82 0-.998.705-1.82 1.6-1.82.894 0 1.614.82 1.599 1.82.001 1-.705 1.82-1.6 1.82m5.91 0c-.878 0-1.599-.82-1.599-1.82 0-.998.705-1.82 1.6-1.82.893 0 1.614.82 1.599 1.82 0 1-.706 1.82-1.6 1.82"/>
  </symbol>
  <symbol id="documentation-icon" viewBox="0 0 21 20">
    <path fill="none" stroke="#aa3bff" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.35" d="m15.5 13.333 1.533 1.322c.645.555.967.833.967 1.178s-.322.623-.967 1.179L15.5 18.333m-3.333-5-1.534 1.322c-.644.555-.966.833-.966 1.178s.322.623.966 1.179l1.534 1.321"/>
    <path fill="none" stroke="#aa3bff" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.35" d="M17.167 10.836v-4.32c0-1.41 0-2.117-.224-2.68-.359-.906-1.118-1.621-2.08-1.96-.599-.21-1.349-.21-2.848-.21-2.623 0-3.935 0-4.983.369-1.684.591-3.013 1.842-3.641 3.428C3 6.449 3 7.684 3 10.154v2.122c0 2.558 0 3.838.706 4.726q.306.383.713.671c.76.536 1.79.64 3.581.66"/>
    <path fill="none" stroke="#aa3bff" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.35" d="M3 10a2.78 2.78 0 0 1 2.778-2.778c.555 0 1.209.097 1.748-.047.48-.129.854-.503.982-.982.145-.54.048-1.194.048-1.749a2.78 2.78 0 0 1 2.777-2.777"/>
  </symbol>
  <symbol id="github-icon" viewBox="0 0 19 19">
    <path fill="#08060d" fill-rule="evenodd" d="M9.356 1.85C5.05 1.85 1.57 5.356 1.57 9.694a7.84 7.84 0 0 0 5.324 7.44c.387.079.528-.168.528-.376 0-.182-.013-.805-.013-1.454-2.165.467-2.616-.935-2.616-.935-.349-.91-.864-1.143-.864-1.143-.71-.48.051-.48.051-.48.787.051 1.2.805 1.2.805.695 1.194 1.817.857 2.268.649.064-.507.27-.857.49-1.052-1.728-.182-3.545-.857-3.545-3.87 0-.857.31-1.558.8-2.104-.078-.195-.349-1 .077-2.078 0 0 .657-.208 2.14.805a7.5 7.5 0 0 1 1.946-.26c.657 0 1.328.092 1.946.26 1.483-1.013 2.14-.805 2.14-.805.426 1.078.155 1.883.078 2.078.502.546.799 1.247.799 2.104 0 3.013-1.818 3.675-3.558 3.87.284.247.528.714.528 1.454 0 1.052-.012 1.896-.012 2.156 0 .208.142.455.528.377a7.84 7.84 0 0 0 5.324-7.441c.013-4.338-3.48-7.844-7.773-7.844" clip-rule="evenodd"/>
  </symbol>
  <symbol id="social-icon" viewBox="0 0 20 20">
    <path fill="none" stroke="#aa3bff" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.35" d="M12.5 6.667a4.167 4.167 0 1 0-8.334 0 4.167 4.167 0 0 0 8.334 0"/>
    <path fill="none" stroke="#aa3bff" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.35" d="M2.5 16.667a5.833 5.833 0 0 1 8.75-5.053m3.837.474.513 1.035c.07.144.257.282.414.309l.93.155c.596.1.736.536.307.965l-.723.73a.64.64 0 0 0-.152.531l.207.903c.164.715-.213.991-.84.618l-.872-.52a.63.63 0 0 0-.577 0l-.872.52c-.624.373-1.003.094-.84-.618l.207-.903a.64.64 0 0 0-.152-.532l-.723-.729c-.426-.43-.289-.864.306-.964l.93-.156a.64.64 0 0 0 .412-.31l.513-1.034c.28-.562.735-.562 1.012 0"/>
  </symbol>
  <symbol id="x-icon" viewBox="0 0 19 19">
    <path fill="#08060d" fill-rule="evenodd" d="M1.893 1.98c.052.072 1.245 1.769 2.653 3.77l2.892 4.114c.183.261.333.48.333.486s-.068.089-.152.183l-.522.593-.765.867-3.597 4.087c-.375.426-.734.834-.798.905a1 1 0 0 0-.118.148c0 .01.236.017.664.017h.663l.729-.83c.4-.457.796-.906.879-.999a692 692 0 0 0 1.794-2.038c.034-.037.301-.34.594-.675l.551-.624.345-.392a7 7 0 0 1 .34-.374c.006 0 .93 1.306 2.052 2.903l2.084 2.965.045.063h2.275c1.87 0 2.273-.003 2.266-.021-.008-.02-1.098-1.572-3.894-5.547-2.013-2.862-2.28-3.246-2.273-3.266.008-.019.282-.332 2.085-2.38l2-2.274 1.567-1.782c.022-.028-.016-.03-.65-.03h-.674l-.3.342a871 871 0 0 1-1.782 2.025c-.067.075-.405.458-.75.852a100 100 0 0 1-.803.91c-.148.172-.299.344-.99 1.127-.304.343-.32.358-.345.327-.015-.019-.904-1.282-1.976-2.808L6.365 1.85H1.8zm1.782.91 8.078 11.294c.772 1.08 1.413 1.973 1.425 1.984.016.017.241.02 1.05.017l1.03-.004-2.694-3.766L7.796 5.75 5.722 2.852l-1.039-.004-1.039-.004z" clip-rule="evenodd"/>
  </symbol>
</svg>

```

## client/src/App.css

```css
.counter {
  font-size: 16px;
  padding: 5px 10px;
  border-radius: 5px;
  color: var(--accent);
  background: var(--accent-bg);
  border: 2px solid transparent;
  transition: border-color 0.3s;
  margin-bottom: 24px;

  &:hover {
    border-color: var(--accent-border);
  }
  &:focus-visible {
    outline: 2px solid var(--accent);
    outline-offset: 2px;
  }
}

.hero {
  position: relative;

  .base,
  .framework,
  .vite {
    inset-inline: 0;
    margin: 0 auto;
  }

  .base {
    width: 170px;
    position: relative;
    z-index: 0;
  }

  .framework,
  .vite {
    position: absolute;
  }

  .framework {
    z-index: 1;
    top: 34px;
    height: 28px;
    transform: perspective(2000px) rotateZ(300deg) rotateX(44deg) rotateY(39deg)
      scale(1.4);
  }

  .vite {
    z-index: 0;
    top: 107px;
    height: 26px;
    width: auto;
    transform: perspective(2000px) rotateZ(300deg) rotateX(40deg) rotateY(39deg)
      scale(0.8);
  }
}

#center {
  display: flex;
  flex-direction: column;
  gap: 25px;
  place-content: center;
  place-items: center;
  flex-grow: 1;

  @media (max-width: 1024px) {
    padding: 32px 20px 24px;
    gap: 18px;
  }
}

#next-steps {
  display: flex;
  border-top: 1px solid var(--border);
  text-align: left;

  & > div {
    flex: 1 1 0;
    padding: 32px;
    @media (max-width: 1024px) {
      padding: 24px 20px;
    }
  }

  .icon {
    margin-bottom: 16px;
    width: 22px;
    height: 22px;
  }

  @media (max-width: 1024px) {
    flex-direction: column;
    text-align: center;
  }
}

#docs {
  border-right: 1px solid var(--border);

  @media (max-width: 1024px) {
    border-right: none;
    border-bottom: 1px solid var(--border);
  }
}

#next-steps ul {
  list-style: none;
  padding: 0;
  display: flex;
  gap: 8px;
  margin: 32px 0 0;

  .logo {
    height: 18px;
  }

  a {
    color: var(--text-h);
    font-size: 16px;
    border-radius: 6px;
    background: var(--social-bg);
    display: flex;
    padding: 6px 12px;
    align-items: center;
    gap: 8px;
    text-decoration: none;
    transition: box-shadow 0.3s;

    &:hover {
      box-shadow: var(--shadow);
    }
    .button-icon {
      height: 18px;
      width: 18px;
    }
  }

  @media (max-width: 1024px) {
    margin-top: 20px;
    flex-wrap: wrap;
    justify-content: center;

    li {
      flex: 1 1 calc(50% - 8px);
    }

    a {
      width: 100%;
      justify-content: center;
      box-sizing: border-box;
    }
  }
}

#spacer {
  height: 88px;
  border-top: 1px solid var(--border);
  @media (max-width: 1024px) {
    height: 48px;
  }
}

.ticks {
  position: relative;
  width: 100%;

  &::before,
  &::after {
    content: '';
    position: absolute;
    top: -4.5px;
    border: 5px solid transparent;
  }

  &::before {
    left: 0;
    border-left-color: var(--border);
  }
  &::after {
    right: 0;
    border-right-color: var(--border);
  }
}

```

## client/src/App.jsx

```jsx
import { Navigate, Route, Routes } from "react-router-dom";

import MainLayout from "./layouts/MainLayout";
import { NexusProvider } from "./context/NexusContext";
import ApiDocs from "./pages/api-docs";
import Dashboard from "./pages/dashboard";
import Documents from "./pages/documents";
import Login from "./pages/login";
import Meetings from "./pages/meetings";
import Payments from "./pages/payments";
import Presentation from "./pages/presentation";
import Register from "./pages/register";
import VideoCall from "./pages/videocall";

function App() {
  return (
    <NexusProvider>
      <Routes>
        <Route path="/login" element={<Login />} />
        <Route path="/register" element={<Register />} />
        <Route path="/" element={<MainLayout />}>
          <Route index element={<Dashboard />} />
          <Route path="dashboard" element={<Dashboard />} />
          <Route path="meetings" element={<Meetings />} />
          <Route path="documents" element={<Documents />} />
          <Route path="videocall" element={<VideoCall />} />
          <Route path="payments" element={<Payments />} />
          <Route path="api-docs" element={<ApiDocs />} />
          <Route path="presentation" element={<Presentation />} />
        </Route>
        <Route path="*" element={<Navigate to="/" replace />} />
      </Routes>
    </NexusProvider>
  );
}

export default App;

```

## client/src/index.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-width: 320px;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  background: #f1f5f9;
}

button,
input,
select,
textarea {
  font: inherit;
}

```

## client/src/main.jsx

```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import { BrowserRouter } from "react-router-dom";

import App from "./App.jsx";
import "./index.css";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </StrictMode>,
);

```

## client/src/components/navbar.jsx

```jsx
import { Bell, LogIn, Search, UserRound } from "lucide-react";
import { Link } from "react-router-dom";

import { useNexus } from "../context/NexusContext";

const Navbar = () => {
  const { currentUser } = useNexus();

  return (
    <header className="h-16 border-b border-slate-200 bg-white px-4 sm:px-6 flex items-center justify-between gap-4">
      <div>
        <p className="text-xs uppercase tracking-wide text-slate-500">Nexus Collaboration Platform</p>
        <h2 className="text-lg font-semibold text-slate-950">Welcome back, {currentUser.name}</h2>
      </div>

      <div className="hidden md:flex h-10 w-full max-w-md items-center gap-2 rounded-md border border-slate-200 bg-slate-50 px-3">
        <Search size={18} className="text-slate-400" />
        <input
          className="w-full bg-transparent text-sm outline-none placeholder:text-slate-400"
          placeholder="Search meetings, investors, documents"
        />
      </div>

      <div className="flex items-center gap-2">
        <button className="grid h-10 w-10 place-items-center rounded-md border border-slate-200 text-slate-600 hover:bg-slate-50" title="Notifications">
          <Bell size={18} />
        </button>
        <Link
          to="/login"
          className="grid h-10 w-10 place-items-center rounded-md border border-slate-200 text-slate-600 hover:bg-slate-50"
          title="Login"
        >
          <LogIn size={18} />
        </Link>
        <div className="hidden sm:flex h-10 items-center gap-2 rounded-md border border-slate-200 px-3">
          <UserRound size={18} className="text-emerald-600" />
          <span className="text-sm font-medium text-slate-800">{currentUser.role}</span>
        </div>
      </div>
    </header>
  );
};

export default Navbar;

```

## client/src/components/sidebar.jsx

```jsx
import { BookOpen, Calendar, CreditCard, FileText, LayoutDashboard, Presentation, Video } from "lucide-react";
import { NavLink } from "react-router-dom";

const links = [
  { to: "/", label: "Dashboard", icon: LayoutDashboard },
  { to: "/meetings", label: "Meetings", icon: Calendar },
  { to: "/documents", label: "Documents", icon: FileText },
  { to: "/videocall", label: "Video Call", icon: Video },
  { to: "/payments", label: "Payments", icon: CreditCard },
  { to: "/api-docs", label: "API Docs", icon: BookOpen },
  { to: "/presentation", label: "Presentation", icon: Presentation },
];

const Sidebar = () => {
  return (
    <aside className="w-full border-b border-slate-800 bg-slate-950 text-white lg:h-screen lg:w-64 lg:border-b-0 lg:border-r">
      <div className="flex h-16 items-center justify-between px-5 lg:h-auto lg:block lg:py-6">
        <div>
          <h1 className="text-2xl font-bold">Nexus</h1>
          <p className="hidden text-sm text-slate-400 lg:block">Investor and founder workspace</p>
        </div>
      </div>

      <nav className="flex gap-2 overflow-x-auto px-3 pb-3 lg:block lg:space-y-2 lg:px-4">
        {links.map(({ to, label, icon: Icon }) => (
          <NavLink
            key={to}
            to={to}
            end={to === "/"}
            className={({ isActive }) =>
              `flex min-w-fit items-center gap-3 rounded-md px-3 py-3 text-sm font-medium transition ${
                isActive
                  ? "bg-emerald-500 text-slate-950"
                  : "text-slate-300 hover:bg-slate-900 hover:text-white"
              }`
            }
          >
            <Icon size={18} />
            {label}
          </NavLink>
        ))}
      </nav>
    </aside>
  );
};

export default Sidebar;

```

## client/src/components/StatCard.jsx

```jsx
import { motion } from "framer-motion";

const StatCard = ({ title, value, icon: Icon, tone = "emerald" }) => {
  const tones = {
    emerald: "bg-emerald-50 text-emerald-700 border-emerald-100",
    blue: "bg-sky-50 text-sky-700 border-sky-100",
    amber: "bg-amber-50 text-amber-700 border-amber-100",
    rose: "bg-rose-50 text-rose-700 border-rose-100",
  };

  return (
    <motion.div
      whileHover={{ y: -3 }}
      className={`rounded-lg border p-5 shadow-sm ${tones[tone]}`}
    >
      <div className="flex items-center justify-between">
        <h3 className="text-sm font-medium opacity-80">{title}</h3>
        {Icon ? <Icon size={20} /> : null}
      </div>
      <p className="mt-3 text-3xl font-bold">{value}</p>
    </motion.div>
  );
};

export default StatCard;

```

## client/src/context/NexusContext.jsx

```jsx
/* eslint-disable react-refresh/only-export-components */
import { createContext, useContext, useEffect, useMemo, useReducer } from "react";

const STORAGE_KEY = "nexus-platform-state-v1";

const initialState = {
  currentUserId: "u1",
  users: [
    {
      id: "u1",
      name: "Ayesha Khan",
      email: "ayesha@nexus.test",
      password: "demo123",
      role: "entrepreneur",
      company: "Luma Health",
      bio: "Founder building AI-powered remote patient intake for clinics.",
      location: "Lahore, PK",
      interests: ["HealthTech", "Seed", "AI"],
      investmentHistory: "Raised $220k pre-seed from angel investors.",
    },
    {
      id: "u2",
      name: "Daniel Reed",
      email: "daniel@nexus.test",
      password: "demo123",
      role: "investor",
      company: "Northstar Ventures",
      bio: "Early-stage investor focused on B2B SaaS and developer tools.",
      location: "Austin, US",
      interests: ["SaaS", "FinTech", "Climate"],
      investmentHistory: "18 seed deals, 4 follow-on rounds, 2 exits.",
    },
  ],
  meetings: [
    {
      id: "m1",
      title: "Seed pitch review",
      hostId: "u1",
      guestId: "u2",
      date: "2026-05-18",
      time: "10:00",
      duration: 45,
      status: "Accepted",
      mode: "Video",
      agenda: "Review deck, traction, and fundraising targets.",
    },
    {
      id: "m2",
      title: "Product demo",
      hostId: "u2",
      guestId: "u1",
      date: "2026-05-20",
      time: "14:30",
      duration: 30,
      status: "Pending",
      mode: "Video",
      agenda: "Walk through MVP and discuss integration milestones.",
    },
  ],
  documents: [
    {
      id: "d1",
      title: "Investor Pitch Deck.pdf",
      ownerId: "u1",
      type: "Pitch Deck",
      size: "3.2 MB",
      status: "Signed",
      uploadedAt: "2026-05-14",
      storage: "Cloud",
      notes: "Ready for investor review.",
      signature: "A. Khan",
    },
    {
      id: "d2",
      title: "NDA Draft.docx",
      ownerId: "u2",
      type: "Legal",
      size: "820 KB",
      status: "Review",
      uploadedAt: "2026-05-15",
      storage: "Cloud",
      notes: "Legal terms pending confirmation.",
      signature: "",
    },
  ],
  room: {
    name: "nexus-seed-room",
    connected: false,
    micOn: true,
    cameraOn: true,
    screenShare: false,
    participants: ["Ayesha Khan", "Daniel Reed"],
    chat: [
      { id: "c1", author: "Daniel", body: "Ready when you are." },
      { id: "c2", author: "Ayesha", body: "Deck is uploaded in documents." },
    ],
  },
  transactions: [
    {
      id: "tx1",
      type: "Deposit",
      party: "Northstar Ventures",
      amount: 25000,
      currency: "USD",
      status: "Completed",
      createdAt: "2026-05-15",
      reference: "pi_seed_round_001",
    },
    {
      id: "tx2",
      type: "Transfer",
      party: "Luma Health",
      amount: 5000,
      currency: "USD",
      status: "Pending",
      createdAt: "2026-05-16",
      reference: "tr_milestone_002",
    },
  ],
  security: {
    passwordHashing: true,
    jwtTokens: true,
    twoFactorEnabled: false,
    roleProtectedRoutes: true,
    lastOtp: "428913",
    validationMode: "Strict",
  },
  deployment: {
    frontend: "Vercel ready",
    backend: "Render/Heroku/AWS ready",
    apiDocs: "Swagger/Postman outline ready",
    demo: "Working flows prepared",
  },
  activity: [
    "Payment sandbox created for Week 3",
    "Pitch deck signed and locked for sharing",
    "Seed pitch review accepted by Daniel Reed",
    "NDA Draft moved to review",
  ],
};

const NexusContext = createContext(null);

function loadState() {
  try {
    const stored = window.localStorage.getItem(STORAGE_KEY);
    if (!stored) return initialState;
    return { ...initialState, ...JSON.parse(stored) };
  } catch {
    return initialState;
  }
}

function sanitizeText(value) {
  return String(value ?? "")
    .replace(/[<>]/g, "")
    .replace(/\s+/g, " ")
    .trim();
}

function overlap(startA, durationA, startB, durationB) {
  const a = startA.getTime();
  const b = startB.getTime();
  return a < b + durationB * 60000 && b < a + durationA * 60000;
}

function reducer(state, action) {
  switch (action.type) {
    case "login": {
      const user = state.users.find(
        (item) =>
          item.email.toLowerCase() === action.email.toLowerCase() &&
          item.password === action.password,
      );
      return user ? { ...state, currentUserId: user.id } : state;
    }
    case "register": {
      const id = `u${Date.now()}`;
      const user = {
        id,
        name: action.payload.name,
        email: action.payload.email,
        password: action.payload.password,
        role: action.payload.role,
        company: action.payload.company,
        bio: "New Nexus member building a collaboration profile.",
        location: action.payload.location,
        interests: action.payload.interests.split(",").map((item) => item.trim()).filter(Boolean),
        investmentHistory: action.payload.role === "investor" ? "New investment profile." : "Fundraising history not added yet.",
      };
      return {
        ...state,
        currentUserId: id,
        users: [...state.users, user],
        activity: [`${user.name} joined Nexus as ${user.role}`, ...state.activity],
      };
    }
    case "updateProfile":
      return {
        ...state,
        users: state.users.map((user) =>
          user.id === state.currentUserId ? { ...user, ...action.payload } : user,
        ),
        activity: ["Profile details updated", ...state.activity],
      };
    case "createMeeting": {
      const start = new Date(`${action.payload.date}T${action.payload.time}`);
      const conflict = state.meetings.some((meeting) => {
        const meetingStart = new Date(`${meeting.date}T${meeting.time}`);
        return (
          meeting.status !== "Rejected" &&
          meeting.date === action.payload.date &&
          overlap(start, Number(action.payload.duration), meetingStart, Number(meeting.duration))
        );
      });
      const meeting = {
        id: `m${Date.now()}`,
        hostId: state.currentUserId,
        status: conflict ? "Conflict" : "Pending",
        ...action.payload,
        duration: Number(action.payload.duration),
      };
      return {
        ...state,
        meetings: [meeting, ...state.meetings],
        activity: [
          conflict
            ? `Conflict detected for ${meeting.title}`
            : `Meeting request created: ${meeting.title}`,
          ...state.activity,
        ],
      };
    }
    case "setMeetingStatus":
      return {
        ...state,
        meetings: state.meetings.map((meeting) =>
          meeting.id === action.id ? { ...meeting, status: action.status } : meeting,
        ),
        activity: [`Meeting marked ${action.status}`, ...state.activity],
      };
    case "addDocument": {
      const document = {
        id: `d${Date.now()}`,
        ownerId: state.currentUserId,
        uploadedAt: new Date().toISOString().slice(0, 10),
        storage: "Cloud",
        status: "Review",
        signature: "",
        notes: "Uploaded from workspace demo.",
        ...action.payload,
      };
      return {
        ...state,
        documents: [document, ...state.documents],
        activity: [`Document uploaded: ${document.title}`, ...state.activity],
      };
    }
    case "signDocument":
      return {
        ...state,
        documents: state.documents.map((document) =>
          document.id === action.id
            ? { ...document, status: "Signed", signature: action.signature }
            : document,
        ),
        activity: ["Document e-signature captured", ...state.activity],
      };
    case "setRoom":
      return { ...state, room: { ...state.room, ...action.payload } };
    case "sendMessage":
      return {
        ...state,
        room: {
          ...state.room,
          chat: [
            ...state.room.chat,
            { id: `c${Date.now()}`, author: action.author, body: action.body },
          ],
        },
      };
    case "createTransaction": {
      const amount = Number(action.payload.amount);
      const transaction = {
        id: `tx${Date.now()}`,
        type: action.payload.type,
        party: sanitizeText(action.payload.party),
        amount,
        currency: action.payload.currency,
        status: amount > 0 ? "Pending" : "Failed",
        createdAt: new Date().toISOString().slice(0, 10),
        reference: `sandbox_${Date.now()}`,
      };
      return {
        ...state,
        transactions: [transaction, ...state.transactions],
        activity: [`Payment ${transaction.status.toLowerCase()}: ${transaction.type} ${transaction.currency} ${transaction.amount}`, ...state.activity],
      };
    }
    case "setTransactionStatus":
      return {
        ...state,
        transactions: state.transactions.map((transaction) =>
          transaction.id === action.id ? { ...transaction, status: action.status } : transaction,
        ),
        activity: [`Transaction marked ${action.status}`, ...state.activity],
      };
    case "toggleSecurity":
      return {
        ...state,
        security: {
          ...state.security,
          [action.key]: !state.security[action.key],
          lastOtp: action.key === "twoFactorEnabled" ? String(Math.floor(100000 + Math.random() * 900000)) : state.security.lastOtp,
        },
        activity: [`Security setting updated: ${action.key}`, ...state.activity],
      };
    default:
      return state;
  }
}

export function NexusProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, undefined, loadState);

  useEffect(() => {
    window.localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
  }, [state]);

  const value = useMemo(() => {
    const currentUser = state.users.find((user) => user.id === state.currentUserId) ?? state.users[0];
    return { ...state, currentUser, dispatch };
  }, [state]);

  return <NexusContext.Provider value={value}>{children}</NexusContext.Provider>;
}

export function useNexus() {
  const value = useContext(NexusContext);
  if (!value) {
    throw new Error("useNexus must be used inside NexusProvider");
  }
  return value;
}

```

## client/src/layouts/MainLayout.jsx

```jsx
import { Outlet } from "react-router-dom";

import Navbar from "../components/navbar";
import Sidebar from "../components/sidebar";

const MainLayout = () => {
  return (
    <div className="min-h-screen bg-slate-100 lg:flex">
      <Sidebar />
      <div className="min-w-0 flex-1">
        <Navbar />
        <main className="min-h-[calc(100vh-4rem)]">
          <Outlet />
        </main>
      </div>
    </div>
  );
};

export default MainLayout;

```

## client/src/pages/api-docs.jsx

```jsx
const groups = [
  {
    title: "Authentication",
    routes: [
      ["POST", "/api/auth/login", "Returns signed token, user profile, and mock 2FA challenge when enabled."],
      ["POST", "/api/auth/register", "Creates a profile with sanitized input and hashed password."],
      ["POST", "/api/auth/verify-2fa", "Verifies the mock OTP code for demo flows."],
    ],
  },
  {
    title: "Collaboration",
    routes: [
      ["GET", "/api/profiles", "Lists investor and entrepreneur profiles."],
      ["PUT", "/api/profiles/:id", "Updates profile fields with role-protected access."],
      ["GET", "/api/meetings", "Returns scheduling records."],
      ["POST", "/api/meetings", "Creates a meeting and flags calendar conflicts."],
      ["PATCH", "/api/meetings/:id", "Accepts, rejects, or updates a meeting."],
    ],
  },
  {
    title: "Documents, Video and Payments",
    routes: [
      ["POST", "/api/documents", "Stores document metadata and mock cloud URL."],
      ["PATCH", "/api/documents/:id/sign", "Captures e-signature metadata."],
      ["GET", "/api/video/rooms/:name", "Reads room state and participants."],
      ["POST", "/api/video/rooms/:name/chat", "Adds room chat messages."],
      ["GET", "/api/payments/transactions", "Returns transaction history."],
      ["POST", "/api/payments/create-intent", "Creates sandbox deposit, withdraw, or transfer transaction."],
      ["PATCH", "/api/payments/transactions/:id", "Updates payment status."],
    ],
  },
];

export default function ApiDocs() {
  return (
    <div className="space-y-6 p-4 sm:p-6">
      <section className="rounded-lg bg-white p-5 shadow-sm">
        <p className="text-sm font-medium text-emerald-700">Swagger/Postman outline</p>
        <h1 className="mt-1 text-2xl font-bold text-slate-950">Nexus API documentation</h1>
        <p className="mt-2 max-w-3xl text-sm text-slate-600">
          This page gives the client a clean route map for the backend endpoints delivered with the prototype.
        </p>
      </section>

      <section className="grid gap-6 xl:grid-cols-3">
        {groups.map((group) => (
          <article key={group.title} className="rounded-lg bg-white p-5 shadow-sm">
            <h2 className="text-lg font-semibold text-slate-950">{group.title}</h2>
            <div className="mt-4 space-y-3">
              {group.routes.map(([method, path, detail]) => (
                <div key={`${method}-${path}`} className="rounded-md border border-slate-200 p-3">
                  <div className="flex items-center gap-2">
                    <span className="rounded bg-slate-950 px-2 py-1 text-xs font-bold text-white">{method}</span>
                    <code className="text-sm font-semibold text-slate-800">{path}</code>
                  </div>
                  <p className="mt-2 text-sm text-slate-600">{detail}</p>
                </div>
              ))}
            </div>
          </article>
        ))}
      </section>
    </div>
  );
}

```

## client/src/pages/dashboard.jsx

```jsx
import { CalendarClock, FileSignature, Handshake, UsersRound } from "lucide-react";

import StatCard from "../components/StatCard";
import { useNexus } from "../context/NexusContext";

const statusClass = {
  Accepted: "bg-emerald-100 text-emerald-700",
  Pending: "bg-amber-100 text-amber-700",
  Conflict: "bg-rose-100 text-rose-700",
  Rejected: "bg-slate-200 text-slate-600",
};

const Dashboard = () => {
  const { activity, currentUser, documents, meetings, users, dispatch } = useNexus();
  const investors = users.filter((user) => user.role === "investor").length;
  const signedDocuments = documents.filter((doc) => doc.status === "Signed").length;
  const upcomingMeetings = meetings.slice(0, 4);

  const handleProfileChange = (event) => {
    const { name, value } = event.target;
    dispatch({ type: "updateProfile", payload: { [name]: value } });
  };

  return (
    <div className="space-y-6 p-4 sm:p-6">
      <section className="rounded-lg bg-white p-5 shadow-sm">
        <div className="flex flex-col justify-between gap-4 lg:flex-row lg:items-center">
          <div>
            <p className="text-sm font-medium text-emerald-700">Full stack demo workspace</p>
            <h1 className="mt-1 text-3xl font-bold text-slate-950">Investor and entrepreneur collaboration</h1>
            <p className="mt-2 max-w-3xl text-sm text-slate-600">
              A working Nexus prototype with profiles, scheduling, document handling, e-signature state, and a video-room interface.
            </p>
          </div>
          <div className="rounded-md border border-slate-200 bg-slate-50 px-4 py-3 text-sm text-slate-700">
            Active profile: <span className="font-semibold capitalize">{currentUser.role}</span>
          </div>
        </div>
      </section>

      <section className="grid gap-4 md:grid-cols-2 xl:grid-cols-4">
        <StatCard title="Total meetings" value={meetings.length} icon={CalendarClock} tone="emerald" />
        <StatCard title="Investors" value={investors} icon={UsersRound} tone="blue" />
        <StatCard title="Documents" value={documents.length} icon={FileSignature} tone="amber" />
        <StatCard title="Signed files" value={signedDocuments} icon={Handshake} tone="rose" />
      </section>

      <section className="grid gap-6 xl:grid-cols-[1.15fr_0.85fr]">
        <div className="rounded-lg bg-white p-5 shadow-sm">
          <div className="mb-4 flex items-center justify-between">
            <h2 className="text-lg font-semibold text-slate-950">Upcoming meetings</h2>
            <span className="text-sm text-slate-500">Conflict detection enabled</span>
          </div>
          <div className="overflow-x-auto">
            <table className="w-full min-w-[640px] text-left text-sm">
              <thead className="border-b border-slate-200 text-xs uppercase text-slate-500">
                <tr>
                  <th className="py-3">Meeting</th>
                  <th className="py-3">Date</th>
                  <th className="py-3">Time</th>
                  <th className="py-3">Mode</th>
                  <th className="py-3">Status</th>
                </tr>
              </thead>
              <tbody className="divide-y divide-slate-100">
                {upcomingMeetings.map((meeting) => (
                  <tr key={meeting.id}>
                    <td className="py-3 font-medium text-slate-900">{meeting.title}</td>
                    <td className="py-3 text-slate-600">{meeting.date}</td>
                    <td className="py-3 text-slate-600">{meeting.time}</td>
                    <td className="py-3 text-slate-600">{meeting.mode}</td>
                    <td className="py-3">
                      <span className={`rounded-full px-2.5 py-1 text-xs font-semibold ${statusClass[meeting.status]}`}>
                        {meeting.status}
                      </span>
                    </td>
                  </tr>
                ))}
              </tbody>
            </table>
          </div>
        </div>

        <div className="rounded-lg bg-white p-5 shadow-sm">
          <h2 className="text-lg font-semibold text-slate-950">Profile center</h2>
          <div className="mt-4 grid gap-3">
            <label className="text-sm font-medium text-slate-700">
              Company
              <input
                name="company"
                value={currentUser.company}
                onChange={handleProfileChange}
                className="mt-1 w-full rounded-md border border-slate-200 px-3 py-2 text-sm outline-none focus:border-emerald-500"
              />
            </label>
            <label className="text-sm font-medium text-slate-700">
              Bio
              <textarea
                name="bio"
                value={currentUser.bio}
                onChange={handleProfileChange}
                rows="4"
                className="mt-1 w-full resize-none rounded-md border border-slate-200 px-3 py-2 text-sm outline-none focus:border-emerald-500"
              />
            </label>
          </div>
        </div>
      </section>

      <section className="rounded-lg bg-white p-5 shadow-sm">
        <h2 className="text-lg font-semibold text-slate-950">Recent activity</h2>
        <div className="mt-4 grid gap-3 md:grid-cols-3">
          {activity.slice(0, 6).map((item, index) => (
            <div key={`${item}-${index}`} className="rounded-md border border-slate-200 p-3 text-sm text-slate-700">
              {item}
            </div>
          ))}
        </div>
      </section>
    </div>
  );
};

export default Dashboard;

```

## client/src/pages/documents.jsx

```jsx
import { FileCheck2, FileUp, PenLine } from "lucide-react";
import { useState } from "react";

import { useNexus } from "../context/NexusContext";

const statusClass = {
  Signed: "bg-emerald-100 text-emerald-700",
  Review: "bg-amber-100 text-amber-700",
  Draft: "bg-slate-100 text-slate-600",
};

export default function Documents() {
  const { currentUser, dispatch, documents, users } = useNexus();
  const [signature, setSignature] = useState(currentUser.name);

  const addDocument = (event) => {
    const file = event.target.files?.[0];
    if (!file) return;
    dispatch({
      type: "addDocument",
      payload: {
        title: file.name,
        type: file.type.includes("pdf") ? "PDF" : "Document",
        size: `${Math.max(file.size / 1024 / 1024, 0.1).toFixed(1)} MB`,
      },
    });
    event.target.value = "";
  };

  const ownerName = (id) => users.find((user) => user.id === id)?.name ?? "Nexus member";

  return (
    <div className="space-y-6 p-4 sm:p-6">
      <section className="rounded-lg bg-white p-5 shadow-sm">
        <div className="flex flex-col justify-between gap-4 lg:flex-row lg:items-center">
          <div>
            <p className="text-sm font-medium text-emerald-700">Document Processing Chamber</p>
            <h1 className="mt-1 text-2xl font-bold text-slate-950">Upload, preview, store metadata, and sign</h1>
            <p className="mt-2 max-w-3xl text-sm text-slate-600">
              This module mirrors the backend requirements for cloud storage, DB metadata, PDF preview, and e-signature state.
            </p>
          </div>
          <label className="inline-flex cursor-pointer items-center justify-center gap-2 rounded-md bg-emerald-500 px-4 py-3 text-sm font-semibold text-slate-950 hover:bg-emerald-400">
            <FileUp size={18} />
            Upload file
            <input type="file" className="sr-only" onChange={addDocument} />
          </label>
        </div>
      </section>

      <section className="grid gap-6 xl:grid-cols-[1fr_360px]">
        <div className="rounded-lg bg-white p-5 shadow-sm">
          <h2 className="text-lg font-semibold text-slate-950">Document vault</h2>
          <div className="mt-4 grid gap-4">
            {documents.map((document) => (
              <article key={document.id} className="rounded-lg border border-slate-200 p-4">
                <div className="flex flex-col justify-between gap-4 lg:flex-row lg:items-center">
                  <div className="min-w-0">
                    <div className="flex flex-wrap items-center gap-2">
                      <FileCheck2 size={18} className="text-emerald-700" />
                      <h3 className="truncate text-lg font-semibold text-slate-950">{document.title}</h3>
                      <span className={`rounded-full px-2.5 py-1 text-xs font-semibold ${statusClass[document.status]}`}>
                        {document.status}
                      </span>
                    </div>
                    <p className="mt-2 text-sm text-slate-600">{document.notes}</p>
                    <div className="mt-3 flex flex-wrap gap-3 text-sm text-slate-500">
                      <span>{document.type}</span>
                      <span>{document.size}</span>
                      <span>{document.storage}</span>
                      <span>Owner: {ownerName(document.ownerId)}</span>
                      <span>Uploaded: {document.uploadedAt}</span>
                    </div>
                  </div>
                  <button
                    onClick={() => dispatch({ type: "signDocument", id: document.id, signature })}
                    className="inline-flex items-center justify-center gap-2 rounded-md border border-emerald-200 px-4 py-2 text-sm font-semibold text-emerald-700 hover:bg-emerald-50"
                  >
                    <PenLine size={17} />
                    Sign
                  </button>
                </div>
                {document.signature ? (
                  <div className="mt-4 rounded-md bg-slate-50 px-3 py-2 text-sm text-slate-700">
                    E-signature: <span className="font-semibold">{document.signature}</span>
                  </div>
                ) : null}
              </article>
            ))}
          </div>
        </div>

        <aside className="rounded-lg bg-white p-5 shadow-sm">
          <h2 className="text-lg font-semibold text-slate-950">Signature pad</h2>
          <p className="mt-2 text-sm text-slate-600">Type the signer name, then apply it to any document.</p>
          <input
            value={signature}
            onChange={(event) => setSignature(event.target.value)}
            className="mt-4 w-full rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500"
          />
          <div className="mt-4 rounded-lg border border-dashed border-slate-300 bg-slate-50 p-6 text-center">
            <p className="font-serif text-3xl text-slate-800">{signature || "Signature"}</p>
            <p className="mt-2 text-xs uppercase tracking-wide text-slate-400">Stored as signature metadata</p>
          </div>
        </aside>
      </section>
    </div>
  );
}

```

## client/src/pages/login.jsx

```jsx
import { useState } from "react";
import { Link, useNavigate } from "react-router-dom";

import { useNexus } from "../context/NexusContext";

export default function Login() {
  const navigate = useNavigate();
  const { dispatch } = useNexus();
  const [form, setForm] = useState({ email: "ayesha@nexus.test", password: "demo123" });
  const [error, setError] = useState("");

  const handleLogin = (event) => {
    event.preventDefault();
    if (!form.email || !form.password) {
      setError("Please enter email and password.");
      return;
    }
    dispatch({ type: "login", email: form.email, password: form.password });
    navigate("/");
  };

  return (
    <div className="min-h-screen bg-slate-950 px-4 py-10 text-white">
      <div className="mx-auto grid min-h-[calc(100vh-5rem)] max-w-5xl items-center gap-8 lg:grid-cols-[1fr_420px]">
        <section>
          <p className="text-sm font-semibold uppercase tracking-wide text-emerald-300">Nexus Platform</p>
          <h1 className="mt-3 text-4xl font-bold">Secure access for investors and entrepreneurs</h1>
          <p className="mt-4 max-w-xl text-slate-300">
            Demo login is prefilled so the client can immediately inspect dashboards, profiles, meetings, documents, and video collaboration flows.
          </p>
        </section>

        <section className="rounded-lg bg-white p-6 text-slate-950 shadow-xl">
          <h2 className="text-2xl font-bold">Sign in</h2>
          <form onSubmit={handleLogin} className="mt-6 space-y-4">
            <input
              type="email"
              placeholder="Email"
              className="w-full rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500"
              value={form.email}
              onChange={(event) => setForm({ ...form, email: event.target.value })}
            />
            <input
              type="password"
              placeholder="Password"
              className="w-full rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500"
              value={form.password}
              onChange={(event) => setForm({ ...form, password: event.target.value })}
            />
            {error ? <p className="text-sm text-rose-600">{error}</p> : null}
            <button type="submit" className="w-full rounded-md bg-emerald-500 py-3 font-semibold text-slate-950 hover:bg-emerald-400">
              Sign in
            </button>
          </form>
          <p className="mt-5 text-center text-sm text-slate-600">
            Need a new account?{" "}
            <Link to="/register" className="font-semibold text-emerald-700">
              Register
            </Link>
          </p>
        </section>
      </div>
    </div>
  );
}

```

## client/src/pages/meetings.jsx

```jsx
import { CalendarPlus, Check, Clock, X } from "lucide-react";
import { useState } from "react";

import { useNexus } from "../context/NexusContext";

const statusClass = {
  Accepted: "bg-emerald-100 text-emerald-700",
  Pending: "bg-amber-100 text-amber-700",
  Conflict: "bg-rose-100 text-rose-700",
  Rejected: "bg-slate-200 text-slate-600",
};

export default function Meetings() {
  const { currentUser, dispatch, meetings, users } = useNexus();
  const guests = users.filter((user) => user.id !== currentUser.id);
  const [form, setForm] = useState({
    title: "",
    guestId: guests[0]?.id ?? "",
    date: "2026-05-21",
    time: "11:00",
    duration: 30,
    mode: "Video",
    agenda: "",
  });

  const updateField = (event) => {
    setForm({ ...form, [event.target.name]: event.target.value });
  };

  const createMeeting = (event) => {
    event.preventDefault();
    dispatch({ type: "createMeeting", payload: form });
    setForm({ ...form, title: "", agenda: "" });
  };

  const getUserName = (id) => users.find((user) => user.id === id)?.name ?? "Nexus member";

  return (
    <div className="grid gap-6 p-4 sm:p-6 xl:grid-cols-[390px_1fr]">
      <section className="rounded-lg bg-white p-5 shadow-sm">
        <div className="flex items-center gap-3">
          <div className="grid h-10 w-10 place-items-center rounded-md bg-emerald-100 text-emerald-700">
            <CalendarPlus size={20} />
          </div>
          <div>
            <h1 className="text-xl font-bold text-slate-950">Schedule meeting</h1>
            <p className="text-sm text-slate-500">Create, accept, reject, and detect double booking.</p>
          </div>
        </div>

        <form onSubmit={createMeeting} className="mt-6 space-y-4">
          <input
            required
            name="title"
            value={form.title}
            onChange={updateField}
            placeholder="Meeting title"
            className="w-full rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500"
          />
          <select
            name="guestId"
            value={form.guestId}
            onChange={updateField}
            className="w-full rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500"
          >
            {guests.map((guest) => (
              <option key={guest.id} value={guest.id}>
                {guest.name} - {guest.role}
              </option>
            ))}
          </select>
          <div className="grid grid-cols-2 gap-3">
            <input name="date" value={form.date} onChange={updateField} type="date" className="rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500" />
            <input name="time" value={form.time} onChange={updateField} type="time" className="rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500" />
          </div>
          <div className="grid grid-cols-2 gap-3">
            <input name="duration" value={form.duration} onChange={updateField} type="number" min="15" step="15" className="rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500" />
            <select name="mode" value={form.mode} onChange={updateField} className="rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500">
              <option>Video</option>
              <option>In person</option>
              <option>Phone</option>
            </select>
          </div>
          <textarea
            required
            name="agenda"
            value={form.agenda}
            onChange={updateField}
            placeholder="Agenda"
            rows="4"
            className="w-full resize-none rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500"
          />
          <button className="w-full rounded-md bg-emerald-500 py-3 text-sm font-semibold text-slate-950 hover:bg-emerald-400">
            Create request
          </button>
        </form>
      </section>

      <section className="rounded-lg bg-white p-5 shadow-sm">
        <div className="mb-5 flex flex-col justify-between gap-2 sm:flex-row sm:items-center">
          <div>
            <h2 className="text-xl font-bold text-slate-950">Meeting pipeline</h2>
            <p className="text-sm text-slate-500">Calendar-like workflow for backend scheduling APIs.</p>
          </div>
          <span className="rounded-md bg-slate-100 px-3 py-2 text-sm font-medium text-slate-600">{meetings.length} meetings</span>
        </div>

        <div className="grid gap-4">
          {meetings.map((meeting) => (
            <article key={meeting.id} className="rounded-lg border border-slate-200 p-4">
              <div className="flex flex-col justify-between gap-4 lg:flex-row lg:items-start">
                <div>
                  <div className="flex flex-wrap items-center gap-2">
                    <h3 className="text-lg font-semibold text-slate-950">{meeting.title}</h3>
                    <span className={`rounded-full px-2.5 py-1 text-xs font-semibold ${statusClass[meeting.status]}`}>
                      {meeting.status}
                    </span>
                  </div>
                  <p className="mt-2 text-sm text-slate-600">{meeting.agenda}</p>
                  <div className="mt-3 flex flex-wrap gap-3 text-sm text-slate-500">
                    <span>{meeting.date}</span>
                    <span className="flex items-center gap-1">
                      <Clock size={15} />
                      {meeting.time} for {meeting.duration} min
                    </span>
                    <span>{meeting.mode}</span>
                    <span>{getUserName(meeting.hostId)} with {getUserName(meeting.guestId)}</span>
                  </div>
                </div>
                <div className="flex gap-2">
                  <button
                    onClick={() => dispatch({ type: "setMeetingStatus", id: meeting.id, status: "Accepted" })}
                    className="grid h-10 w-10 place-items-center rounded-md bg-emerald-100 text-emerald-700 hover:bg-emerald-200"
                    title="Accept"
                  >
                    <Check size={18} />
                  </button>
                  <button
                    onClick={() => dispatch({ type: "setMeetingStatus", id: meeting.id, status: "Rejected" })}
                    className="grid h-10 w-10 place-items-center rounded-md bg-rose-100 text-rose-700 hover:bg-rose-200"
                    title="Reject"
                  >
                    <X size={18} />
                  </button>
                </div>
              </div>
            </article>
          ))}
        </div>
      </section>
    </div>
  );
}

```

## client/src/pages/payments.jsx

```jsx
import { Check, CreditCard, ExternalLink, LockKeyhole, Rocket, ShieldCheck, WalletCards, X } from "lucide-react";
import { useMemo, useState } from "react";

import { useNexus } from "../context/NexusContext";

const statusClass = {
  Completed: "bg-emerald-100 text-emerald-700",
  Pending: "bg-amber-100 text-amber-700",
  Failed: "bg-rose-100 text-rose-700",
};

const outputItems = [
  "Authentication and profiles",
  "Meeting scheduling calendar",
  "Video calling",
  "Document chamber with e-signature",
  "Payment simulation",
  "Security features",
  "GitHub repository ready for frontend and backend",
  "Live deployment guide for Vercel and Render",
  "API documentation route and Postman collection",
  "Final demo presentation",
];

export default function Payments() {
  const { deployment, dispatch, security, transactions } = useNexus();
  const [form, setForm] = useState({
    type: "Deposit",
    party: "Northstar Ventures",
    amount: "10000",
    currency: "USD",
  });

  const totals = useMemo(() => {
    const completed = transactions.filter((item) => item.status === "Completed");
    return {
      volume: completed.reduce((sum, item) => sum + Number(item.amount), 0),
      pending: transactions.filter((item) => item.status === "Pending").length,
    };
  }, [transactions]);

  const updateField = (event) => {
    setForm({ ...form, [event.target.name]: event.target.value });
  };

  const createTransaction = (event) => {
    event.preventDefault();
    dispatch({ type: "createTransaction", payload: form });
  };

  return (
    <div className="space-y-6 p-4 sm:p-6">
      <section className="rounded-lg bg-white p-5 shadow-sm">
        <div className="flex flex-col justify-between gap-4 xl:flex-row xl:items-center">
          <div>
            <p className="text-sm font-medium text-emerald-700">Week 3 - Payments, Security and Deployment</p>
            <h1 className="mt-1 text-2xl font-bold text-slate-950">Mock payment flow with production-readiness controls</h1>
            <p className="mt-2 max-w-3xl text-sm text-slate-600">
              Covers sandbox payments, transaction history, validation, hashed-password backend support, mock 2FA, protected routes, deployment status, and API documentation.
            </p>
          </div>
          <div className="grid gap-3 sm:grid-cols-2">
            <div className="rounded-md border border-emerald-100 bg-emerald-50 px-4 py-3">
              <p className="text-xs font-medium uppercase text-emerald-700">Completed volume</p>
              <p className="mt-1 text-2xl font-bold text-emerald-800">${totals.volume.toLocaleString()}</p>
            </div>
            <div className="rounded-md border border-amber-100 bg-amber-50 px-4 py-3">
              <p className="text-xs font-medium uppercase text-amber-700">Pending payments</p>
              <p className="mt-1 text-2xl font-bold text-amber-800">{totals.pending}</p>
            </div>
          </div>
        </div>
      </section>

      <section className="grid gap-6 xl:grid-cols-[380px_1fr]">
        <div className="rounded-lg bg-white p-5 shadow-sm">
          <div className="flex items-center gap-3">
            <div className="grid h-10 w-10 place-items-center rounded-md bg-emerald-100 text-emerald-700">
              <CreditCard size={20} />
            </div>
            <div>
              <h2 className="text-lg font-semibold text-slate-950">Payment sandbox</h2>
              <p className="text-sm text-slate-500">Deposit, withdraw, or transfer funds.</p>
            </div>
          </div>

          <form onSubmit={createTransaction} className="mt-5 space-y-4">
            <select name="type" value={form.type} onChange={updateField} className="w-full rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500">
              <option>Deposit</option>
              <option>Withdraw</option>
              <option>Transfer</option>
            </select>
            <input name="party" value={form.party} onChange={updateField} placeholder="Investor or founder" className="w-full rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500" />
            <div className="grid grid-cols-[1fr_110px] gap-3">
              <input name="amount" value={form.amount} onChange={updateField} min="1" type="number" className="rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500" />
              <select name="currency" value={form.currency} onChange={updateField} className="rounded-md border border-slate-200 px-3 py-3 text-sm outline-none focus:border-emerald-500">
                <option>USD</option>
                <option>PKR</option>
                <option>EUR</option>
              </select>
            </div>
            <button className="inline-flex w-full items-center justify-center gap-2 rounded-md bg-emerald-500 px-4 py-3 text-sm font-semibold text-slate-950 hover:bg-emerald-400">
              <WalletCards size={18} />
              Create payment intent
            </button>
          </form>
        </div>

        <div className="rounded-lg bg-white p-5 shadow-sm">
          <div className="mb-4 flex flex-col justify-between gap-2 sm:flex-row sm:items-center">
            <h2 className="text-lg font-semibold text-slate-950">Transaction history</h2>
            <span className="rounded-md bg-slate-100 px-3 py-2 text-sm font-medium text-slate-600">{transactions.length} records</span>
          </div>
          <div className="overflow-x-auto">
            <table className="w-full min-w-[720px] text-left text-sm">
              <thead className="border-b border-slate-200 text-xs uppercase text-slate-500">
                <tr>
                  <th className="py-3">Type</th>
                  <th className="py-3">Party</th>
                  <th className="py-3">Amount</th>
                  <th className="py-3">Reference</th>
                  <th className="py-3">Status</th>
                  <th className="py-3">Actions</th>
                </tr>
              </thead>
              <tbody className="divide-y divide-slate-100">
                {transactions.map((transaction) => (
                  <tr key={transaction.id}>
                    <td className="py-3 font-medium text-slate-900">{transaction.type}</td>
                    <td className="py-3 text-slate-600">{transaction.party}</td>
                    <td className="py-3 text-slate-600">{transaction.currency} {Number(transaction.amount).toLocaleString()}</td>
                    <td className="py-3 text-slate-500">{transaction.reference}</td>
                    <td className="py-3">
                      <span className={`rounded-full px-2.5 py-1 text-xs font-semibold ${statusClass[transaction.status]}`}>
                        {transaction.status}
                      </span>
                    </td>
                    <td className="py-3">
                      <div className="flex gap-2">
                        <button onClick={() => dispatch({ type: "setTransactionStatus", id: transaction.id, status: "Completed" })} className="grid h-9 w-9 place-items-center rounded-md bg-emerald-100 text-emerald-700 hover:bg-emerald-200" title="Complete">
                          <Check size={16} />
                        </button>
                        <button onClick={() => dispatch({ type: "setTransactionStatus", id: transaction.id, status: "Failed" })} className="grid h-9 w-9 place-items-center rounded-md bg-rose-100 text-rose-700 hover:bg-rose-200" title="Fail">
                          <X size={16} />
                        </button>
                      </div>
                    </td>
                  </tr>
                ))}
              </tbody>
            </table>
          </div>
        </div>
      </section>

      <section className="grid gap-6 xl:grid-cols-3">
        <div className="rounded-lg bg-white p-5 shadow-sm">
          <div className="flex items-center gap-3">
            <LockKeyhole size={22} className="text-emerald-700" />
            <h2 className="text-lg font-semibold text-slate-950">Security enhancements</h2>
          </div>
          <div className="mt-5 space-y-3">
            {[
              ["passwordHashing", "Password hashing"],
              ["jwtTokens", "Secure JWT-style tokens"],
              ["twoFactorEnabled", "2FA mock"],
              ["roleProtectedRoutes", "Role protected routes"],
            ].map(([key, label]) => (
              <button key={key} onClick={() => dispatch({ type: "toggleSecurity", key })} className="flex w-full items-center justify-between rounded-md border border-slate-200 px-3 py-3 text-left text-sm hover:bg-slate-50">
                <span className="font-medium text-slate-700">{label}</span>
                <span className={`rounded-full px-2.5 py-1 text-xs font-semibold ${security[key] ? "bg-emerald-100 text-emerald-700" : "bg-slate-100 text-slate-500"}`}>
                  {security[key] ? "Enabled" : "Off"}
                </span>
              </button>
            ))}
          </div>
          <div className="mt-4 rounded-md bg-slate-50 px-3 py-3 text-sm text-slate-600">
            Current mock OTP: <span className="font-semibold text-slate-950">{security.lastOtp}</span>
          </div>
        </div>

        <div className="rounded-lg bg-white p-5 shadow-sm">
          <div className="flex items-center gap-3">
            <Rocket size={22} className="text-sky-700" />
            <h2 className="text-lg font-semibold text-slate-950">Final integration</h2>
          </div>
          <div className="mt-5 space-y-3 text-sm">
            {Object.entries(deployment).map(([key, value]) => (
              <div key={key} className="flex items-center justify-between rounded-md bg-slate-50 px-3 py-3">
                <span className="capitalize text-slate-500">{key}</span>
                <span className="font-semibold text-slate-900">{value}</span>
              </div>
            ))}
          </div>
          <a href="/api-docs" className="mt-4 inline-flex items-center gap-2 text-sm font-semibold text-emerald-700">
            API documentation outline <ExternalLink size={15} />
          </a>
        </div>

        <div className="rounded-lg bg-white p-5 shadow-sm">
          <div className="flex items-center gap-3">
            <ShieldCheck size={22} className="text-amber-700" />
            <h2 className="text-lg font-semibold text-slate-950">Final output checklist</h2>
          </div>
          <div className="mt-5 space-y-3">
            {outputItems.map((item) => (
              <div key={item} className="flex items-center gap-3 rounded-md border border-slate-200 px-3 py-3 text-sm text-slate-700">
                <Check size={16} className="text-emerald-600" />
                {item}
              </div>
            ))}
          </div>
        </div>
      </section>
    </div>
  );
}

```

## client/src/pages/presentation.jsx

```jsx
import { CheckCircle2, FileText, Globe2, Rocket, ShieldCheck, Video } from "lucide-react";

const slides = [
  {
    title: "Nexus Platform",
    subtitle: "Investor and entrepreneur collaboration workspace",
    points: ["Role-based profiles", "Meeting coordination", "Documents, video, payments, and security"],
  },
  {
    title: "Core Web App",
    subtitle: "Functional modules delivered",
    points: ["Authentication and profiles", "Meeting scheduling with conflict detection", "Document vault with e-signature metadata"],
  },
  {
    title: "Collaboration Tools",
    subtitle: "Client demo workflows",
    points: ["Video room controls and chat", "Document upload and signing", "Dashboard activity and status tracking"],
  },
  {
    title: "Week 3 Completion",
    subtitle: "Payments, security, and deployment",
    points: ["Payment sandbox and transaction history", "Hashed password backend and signed tokens", "Mock 2FA and protected profile updates"],
  },
  {
    title: "Delivery Package",
    subtitle: "Ready for client handoff",
    points: ["Frontend and backend repo structure", "Deployment guide and configs", "API docs plus Postman collection"],
  },
  {
    title: "Final Output",
    subtitle: "Expected intern deliverables",
    points: ["Functional web app", "GitHub repository package", "Live deployment plan, API documentation, and final demo"],
  },
];

const summary = [
  { label: "Frontend", value: "Vite React dashboard", icon: Globe2 },
  { label: "Backend", value: "Node HTTP API", icon: Rocket },
  { label: "Security", value: "Hashing, JWT-style tokens, 2FA", icon: ShieldCheck },
  { label: "Docs", value: "API, deploy, presentation", icon: FileText },
  { label: "Demo", value: "Working client flows", icon: Video },
];

export default function Presentation() {
  return (
    <div className="space-y-6 p-4 sm:p-6">
      <section className="rounded-lg bg-slate-950 p-6 text-white shadow-sm">
        <p className="text-sm font-semibold uppercase tracking-wide text-emerald-300">Final demo presentation</p>
        <h1 className="mt-2 text-3xl font-bold">Nexus Platform Client Handoff</h1>
        <p className="mt-3 max-w-3xl text-slate-300">
          A concise presentation view covering the final output expected from interns: functional app, repository package, deployment plan, API documentation, and demo narrative.
        </p>
      </section>

      <section className="grid gap-4 md:grid-cols-2 xl:grid-cols-5">
        {summary.map(({ label, value, icon: Icon }) => (
          <div key={label} className="rounded-lg bg-white p-4 shadow-sm">
            <Icon size={22} className="text-emerald-700" />
            <h2 className="mt-3 text-sm font-semibold uppercase text-slate-500">{label}</h2>
            <p className="mt-1 text-sm font-medium text-slate-950">{value}</p>
          </div>
        ))}
      </section>

      <section className="grid gap-6 xl:grid-cols-2">
        {slides.map((slide, index) => (
          <article key={slide.title} className="rounded-lg bg-white p-5 shadow-sm">
            <div className="flex items-start gap-4">
              <div className="grid h-10 w-10 shrink-0 place-items-center rounded-md bg-emerald-100 text-sm font-bold text-emerald-800">
                {index + 1}
              </div>
              <div>
                <p className="text-sm font-medium text-emerald-700">{slide.subtitle}</p>
                <h2 className="mt-1 text-xl font-bold text-slate-950">{slide.title}</h2>
                <div className="mt-4 space-y-3">
                  {slide.points.map((point) => (
                    <div key={point} className="flex items-center gap-2 text-sm text-slate-700">
                      <CheckCircle2 size={16} className="text-emerald-600" />
                      {point}
                    </div>
                  ))}
                </div>
              </div>
            </div>
          </article>
        ))}
      </section>
    </div>
  );
}

```

## client/src/pages/register.jsx

```jsx
import { useState } from "react";
import { Link, useNavigate } from "react-router-dom";

import { useNexus } from "../context/NexusContext";

export default function Register() {
  const navigate = useNavigate();
  const { dispatch } = useNexus();
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    password: "",
    role: "entrepreneur",
    company: "",
    location: "",
    interests: "",
  });

  const handleRegister = (event) => {
    event.preventDefault();
    dispatch({ type: "register", payload: formData });
    navigate("/");
  };

  const updateField = (event) => {
    setFormData({ ...formData, [event.target.name]: event.target.value });
  };

  return (
    <div className="min-h-screen bg-slate-950 px-4 py-10 text-white">
      <div className="mx-auto max-w-xl rounded-lg bg-white p-6 text-slate-950 shadow-xl">
        <h1 className="text-2xl font-bold">Create Nexus account</h1>
        <p className="mt-2 text-sm text-slate-600">Add a founder or investor profile for the collaboration workspace.</p>

        <form onSubmit={handleRegister} className="mt-6 grid gap-4 sm:grid-cols-2">
          <input name="name" required placeholder="Full name" className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500" onChange={updateField} />
          <input name="email" required type="email" placeholder="Email" className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500" onChange={updateField} />
          <input name="password" required type="password" placeholder="Password" className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500" onChange={updateField} />
          <select name="role" value={formData.role} className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500" onChange={updateField}>
            <option value="entrepreneur">Entrepreneur</option>
            <option value="investor">Investor</option>
          </select>
          <input name="company" required placeholder="Company" className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500" onChange={updateField} />
          <input name="location" required placeholder="Location" className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500" onChange={updateField} />
          <input name="interests" placeholder="Interests, comma separated" className="rounded-md border border-slate-200 px-3 py-3 outline-none focus:border-emerald-500 sm:col-span-2" onChange={updateField} />
          <button type="submit" className="rounded-md bg-emerald-500 py-3 font-semibold text-slate-950 hover:bg-emerald-400 sm:col-span-2">
            Create account
          </button>
        </form>

        <p className="mt-5 text-center text-sm text-slate-600">
          Already registered?{" "}
          <Link to="/login" className="font-semibold text-emerald-700">
            Sign in
          </Link>
        </p>
      </div>
    </div>
  );
}

```

## client/src/pages/videocall.jsx

```jsx
import { Mic, MicOff, MonitorUp, PhoneOff, Send, Video, VideoOff } from "lucide-react";
import { useState } from "react";

import { useNexus } from "../context/NexusContext";

export default function VideoCall() {
  const { currentUser, dispatch, room } = useNexus();
  const [message, setMessage] = useState("");

  const toggle = (key) => {
    dispatch({ type: "setRoom", payload: { [key]: !room[key] } });
  };

  const sendMessage = (event) => {
    event.preventDefault();
    if (!message.trim()) return;
    dispatch({ type: "sendMessage", author: currentUser.name.split(" ")[0], body: message.trim() });
    setMessage("");
  };

  return (
    <div className="grid gap-6 p-4 sm:p-6 xl:grid-cols-[1fr_360px]">
      <section className="rounded-lg bg-slate-950 p-4 text-white shadow-sm">
        <div className="flex flex-col justify-between gap-3 border-b border-slate-800 pb-4 sm:flex-row sm:items-center">
          <div>
            <p className="text-sm text-emerald-300">WebRTC signaling room</p>
            <h1 className="text-2xl font-bold">{room.name}</h1>
          </div>
          <button
            onClick={() => dispatch({ type: "setRoom", payload: { connected: !room.connected } })}
            className={`rounded-md px-4 py-2 text-sm font-semibold ${
              room.connected ? "bg-rose-500 text-white" : "bg-emerald-500 text-slate-950"
            }`}
          >
            {room.connected ? "Leave room" : "Join room"}
          </button>
        </div>

        <div className="mt-4 grid min-h-[420px] gap-4 lg:grid-cols-2">
          {room.participants.map((participant, index) => (
            <div key={participant} className="relative grid min-h-[220px] place-items-center rounded-lg bg-slate-900">
              <div className="grid h-24 w-24 place-items-center rounded-full bg-emerald-500 text-3xl font-bold text-slate-950">
                {participant.charAt(0)}
              </div>
              <div className="absolute bottom-3 left-3 rounded-md bg-black/50 px-3 py-2 text-sm">
                {participant}
              </div>
              {!room.cameraOn && index === 0 ? (
                <div className="absolute right-3 top-3 rounded-md bg-slate-950 px-2 py-1 text-xs text-slate-300">
                  Camera off
                </div>
              ) : null}
            </div>
          ))}
        </div>

        <div className="mt-4 flex flex-wrap items-center justify-center gap-3">
          <button
            onClick={() => toggle("micOn")}
            className="grid h-11 w-11 place-items-center rounded-md bg-slate-800 text-white hover:bg-slate-700"
            title="Toggle microphone"
          >
            {room.micOn ? <Mic size={19} /> : <MicOff size={19} />}
          </button>
          <button
            onClick={() => toggle("cameraOn")}
            className="grid h-11 w-11 place-items-center rounded-md bg-slate-800 text-white hover:bg-slate-700"
            title="Toggle camera"
          >
            {room.cameraOn ? <Video size={19} /> : <VideoOff size={19} />}
          </button>
          <button
            onClick={() => toggle("screenShare")}
            className={`grid h-11 w-11 place-items-center rounded-md ${
              room.screenShare ? "bg-emerald-500 text-slate-950" : "bg-slate-800 text-white hover:bg-slate-700"
            }`}
            title="Share screen"
          >
            <MonitorUp size={19} />
          </button>
          <button
            onClick={() => dispatch({ type: "setRoom", payload: { connected: false } })}
            className="grid h-11 w-11 place-items-center rounded-md bg-rose-500 text-white hover:bg-rose-400"
            title="End call"
          >
            <PhoneOff size={19} />
          </button>
        </div>
      </section>

      <aside className="grid gap-6">
        <section className="rounded-lg bg-white p-5 shadow-sm">
          <h2 className="text-lg font-semibold text-slate-950">Call status</h2>
          <div className="mt-4 grid gap-3 text-sm">
            <div className="flex justify-between rounded-md bg-slate-50 px-3 py-2">
              <span className="text-slate-500">Connection</span>
              <span className="font-semibold text-slate-900">{room.connected ? "Connected" : "Waiting"}</span>
            </div>
            <div className="flex justify-between rounded-md bg-slate-50 px-3 py-2">
              <span className="text-slate-500">Participants</span>
              <span className="font-semibold text-slate-900">{room.participants.length}</span>
            </div>
            <div className="flex justify-between rounded-md bg-slate-50 px-3 py-2">
              <span className="text-slate-500">Screen share</span>
              <span className="font-semibold text-slate-900">{room.screenShare ? "On" : "Off"}</span>
            </div>
          </div>
        </section>

        <section className="rounded-lg bg-white p-5 shadow-sm">
          <h2 className="text-lg font-semibold text-slate-950">Room chat</h2>
          <div className="mt-4 max-h-72 space-y-3 overflow-y-auto">
            {room.chat.map((chat) => (
              <div key={chat.id} className="rounded-md bg-slate-50 p-3 text-sm">
                <p className="font-semibold text-slate-900">{chat.author}</p>
                <p className="mt-1 text-slate-600">{chat.body}</p>
              </div>
            ))}
          </div>
          <form onSubmit={sendMessage} className="mt-4 flex gap-2">
            <input
              value={message}
              onChange={(event) => setMessage(event.target.value)}
              placeholder="Write message"
              className="min-w-0 flex-1 rounded-md border border-slate-200 px-3 py-2 text-sm outline-none focus:border-emerald-500"
            />
            <button className="grid h-10 w-10 place-items-center rounded-md bg-emerald-500 text-slate-950 hover:bg-emerald-400" title="Send">
              <Send size={17} />
            </button>
          </form>
        </section>
      </aside>
    </div>
  );
}

```

## docs/API_DOCUMENTATION.md

```md
# Nexus API Documentation

Base URL:

``\`text
http://localhost:5000
``\`

## Health

### GET `/api/health`

Returns backend health and security header status.

## Authentication

### POST `/api/auth/login`

Request:

``\`json
{
  "email": "ayesha@nexus.test",
  "password": "demo123"
}
``\`

Response:

``\`json
{
  "token": "signed-token",
  "user": {
    "id": "u1",
    "name": "Ayesha Khan",
    "role": "entrepreneur"
  }
}
``\`

Investor login may return a mock 2FA challenge:

``\`json
{
  "twoFactorRequired": true,
  "userId": "u2",
  "delivery": "email",
  "otp": "913428"
}
``\`

### POST `/api/auth/verify-2fa`

Request:

``\`json
{
  "userId": "u2",
  "otp": "913428"
}
``\`

### POST `/api/auth/register`

Creates a user profile with sanitized input and hashed password.

## Profiles

### GET `/api/profiles`

Returns public investor and entrepreneur profiles.

### PUT `/api/profiles/:id`

Protected route. Requires bearer token.

Request:

``\`json
{
  "company": "Updated Company",
  "bio": "Updated profile bio"
}
``\`

## Meetings

### GET `/api/meetings`

Returns all meetings.

### POST `/api/meetings`

Creates a meeting and marks conflicting times as `Conflict`.

Request:

``\`json
{
  "title": "Investor review",
  "hostId": "u1",
  "guestId": "u2",
  "date": "2026-05-21",
  "time": "11:00",
  "duration": 30,
  "mode": "Video",
  "agenda": "Discuss funding plan"
}
``\`

### PATCH `/api/meetings/:id`

Updates meeting status or details.

## Documents

### GET `/api/documents`

Returns uploaded document metadata.

### POST `/api/documents`

Creates document metadata with a mock cloud storage URL.

### PATCH `/api/documents/:id/sign`

Adds e-signature metadata.

Request:

``\`json
{
  "signature": "A. Khan"
}
``\`

## Video

### GET `/api/video/rooms/:name`

Returns room state, participants, and chat.

### POST `/api/video/rooms/:name/chat`

Adds a chat message.

## Payments

### GET `/api/payments/transactions`

Returns transaction history.

### POST `/api/payments/create-intent`

Creates a sandbox deposit, withdraw, or transfer transaction.

Request:

``\`json
{
  "type": "Deposit",
  "party": "Northstar Ventures",
  "amount": 10000,
  "currency": "USD"
}
``\`

### PATCH `/api/payments/transactions/:id`

Updates transaction status.

Request:

``\`json
{
  "status": "Completed"
}
``\`

```

## docs/DEMO_PRESENTATION.md

```md
# Nexus Platform Demo Presentation

## Slide 1: Project Overview

Nexus is a collaboration platform for investors and entrepreneurs.

Delivered modules:

- Authentication and profiles
- Meeting scheduling
- Video calling
- Document handling and e-signature
- Payment simulation
- Security and deployment readiness

## Slide 2: Dashboard and Profiles

Show:

- Role-aware dashboard
- Investor and entrepreneur profile data
- Editable profile center
- Recent activity feed

## Slide 3: Meeting Scheduling

Show:

- Create meeting request
- Accept or reject meetings
- Conflict detection for double booking
- Meeting pipeline table

## Slide 4: Document Chamber

Show:

- Upload document metadata
- Document vault
- Signature pad
- Signed document status

## Slide 5: Video Calling

Show:

- Join room
- Mic and camera toggles
- Screen-share status
- Room chat

## Slide 6: Payments

Show:

- Create payment intent
- Deposit, withdraw, transfer options
- Transaction history
- Completed, pending, failed statuses

## Slide 7: Security

Show:

- Sanitized backend request body
- Scrypt password hashing
- Signed JWT-style token
- Mock 2FA verification
- Role-protected profile update
- Security headers

## Slide 8: Deployment and Docs

Show:

- Vercel frontend deployment plan
- Render/Heroku/AWS backend deployment plan
- `/api-docs` app page
- `docs/API_DOCUMENTATION.md`
- `docs/Nexus.postman_collection.json`

## Slide 9: Final Output

Final deliverables:

- Functional web app
- GitHub repository structure
- Live deployment guide
- API documentation
- Final demo presentation

```

## docs/DEPLOYMENT.md

```md
# Deployment Guide

## Frontend: Vercel

1. Push this repository to GitHub.
2. Open Vercel and import the repository.
3. Set the root directory to `client`.
4. Use these settings:

``\`text
Build command: npm run build
Output directory: dist
Install command: npm install
``\`

5. Add environment variables if the frontend is connected to a deployed backend:

``\`text
VITE_API_URL=https://your-backend-url.example.com
``\`

## Backend: Render

1. Push this repository to GitHub.
2. Open Render and create a new Web Service.
3. Use this repository.
4. Set the root directory to `sever`.
5. Use these settings:

``\`text
Build command: npm install
Start command: npm start
``\`

6. Add environment variables:

``\`text
PORT=5000
JWT_SECRET=replace-with-a-long-secret
``\`

## Backend: Heroku

``\`bash
cd sever
heroku create nexus-platform-api
heroku config:set JWT_SECRET=replace-with-a-long-secret
git subtree push --prefix sever heroku main
``\`

## Backend: AWS

Recommended simple path:

- Package `sever/server.js` as a Node service.
- Deploy on Elastic Beanstalk, App Runner, or ECS.
- Set `PORT` and `JWT_SECRET`.
- Add a managed database when moving beyond demo data.

## Production Notes

- Replace in-memory backend data with MongoDB or PostgreSQL.
- Replace browser localStorage demo state with API calls.
- Replace mock payment intent with Stripe or PayPal sandbox SDK.
- Replace mock 2FA with email or authenticator provider.
- Add HTTPS-only cookies or Authorization headers depending on final auth strategy.

```

## docs/FINAL_DELIVERABLES.md

```md
# Final Deliverables

Deadline: 25 May, 2026

## 1. Functional Web App

All core features are present in the frontend:

- Authentication and profiles
- Meeting scheduling calendar workflow
- Video calling demo room
- Document chamber with e-signature metadata
- Payment simulation
- Security features

## 2. GitHub Repository

Repository package includes:

- `client/` - React frontend
- `sever/` - Node backend API
- `docs/` - API docs, deployment guide, final deliverables, Postman collection, and demo presentation
- `render.yaml` - backend deployment blueprint
- `client/vercel.json` - frontend deployment config

## 3. Live Deployment

Deployment guide is ready for:

- Frontend on Vercel
- Backend on Render, Heroku, or AWS

See `docs/DEPLOYMENT.md`.

## 4. API Documentation

API documentation is available in:

- App route: `/api-docs`
- Markdown: `docs/API_DOCUMENTATION.md`
- Backend route: `GET /api/docs`
- Postman collection: `docs/Nexus.postman_collection.json`

## 5. Final Demo Presentation

Presentation is available in:

- App route: `/presentation`
- Markdown: `docs/DEMO_PRESENTATION.md`

```

## docs/Nexus.postman_collection.json

```json
{
  "info": {
    "name": "Nexus Platform API",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "variable": [
    {
      "key": "baseUrl",
      "value": "http://localhost:5000"
    },
    {
      "key": "token",
      "value": ""
    }
  ],
  "item": [
    {
      "name": "Health",
      "request": {
        "method": "GET",
        "url": "{{baseUrl}}/api/health"
      }
    },
    {
      "name": "Login",
      "request": {
        "method": "POST",
        "header": [{ "key": "Content-Type", "value": "application/json" }],
        "body": {
          "mode": "raw",
          "raw": "{\"email\":\"ayesha@nexus.test\",\"password\":\"demo123\"}"
        },
        "url": "{{baseUrl}}/api/auth/login"
      }
    },
    {
      "name": "Verify 2FA",
      "request": {
        "method": "POST",
        "header": [{ "key": "Content-Type", "value": "application/json" }],
        "body": {
          "mode": "raw",
          "raw": "{\"userId\":\"u2\",\"otp\":\"913428\"}"
        },
        "url": "{{baseUrl}}/api/auth/verify-2fa"
      }
    },
    {
      "name": "Profiles",
      "request": {
        "method": "GET",
        "url": "{{baseUrl}}/api/profiles"
      }
    },
    {
      "name": "Create Meeting",
      "request": {
        "method": "POST",
        "header": [{ "key": "Content-Type", "value": "application/json" }],
        "body": {
          "mode": "raw",
          "raw": "{\"title\":\"Investor review\",\"hostId\":\"u1\",\"guestId\":\"u2\",\"date\":\"2026-05-21\",\"time\":\"11:00\",\"duration\":30,\"mode\":\"Video\",\"agenda\":\"Discuss funding plan\"}"
        },
        "url": "{{baseUrl}}/api/meetings"
      }
    },
    {
      "name": "Create Document",
      "request": {
        "method": "POST",
        "header": [{ "key": "Content-Type", "value": "application/json" }],
        "body": {
          "mode": "raw",
          "raw": "{\"title\":\"NDA Draft.docx\",\"ownerId\":\"u1\",\"type\":\"Legal\",\"size\":\"820 KB\"}"
        },
        "url": "{{baseUrl}}/api/documents"
      }
    },
    {
      "name": "Room State",
      "request": {
        "method": "GET",
        "url": "{{baseUrl}}/api/video/rooms/nexus-seed-room"
      }
    },
    {
      "name": "Transactions",
      "request": {
        "method": "GET",
        "url": "{{baseUrl}}/api/payments/transactions"
      }
    },
    {
      "name": "Create Payment Intent",
      "request": {
        "method": "POST",
        "header": [{ "key": "Content-Type", "value": "application/json" }],
        "body": {
          "mode": "raw",
          "raw": "{\"type\":\"Deposit\",\"party\":\"Northstar Ventures\",\"amount\":10000,\"currency\":\"USD\"}"
        },
        "url": "{{baseUrl}}/api/payments/create-intent"
      }
    },
    {
      "name": "API Docs",
      "request": {
        "method": "GET",
        "url": "{{baseUrl}}/api/docs"
      }
    }
  ]
}

```

## sever/.env.example

```
PORT=5000
JWT_SECRET=replace-with-a-long-secret

```

## sever/package.json

```json
{
  "name": "nexus-server",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "node server.js",
    "start": "node server.js"
  }
}

```

## sever/README.md

```md
# Nexus Server

Dependency-free Node API for the Nexus platform demo.

## Run

``\`bash
npm run dev
``\`

The server listens on `http://localhost:5000`.

## Main Routes

- `POST /api/auth/login`
- `POST /api/auth/register`
- `POST /api/auth/verify-2fa`
- `GET /api/docs`
- `GET /api/profiles`
- `PUT /api/profiles/:id`
- `GET /api/meetings`
- `POST /api/meetings`
- `PATCH /api/meetings/:id`
- `GET /api/documents`
- `POST /api/documents`
- `PATCH /api/documents/:id/sign`
- `GET /api/video/rooms/:name`
- `POST /api/video/rooms/:name/chat`
- `GET /api/payments/transactions`
- `POST /api/payments/create-intent`
- `PATCH /api/payments/transactions/:id`

Security implemented for the demo API:

- Input sanitization for request bodies
- Scrypt password hashing with per-user salt
- Signed JWT-style bearer tokens
- Mock 2FA verification flow
- Role-protected profile update route
- Basic security headers

```

## sever/server.js

```js
import http from "node:http";
import { createHmac, randomBytes, randomUUID, scryptSync, timingSafeEqual } from "node:crypto";

const PORT = process.env.PORT || 5000;
const TOKEN_SECRET = process.env.JWT_SECRET || "nexus-local-demo-secret";

function sanitize(value) {
  if (Array.isArray(value)) return value.map(sanitize);
  if (value && typeof value === "object") {
    return Object.fromEntries(Object.entries(value).map(([key, item]) => [key, sanitize(item)]));
  }
  return typeof value === "string" ? value.replace(/[<>]/g, "").trim() : value;
}

function hashPassword(password) {
  const salt = randomBytes(16).toString("hex");
  const hash = scryptSync(password, salt, 64).toString("hex");
  return `${salt}:${hash}`;
}

function verifyPassword(password, stored) {
  const [salt, hash] = stored.split(":");
  const candidate = scryptSync(password, salt, 64);
  return timingSafeEqual(Buffer.from(hash, "hex"), candidate);
}

function base64url(input) {
  return Buffer.from(JSON.stringify(input)).toString("base64url");
}

function sign(value) {
  return createHmac("sha256", TOKEN_SECRET).update(value).digest("base64url");
}

function createToken(user) {
  const header = base64url({ alg: "HS256", typ: "JWT" });
  const payload = base64url({ sub: user.id, role: user.role, exp: Date.now() + 1000 * 60 * 60 * 8 });
  return `${header}.${payload}.${sign(`${header}.${payload}`)}`;
}

function verifyToken(req) {
  const token = req.headers.authorization?.replace("Bearer ", "");
  if (!token) return null;
  const [header, payload, signature] = token.split(".");
  if (!header || !payload || !signature || sign(`${header}.${payload}`) !== signature) return null;
  const data = JSON.parse(Buffer.from(payload, "base64url").toString("utf8"));
  if (Date.now() > data.exp) return null;
  return db.users.find((user) => user.id === data.sub) ?? null;
}

function requireRole(req, res, roles = []) {
  const user = verifyToken(req);
  if (!user) {
    send(res, 401, { message: "Authorization token required" });
    return null;
  }
  if (roles.length && !roles.includes(user.role)) {
    send(res, 403, { message: "Role is not allowed for this route" });
    return null;
  }
  return user;
}

const db = {
  users: [
    {
      id: "u1",
      name: "Ayesha Khan",
      email: "ayesha@nexus.test",
      passwordHash: hashPassword("demo123"),
      role: "entrepreneur",
      twoFactorEnabled: false,
      otp: "428913",
      company: "Luma Health",
      bio: "Founder building AI-powered remote patient intake for clinics.",
      interests: ["HealthTech", "Seed", "AI"],
      investmentHistory: "Raised $220k pre-seed from angel investors.",
    },
    {
      id: "u2",
      name: "Daniel Reed",
      email: "daniel@nexus.test",
      passwordHash: hashPassword("demo123"),
      role: "investor",
      twoFactorEnabled: true,
      otp: "913428",
      company: "Northstar Ventures",
      bio: "Early-stage investor focused on B2B SaaS and developer tools.",
      interests: ["SaaS", "FinTech", "Climate"],
      investmentHistory: "18 seed deals, 4 follow-on rounds, 2 exits.",
    },
  ],
  meetings: [
    {
      id: "m1",
      title: "Seed pitch review",
      hostId: "u1",
      guestId: "u2",
      date: "2026-05-18",
      time: "10:00",
      duration: 45,
      status: "Accepted",
      mode: "Video",
      agenda: "Review deck, traction, and fundraising targets.",
    },
  ],
  documents: [
    {
      id: "d1",
      title: "Investor Pitch Deck.pdf",
      ownerId: "u1",
      type: "Pitch Deck",
      size: "3.2 MB",
      status: "Signed",
      signature: "A. Khan",
      storageUrl: "s3://nexus-demo/investor-pitch-deck.pdf",
    },
  ],
  transactions: [
    {
      id: "tx1",
      type: "Deposit",
      party: "Northstar Ventures",
      amount: 25000,
      currency: "USD",
      status: "Completed",
      createdAt: "2026-05-15",
      reference: "pi_seed_round_001",
    },
  ],
  rooms: {
    "nexus-seed-room": {
      connected: false,
      participants: ["Ayesha Khan", "Daniel Reed"],
      chat: [{ id: "c1", author: "Daniel", body: "Ready when you are." }],
    },
  },
};

function send(res, status, payload) {
  res.writeHead(status, {
    "Access-Control-Allow-Origin": "*",
    "Access-Control-Allow-Headers": "Content-Type, Authorization",
    "Access-Control-Allow-Methods": "GET, POST, PUT, PATCH, OPTIONS",
    "Content-Type": "application/json",
    "Referrer-Policy": "no-referrer",
    "X-Content-Type-Options": "nosniff",
    "X-Frame-Options": "DENY",
  });
  res.end(status === 204 ? "" : JSON.stringify(payload));
}

function parseBody(req) {
  return new Promise((resolve, reject) => {
    let body = "";
    req.on("data", (chunk) => {
      body += chunk;
      if (body.length > 1_000_000) {
        reject(new Error("Payload too large"));
        req.destroy();
      }
    });
    req.on("end", () => {
      try {
        resolve(sanitize(body ? JSON.parse(body) : {}));
      } catch {
        reject(new Error("Invalid JSON"));
      }
    });
  });
}

function publicUser(user) {
  const { passwordHash, otp, ...safeUser } = user;
  return safeUser;
}

function hasConflict(candidate) {
  const start = new Date(`${candidate.date}T${candidate.time}`).getTime();
  const end = start + Number(candidate.duration) * 60000;
  return db.meetings.some((meeting) => {
    if (meeting.status === "Rejected" || meeting.date !== candidate.date) return false;
    const meetingStart = new Date(`${meeting.date}T${meeting.time}`).getTime();
    const meetingEnd = meetingStart + Number(meeting.duration) * 60000;
    return start < meetingEnd && meetingStart < end;
  });
}

async function route(req, res) {
  const url = new URL(req.url, `http://${req.headers.host}`);

  if (req.method === "OPTIONS") return send(res, 204, {});

  if (req.method === "GET" && url.pathname === "/api/health") {
    return send(res, 200, { ok: true, service: "nexus-server", security: "headers-enabled" });
  }

  if (req.method === "GET" && url.pathname === "/api/docs") {
    return send(res, 200, {
      auth: ["POST /api/auth/login", "POST /api/auth/register", "POST /api/auth/verify-2fa"],
      profiles: ["GET /api/profiles", "PUT /api/profiles/:id"],
      meetings: ["GET /api/meetings", "POST /api/meetings", "PATCH /api/meetings/:id"],
      documents: ["GET /api/documents", "POST /api/documents", "PATCH /api/documents/:id/sign"],
      payments: ["GET /api/payments/transactions", "POST /api/payments/create-intent", "PATCH /api/payments/transactions/:id"],
      video: ["GET /api/video/rooms/:name", "POST /api/video/rooms/:name/chat"],
    });
  }

  if (req.method === "POST" && url.pathname === "/api/auth/login") {
    const body = await parseBody(req);
    const user = db.users.find((item) => item.email === body.email);
    if (!user || !verifyPassword(body.password ?? "", user.passwordHash)) {
      return send(res, 401, { message: "Invalid email or password" });
    }
    if (user.twoFactorEnabled) {
      return send(res, 202, { twoFactorRequired: true, userId: user.id, delivery: "email", otp: user.otp });
    }
    return send(res, 200, { token: createToken(user), user: publicUser(user) });
  }

  if (req.method === "POST" && url.pathname === "/api/auth/verify-2fa") {
    const body = await parseBody(req);
    const user = db.users.find((item) => item.id === body.userId);
    if (!user || user.otp !== body.otp) return send(res, 401, { message: "Invalid OTP" });
    return send(res, 200, { token: createToken(user), user: publicUser(user) });
  }

  if (req.method === "POST" && url.pathname === "/api/auth/register") {
    const body = await parseBody(req);
    if (!body.email || !body.password || !body.name) {
      return send(res, 400, { message: "name, email, and password are required" });
    }
    const user = {
      id: randomUUID(),
      role: body.role || "entrepreneur",
      company: body.company || "",
      bio: body.bio || "",
      interests: body.interests || [],
      investmentHistory: "",
      twoFactorEnabled: false,
      otp: String(Math.floor(100000 + Math.random() * 900000)),
      name: body.name,
      email: body.email,
      passwordHash: hashPassword(body.password),
    };
    db.users.push(user);
    return send(res, 201, { token: createToken(user), user: publicUser(user) });
  }

  if (req.method === "GET" && url.pathname === "/api/profiles") {
    return send(res, 200, db.users.map(publicUser));
  }

  if (req.method === "PUT" && url.pathname.startsWith("/api/profiles/")) {
    const authUser = requireRole(req, res, ["entrepreneur", "investor"]);
    if (!authUser) return;
    const id = url.pathname.split("/").pop();
    if (authUser.id !== id && authUser.role !== "investor") return send(res, 403, { message: "Cannot edit this profile" });
    const body = await parseBody(req);
    const index = db.users.findIndex((user) => user.id === id);
    if (index === -1) return send(res, 404, { message: "Profile not found" });
    db.users[index] = { ...db.users[index], ...body, id, passwordHash: db.users[index].passwordHash };
    return send(res, 200, publicUser(db.users[index]));
  }

  if (req.method === "GET" && url.pathname === "/api/meetings") return send(res, 200, db.meetings);

  if (req.method === "POST" && url.pathname === "/api/meetings") {
    const body = await parseBody(req);
    const meeting = { id: randomUUID(), status: hasConflict(body) ? "Conflict" : "Pending", mode: "Video", ...body };
    db.meetings.unshift(meeting);
    return send(res, 201, meeting);
  }

  if (req.method === "PATCH" && url.pathname.startsWith("/api/meetings/")) {
    const id = url.pathname.split("/").pop();
    const body = await parseBody(req);
    const meeting = db.meetings.find((item) => item.id === id);
    if (!meeting) return send(res, 404, { message: "Meeting not found" });
    Object.assign(meeting, body);
    return send(res, 200, meeting);
  }

  if (req.method === "GET" && url.pathname === "/api/documents") return send(res, 200, db.documents);

  if (req.method === "POST" && url.pathname === "/api/documents") {
    const body = await parseBody(req);
    const document = { id: randomUUID(), status: "Review", storageUrl: `s3://nexus-demo/${body.title || "document"}`, ...body };
    db.documents.unshift(document);
    return send(res, 201, document);
  }

  if (req.method === "PATCH" && url.pathname.match(/^\/api\/documents\/[^/]+\/sign$/)) {
    const id = url.pathname.split("/")[3];
    const body = await parseBody(req);
    const document = db.documents.find((item) => item.id === id);
    if (!document) return send(res, 404, { message: "Document not found" });
    document.status = "Signed";
    document.signature = body.signature;
    return send(res, 200, document);
  }

  if (req.method === "GET" && url.pathname.startsWith("/api/video/rooms/")) {
    const name = url.pathname.split("/").pop();
    return send(res, 200, db.rooms[name] ?? { connected: false, participants: [], chat: [] });
  }

  if (req.method === "POST" && url.pathname.match(/^\/api\/video\/rooms\/[^/]+\/chat$/)) {
    const name = url.pathname.split("/")[4];
    const body = await parseBody(req);
    db.rooms[name] ??= { connected: true, participants: [], chat: [] };
    const chat = { id: randomUUID(), author: body.author, body: body.body };
    db.rooms[name].chat.push(chat);
    return send(res, 201, chat);
  }

  if (req.method === "GET" && url.pathname === "/api/payments/transactions") {
    return send(res, 200, db.transactions);
  }

  if (req.method === "POST" && url.pathname === "/api/payments/create-intent") {
    const body = await parseBody(req);
    const amount = Number(body.amount);
    if (!amount || amount <= 0) return send(res, 400, { message: "Positive amount is required" });
    const transaction = {
      id: `tx_${randomUUID()}`,
      type: body.type || "Deposit",
      party: body.party || "Nexus member",
      amount,
      currency: body.currency || "USD",
      status: "Pending",
      createdAt: new Date().toISOString().slice(0, 10),
      reference: `pi_${randomUUID()}`,
    };
    db.transactions.unshift(transaction);
    return send(res, 201, transaction);
  }

  if (req.method === "PATCH" && url.pathname.startsWith("/api/payments/transactions/")) {
    const id = url.pathname.split("/").pop();
    const body = await parseBody(req);
    const transaction = db.transactions.find((item) => item.id === id);
    if (!transaction) return send(res, 404, { message: "Transaction not found" });
    transaction.status = body.status || transaction.status;
    return send(res, 200, transaction);
  }

  return send(res, 404, { message: "Route not found" });
}

const server = http.createServer((req, res) => {
  route(req, res).catch((error) => send(res, 500, { message: error.message }));
});

server.listen(PORT, () => {
  console.log(`Nexus API running on http://localhost:${PORT}`);
});

```

