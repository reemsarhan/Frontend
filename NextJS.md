# Next.js 

##  What is Next.js? 
Next.js is a React framework that provides server-side rendering (SSR), static site generation (SSG), API routes, and automatic code splitting to build fast and scalable web applications.

### Key Features of Next.js:
- Hybrid Rendering (SSG & SSR)
- File-based Routing
- API Routes
- Image Optimization
- Automatic Code Splitting

```jsx
export default function Home() {
  return <h1>Welcome to Next.js!</h1>;
}
```
## How is Next.js different from React?

| Feature           | Next.js                             | React                       |
|-------------------|-------------------------------------|-----------------------------|
| **Rendering**      | SSR, SSG, ISR, CSR                 | CSR (Client-side Rendering) |
| **Routing**        | File-based routing (pages/)        | React Router (manual setup) |
| **SEO**            | Built-in support                   | Requires third-party libraries |
| **API Handling**   | API Routes                         | Requires Express or external APIs |

## What are the different rendering methods in Next.js?

Next.js supports multiple rendering strategies:

- Static Site Generation (SSG) (getStaticProps)
- Server-Side Rendering (SSR) (getServerSideProps)
- Incremental Static Regeneration (ISR)
- Client-Side Rendering (CSR)

## What is File-based Routing in Next.js?
Next.js automatically creates routes based on the pages/ directory structure.
### Example of Routing in Next.js
```
/pages/index.js      ->  "/"
/pages/about.js      ->  "/about"
/pages/blog/[id].js  ->  "/blog/:id"
```
Dynamic Route (pages/blog/[id].js)
```
import { useRouter } from "next/router";

export default function BlogPost() {
  const router = useRouter();
  return <h1>Post ID: {router.query.id}</h1>;
}
```
## How do API routes work in Next.js?
Next.js allows you to create serverless API routes inside the pages/api/ directory.
### Example (pages/api/hello.js)
```
export default function handler(req, res) {
  res.status(200).json({ message: "Hello from API!" });
}
```
#### Access API Route: http://localhost:3000/api/hello

## What is Image Optimization in Next.js?
Next.js provides an optimized <Image /> component that automatically lazy-loads images, resizes them, and serves them in modern formats.
```
import Image from "next/image";

export default function Profile() {
  return <Image src="/profile.jpg" width={150} height={150} alt="Profile" />;
}
```
## Why use next/image instead of <img>?
Optimized loading
Automatic resizing
WebP format support

## How does Next.js handle CSS? 
Next.js supports multiple CSS solutions:
Global CSS (styles/global.css)
CSS Modules (Component.module.css)
Styled Components
Tailwind CSS

✅ Example of CSS Module:
```
/* styles/Home.module.css */
.title {
  color: blue;
  font-size: 24px;
}
```
```
import styles from "../styles/Home.module.css";

export default function Home() {
  return <h1 className={styles.title}>Hello, Next.js!</h1>;
}
```
## What is Middleware in Next.js? 
Middleware allows you to execute code before a request is completed, useful for authentication, redirects, and custom headers.
Example (middleware.ts or middleware.js):
```
import { NextResponse } from "next/server";

export function middleware(req) {
  if (!req.cookies.authToken) {
    return NextResponse.redirect("/login");
  }
  return NextResponse.next();
}
```
📌 Middleware is applied to all routes in Next.js 12+.

## What is Incremental Static Regeneration (ISR)? 
ISR allows static pages to be updated without rebuilding the entire site.
```
export async function getStaticProps() {
  return {
    props: { timestamp: new Date().toISOString() },
    revalidate: 10, // Page updates every 10 seconds
  };
}
```
## What are some performance optimizations in Next.js?
Best Practices to Improve Next.js Performance:
Use Static Site Generation (SSG) when possible
Enable Incremental Static Regeneration (ISR)
Use <Image /> for optimized images
Lazy load components with next/dynamic
Enable API caching
Minimize third-party scripts
Use Middleware for authentication and redirects

### Example of Lazy Loading Components:
```
import dynamic from "next/dynamic";

const HeavyComponent = dynamic(() => import("../components/HeavyComponent"), { ssr: false });

export default function Home() {
  return <HeavyComponent />;
}
``` 
## What is next.config.js used for?
Custom Webpack configuration
Setting environment variables
Enabling experimental features

## How do you handle authentication in Next.js?
Use NextAuth.js for OAuth, JWT, and session-based auth.
Protect routes with middleware.

✅ Example: Protecting a Page
```
import { useSession } from "next-auth/react";

export default function Dashboard() {
  const { data: session } = useSession();
  if (!session) return <p>Please login</p>;
  return <h1>Welcome, {session.user.name}</h1>;
}
```
 
