<h1>📝 Medium Social App — Full Stack Clone</h1>

<p>
A full-stack <b>Medium.com clone</b> built using modern technologies:
React + TypeScript + Vite (Frontend), Cloudflare Workers (Backend),
Prisma ORM, and Neon PostgreSQL. This app allows users to publish posts,
read posts, authenticate, search, and manage content.
</p>

<hr>

<h2>📁 Project Structure Overview</h2>

<pre>
MEDIUM_SOCIAL-APP/
│── backend/
│   ├── .wrangler/                  # Cloudflare worker cache
│   ├── node_modules/
│   ├── prisma/
│   │     ├── migrations/
│   │     └── schema.prisma
│   ├── src/
│   │     ├── routes/
│   │     │      ├── post.ts
│   │     │      ├── user.ts
│   │     │      └── prisma.ts
│   │     └── index.ts
│   ├── .env
│   ├── .gitignore
│   ├── package.json
│   ├── package-lock.json
│   ├── tsconfig.json
│   └── README.md
│
│── common/
│   ├── index.ts
│   ├── validator.ts
│
│── frontend/
│   ├── node_modules/
│   ├── public/
│   ├── src/
│   │     ├── assets/
│   │     ├── components/
│   │     │      ├── Appbar.tsx
│   │     │      ├── Auth.tsx
│   │     │      ├── LabelledInput.tsx
│   │     │      ├── NoPostsFound.tsx
│   │     │      ├── PostCard.tsx
│   │     │      ├── PostCardSkeleton.tsx
│   │     │      ├── Postexp.tsx
│   │     │      ├── PostexpSkeleton.tsx
│   │     │      ├── Quote.tsx
│   │     │      └── SearchBar.tsx
│   │
│   │     ├── hooks/
│   │     │      ├── PostsFetch.ts
│   │     │      ├── useAuth.ts
│   │     │      └── usePost.ts
│   │
│   │     ├── pages/
│   │     │      ├── DashBoard.tsx
│   │     │      ├── Post.tsx
│   │     │      ├── Posts.tsx
│   │     │      ├── Publish.tsx
│   │     │      ├── Signin.tsx
│   │     │      └── Signup.tsx
│   │
│   │     ├── state/
│   │     │      └── searchState.ts
│   │
│   │     ├── App.tsx
│   │     ├── App.css
│   │     ├── index.css
│   │     ├── main.tsx
│   │     └── vite-env.d.ts
│   │
│   ├── .env
│   ├── .gitignore
│   ├── eslint.config.js
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── package.json
│   ├── package-lock.json
│   ├── tsconfig.app.json
│   ├── tsconfig.node.json
│   └── vite.config.ts
│
└── README.md
</pre>

<hr>

<h2>🚀 Tech Stack</h2>

<h3>Frontend</h3>
<ul>
<li>React + TypeScript</li>
<li>Vite</li>
<li>TailwindCSS</li>
<li>Axios for API</li>
<li>Custom Hooks (useAuth, usePost, PostsFetch)</li>
<li>Reusable Components + Skeleton Loaders</li>
</ul>

<h3>Backend</h3>
<ul>
<li>Cloudflare Workers (Serverless)</li>
<li>Hono.js routing</li>
<li>Prisma ORM</li>
<li>JWT Authentication</li>
<li>Zod Validation</li>
</ul>

<h3>Database</h3>
<ul>
<li>Neon Serverless PostgreSQL</li>
</ul>

<hr>

<h2>🔧 Environment Variables</h2>

<h3>Backend (.env)</h3>
<pre>
DATABASE_URL=postgresql://your-neon-url
JWT_SECRET=your-secret-key
</pre>

<h3>Frontend (.env)</h3>
<pre>
VITE_API_URL=https://your-cloudflare-worker.workers.dev
</pre>

<hr>

<h2>🛠️ Backend Setup</h2>

<ol>
<li><b>Install dependencies</b></li>
<pre>cd backend
npm install</pre>

<li><b>Generate Prisma Client</b></li>
<pre>npx prisma generate</pre>

<li><b>Run migrations</b></li>
<pre>npx prisma migrate deploy</pre>

<li><b>Start development server</b></li>
<pre>npx wrangler dev</pre>

<li><b>Deploy to Cloudflare</b></li>
<pre>npx wrangler deploy</pre>
</ol>

<hr>

<h2>🖥️ Frontend Setup</h2>

<ol>
<li><b>Install dependencies</b></li>
<pre>cd frontend
npm install</pre>

<li><b>Start dev server</b></li>
<pre>npm run dev</pre>

<li><b>Build for production</b></li>
<pre>npm run build</pre>
</ol>

<hr>

<h2>📡 API Routes Overview</h2>

<h3>🔐 User Routes (backend/src/routes/user.ts)</h3>
<pre>
POST /api/v1/signup      → Register user
POST /api/v1/login       → Login user
GET  /api/v1/me          → Get user info (requires token)
</pre>

<h3>📝 Post Routes (backend/src/routes/post.ts)</h3>
<pre>
POST   /api/v1/post              → Create post
PUT    /api/v1/post/:id          → Update post
DELETE /api/v1/post/:id          → Delete post
GET    /api/v1/post/:id          → Fetch single post
GET    /api/v1/posts             → Fetch all posts
</pre>

<hr>

<h2>📦 Key Frontend Components</h2>
<ul>
<li><b>Appbar.tsx</b> – Navbar + auth buttons</li>
<li><b>PostCard.tsx</b> – Shows a single article preview</li>
<li><b>Postexp.tsx</b> – Full post page</li>
<li><b>Publish.tsx</b> – Create new post</li>
<li><b>Auth.tsx</b> – Login / Signup UI</li>
<li><b>Hooks:</b> useAuth.ts, usePost.ts, PostsFetch.ts</li>
<li><b>Pages:</b> DashBoard, Posts, Post, Publish, Signin, Signup</li>
</ul>

<hr>

<h2>🧩 Common Folder</h2>

<p>
Shared types and validation using <b>Zod</b> live here.
</p>

<pre>
common/
│── index.ts         # Shared interfaces
└── validator.ts     # Input validation schema
</pre>

<hr>

<h2>📐 Prisma Schema (Database)</h2>

<pre>
model User {
  id        String   @id @default(uuid())
  email     String   @unique
  password  String
  name      String?
  posts     Post[]
}

model Post {
  id        String   @id @default(uuid())
  title     String
  content   String
  authorId  String
  author    User     @relation(fields: [authorId], references: [id])
  createdAt DateTime @default(now())
}
</pre>

<hr>

<h2>📷 Screenshots</h2>
<p>Below are the UI screenshots of the Medium Social App:</p>

<h3>📝 Posts Page</h3>
<img src="https://github.com/Abhishekkhanai07/Media-Clone-Website/blob/9fbbabfe3191b48818d503901c747405af26f9f3/media-Output/Post%20page.png" />

<br><br>

<h3>✍️ Create Post (Publish Page)</h3>
<img src="https://github.com/Abhishekkhanai07/Media-Clone-Website/blob/9fbbabfe3191b48818d503901c747405af26f9f3/media-Output/create%20post.png" />

<br><br>

<h3>👤 Signin Page</h3>
<img src="https://github.com/Abhishekkhanai07/Media-Clone-Website/blob/9fbbabfe3191b48818d503901c747405af26f9f3/media-Output/signin%20page.png" />

<br><br>


<hr>


<h2>👤 Author</h2>

<p>
<b>Abhishek Khanai</b><br>
Full Stack Developer<br>
GitHub: <a href="https://github.com/Abhishekkhanai07">Abhishekkhanai07</a>
</p>
