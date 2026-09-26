# MentorPass 🧑‍🏫

A mentorship-booking platform landing page and mock dashboard, built with **React**, **Vite**, **React Router**, **Tailwind CSS**, and **Framer Motion**. MentorPass connects users with mentors through a marketing homepage, a mock sign-up/login flow, and a simple post-login dashboard.

---

## ✨ Features

- **Landing page** with animated hero section, featured mentors grid, "How It Works" steps, pricing plans, testimonials, an animated FAQ accordion, and a footer with a contact form
- **Sign up / Login flow** with client-side email validation (credentials are stored in the browser's `localStorage` — see [Known Limitations](#-known-limitations))
- **Protected checkout/dashboard page** — redirects to `/login` automatically if no user is logged in
- **Dashboard sections**: welcome banner, account info, upcoming session, subscription plan, settings, favorite mentors list, and a logout button
- **Smooth animations** throughout via Framer Motion (hero text, FAQ accordion, testimonial cards)
- **Responsive navigation** with a mobile hamburger menu

## 🛠 Tech Stack

- [React 18](https://react.dev/) — UI library
- [Vite](https://vitejs.dev/) — dev server & build tool
- [React Router v7](https://reactrouter.com/) — client-side routing
- [Tailwind CSS](https://tailwindcss.com/) — utility-first styling
- [Framer Motion](https://www.framer.com/motion/) — animations
- [react-icons](https://react-icons.github.io/react-icons/) — icon set (Font Awesome icons)

## 🗺 Routes

| Path | Page | Notes |
|---|---|---|
| `/` | `HomePage` | Public landing page |
| `/login` | `Login` | Redirects to `/checkout` on success |
| `/signup` | `SignUp` | Saves credentials, redirects to `/checkout` |
| `/checkout` | `CheckoutPage` | Protected — redirects to `/login` if no user is stored |

## 📁 Project Structure

```
mentorpass/
├── public/
│   └── vite.svg
├── src/
│   ├── assets/
│   │   └── hero.png
│   ├── components/
│   │   ├── Header.jsx            # Top nav with mobile menu
│   │   ├── HeroSection.jsx       # Animated landing hero
│   │   ├── FeaturedMentors.jsx   # Mentor cards (static sample data)
│   │   ├── HowItWorks.jsx        # 3-step explainer
│   │   ├── PricingPlans.jsx      # Lite / Standard / Premium plans
│   │   ├── Testimonials.jsx      # Animated testimonial cards
│   │   ├── FAQs.jsx              # Animated accordion
│   │   ├── Footer.jsx            # Footer + contact form
│   │   ├── WelcomeSection.jsx    # Dashboard greeting
│   │   ├── AccountInfo.jsx       # Dashboard account details
│   │   ├── UpcomingSession.jsx   # Dashboard session info
│   │   ├── SubscriptionPlan.jsx  # Dashboard subscription info
│   │   ├── Settings.jsx          # Dashboard settings buttons
│   │   ├── MentorsList.jsx       # Dashboard favorite mentors list
│   │   └── LogoutButton.jsx      # Clears session, redirects home
│   ├── pages/
│   │   ├── HomePage.jsx          # Assembles all landing sections
│   │   ├── Login.jsx             # Login form + validation
│   │   ├── SignUp.jsx            # Sign-up form + validation
│   │   └── CheckoutPage.jsx      # Protected dashboard page
│   ├── App.jsx                    # Route definitions
│   ├── main.jsx                    # React app entry point
│   └── index.css                    # Tailwind directives
└── index.html
```

## ⚠️ Known Limitations

Since this is a front-end demo/course project, a few things are worth knowing before treating it as production-ready:

- **No real backend or database** — "authentication" simply reads/writes a single user object to `localStorage`. Signing up overwrites any previously stored account, and only one user can be "logged in" on a given browser at a time.
- **Passwords are stored in plain text** in `localStorage` — never use real credentials with this app as-is.
- **Sample data is hardcoded** — mentors, testimonials, and the "Favorite Mentors" list on the dashboard use static placeholder data rather than an API. `MentorsList` is also passed an empty array (`mentors={[]}`) from `CheckoutPage`, so it will always render empty.
- **Some referenced images aren't included in the repo** — components reference `/mentor1.jpg`, `/mentor2.jpg`, `/mentor3.jpg`, `/person1.jpg`, `/person2.jpg`, and `/person3.jpg`, but only `hero.png` exists in `src/assets/`. Add these files to `public/` (matching those exact names) or update the paths to fix the broken images.

## 🚨 Important Setup Note

This repo's `.gitignore` currently excludes `package.json`, `vite.config.js`, `tailwind.config.js`, and `postcss.config.js` — which means **these files are not in version control** and won't be present after a fresh clone. Before running the project, you'll need to remove those four lines from `.gitignore` and add the config files back. Standard versions for this stack look like:

**`package.json`** (dependencies inferred from `package-lock.json`):
```json
{
  "name": "mentorpass",
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
    "framer-motion": "^11.17.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-icons": "^5.4.0",
    "react-router-dom": "^7.1.1"
  },
  "devDependencies": {
    "@eslint/js": "^9.17.0",
    "@types/react": "^18.3.18",
    "@types/react-dom": "^18.3.5",
    "@vitejs/plugin-react": "^4.3.4",
    "autoprefixer": "^10.4.20",
    "eslint": "^9.17.0",
    "eslint-plugin-react": "^7.37.2",
    "eslint-plugin-react-hooks": "^5.0.0",
    "eslint-plugin-react-refresh": "^0.4.16",
    "globals": "^15.14.0",
    "postcss": "^8.4.49",
    "tailwindcss": "^3.4.17",
    "vite": "^6.0.5"
  }
}
```

**`vite.config.js`**:
```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
```

**`tailwind.config.js`**:
```js
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: { extend: {} },
  plugins: [],
};
```

**`postcss.config.js`**:
```js
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

> These were reconstructed from the dependency versions pinned in `package-lock.json` — double-check them against your local working copy before committing, in case your original configs had extra customization.

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or later recommended)
- npm

### Installation

```bash
# Clone the repository
git clone https://github.com/A-R-Adnan/Mentor_Pass.git

# Move into the project folder
cd Mentor_Pass/mentorpass

# Install dependencies (after restoring package.json — see note above)
npm install
```

### Running Locally

```bash
npm run dev
```

The app will be available at `http://localhost:5173` (default Vite port).

### Building for Production

```bash
npm run build
```

### Preview the Production Build

```bash
npm run preview
```

## 🔭 Future Improvements

- Replace the `localStorage`-based auth with a real backend (e.g., Firebase Auth or a Node/Express API) and support multiple users
- Hash/never store plaintext passwords
- Fetch mentors and testimonials from an API instead of hardcoded arrays
- Pass real data into `MentorsList` on the dashboard instead of an empty array
- Add the missing mentor/testimonial images or swap them for a placeholder image service
- Add form-level loading and error states for Login/SignUp instead of `alert()` calls
- Add tests (e.g., Vitest + React Testing Library) for routing and form validation logic

## 👤 Author

**A-R-Adnan**
[GitHub](https://github.com/A-R-Adnan)
