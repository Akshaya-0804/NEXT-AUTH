# 📝 NEXT - AUTH

A Next.js application implementing authentication using NextAuth.js. This project demonstrates how to set up and configure authentication providers, manage sessions, and protect routes in a Next.js environment.

---

## 📌 Project Overview

This project showcases the integration of NextAuth.js into a Next.js application, providing a seamless authentication experience using various providers like Google, GitHub, and custom credentials.

---

## 🚀 Tech Stack

- **Framework**: Next.js 13+
- **Auth**: NextAuth.js (JWT strategy)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Deployment**: Vercel (assumed)
- **Tools**: GitHub OAuth Provider

---

## 📁 Project Structure

```
├── public/ # Static assets
├── src/
│ ├── app/ # App directory (Next.js 13 routing)
│ │ ├── server/ # Server-side functions
│ │ ├── page.tsx # Root page
│ │ ├── layout.tsx # Layout wrapper
│ ├── components/ # Reusable UI components
│ │ ├── Navbar.tsx
│ │ └── UserCard.tsx
│ ├── context/ # Global auth context
│ │ └── AuthProvider.tsx
│ ├── styles/
│ │ └── globals.css # Tailwind base + custom styles
│ └── middleware.ts # Route protection
├── .env.local # Environment secrets
├── next.config.js # Next.js config
├── tailwind.config.js # Tailwind setup
├── package.json
└── README.md # Project documentation
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/NEXT-AUTH.git
cd next_blog
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Run the Development Server

```bash
npm run dev
```

### 4. Build for Production

```bash
npm run build
```

### 5. Start the Production Server

```bash
npm start
```

---

## Detailed Explanation

### 1. `options.ts` – NextAuth Configuration

- Purpose: Defines all authentication providers and session behavior.

- The authorize function validates credentials for the CredentialsProvider.

- Environment variables are used for GitHub OAuth secrets.


![oauth](/images/oauth.png)
---

### 2. `route.ts` – NextAuth API Route

- Exports NextAuth handler for GET and POST requests.

- Connects the NextAuth framework to the options defined.

---

### 3. `client/page.tsx`– Client-Side Authenticated Page

- Uses the `useSession` hook from NextAuth client to get session data.

- `required: true` forces authentication; redirects unauthenticated users to sign-in.

- Displays the logged-in user's info using the `UserCard` component.

![client](/images/client.png)

---

### 4. `components/Navbar.tsx` – Navigation Bar

- Simple navbar with links to main pages and auth endpoints.

- Uses Next.js `Link` for client-side navigation.

---

### 5. `components/UserCard.tsx` – User Info Display

- Displays a greeting and profile image if available.

- The `pagetype` prop allows customizing the message based on page context.

![signin](/images/signin.png)

![signout](/images/signout.png)

---

### 6. `context/AuthProvider.tsx` – Session Provider Wrapper

- Wraps the app to provide session context via NextAuth's `SessionProvider`.

- Enables client components to use `useSession`.

---

### 7. `extra/page.tsx` – Static Extra Page

- Simple page without authentication.

- Shows usage of async server components in Next.js 13.

![extra](/images/extra.png)

---

### 8. `server/page.tsx` – Server-Side Authenticated Page

- Uses `getServerSession` (server-side) to check for a valid session.

- Redirects unauthenticated users to the sign-in page.

- Displays user info on successful authentication.

![server](/images/server.png)

---

### 9.  `layout.tsx` – Root Layout with Global Styling & Context

- Applies global fonts and CSS.

- Wraps the app with  `AuthProvider` and displays the  `Navbar`.

- Defines page metadata.

---

### 10. `page.tsx` – Homepage with Conditional Rendering

- Server-rendered home page.

- Shows user info if authenticated, else a restricted access message.

![Home](/images/Home.png)

---

### 11. `middleware.ts` – NextAuth Middleware for Route Protection

- Adds NextAuth middleware to protect `/extra` and `/dashboard` routes.

- Automatically redirects unauthorized users to the sign-in page.

---

### 12. `globals.css` – Tailwind and Custom CSS

- Tailwind CSS setup with dark mode color scheme support.

- Defines CSS variables for foreground and background colors.

---

## Environment Variables Required

- `GITHUB_ID` – GitHub OAuth Client ID

- `GITHUB_SECRET` – GitHub OAuth Client Secret

Make sure to set these in your `.env.local` file before running the app.

---

## 📚 My Understanding of NextAuth.js

Through this project, I’ve gained the following key takeaways:

**1. Session Management:** JWT-based session strategy eliminates the need for a backend DB to persist sessions, simplifying architecture.

**2. OAuth Flow:** I understand how GitHub OAuth is configured using client ID/secret and integrated into the app via NextAuth.

**3. Dynamic UI:** The UI (sign in/out buttons) updates reactively based on useSession().

**4. Route Protection:** Both middleware.ts and getServerSession() provide two layers of protection for authenticated-only pages.

**5. Global Context:** Wrapping the app with <SessionProvider /> ensures consistent auth state across pages.

---

## 📎 Resources

- NextAuth.js Docs

- GitHub OAuth App Setup

- Next.js Middleware

- TailwindCSS

---

## 🧑‍💻 Author
Akshaya – Built with ❤️ using Next.js + NextAuth
