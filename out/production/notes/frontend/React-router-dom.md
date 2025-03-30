# React router dom

## Routing can be done in two ways :

#### Component-Based Routing

         return (
       <BrowserRouter>
        <Routes>
          <Route path="/signup" element={<Signup />} />
          <Route path="/signin" element={<Signin />} />
          <Route path="/blog/:id" element={<Blog />} />
        </Routes>
        </BrowserRouter>
        );

- Pros:
  ✅ Simple and familiar for most React developers
  ✅ Easier to read and maintain for small apps
  ✅ Works well with React Router's built-in features
- Cons:
  ❌ Can get messy in larger apps
  ❌ Difficult to organize layouts and nested routes

#### Large project routing using Component based routing

- 1️⃣ Organize Routes Using RouteObject
Instead of cluttering App.tsx, routes are defined in a separate routes.tsx file.

        // 📂 src/routes.tsx
        import { RouteObject } from "react-router-dom";
        import Home from "./pages/Home";
        import Signup from "./pages/Signup";
        import Signin from "./pages/Signin";
        import Blog from "./pages/Blog";
        import DashboardLayout from "./pages/dashboard/Layout";
        import Profile from "./pages/dashboard/Profile";
        import Settings from "./pages/dashboard/Settings";
        
        const routes: RouteObject[] = [
        { path: "/", element: <Home /> },
        { path: "/signup", element: <Signup /> },
        { path: "/signin", element: <Signin /> },
        { path: "/blog/:id", element: <Blog /> },
        {
        path: "/dashboard",
        element: <DashboardLayout />, // Layout wraps child routes
        children: [
        { path: "profile", element: <Profile /> },
        { path: "settings", element: <Settings /> },
        ],
        },
        ];
        
        export default routes;


- 2️⃣ Use useRoutes() for Rendering the Routes
  Instead of manually adding <Routes> and <Route> in App.tsx, we use useRoutes(routes).

        // 📂 src/App.tsx
        import { BrowserRouter, useRoutes } from "react-router-dom";
        import routes from "./routes";
        
        function AppRoutes() {
        return useRoutes(routes); // Loads routes dynamically
        }
        
        function App() {
        return (
        <BrowserRouter>
        <AppRoutes />
        </BrowserRouter>
        );
        }
        
        export default App;


🚀 Why Was This Used in Large Projects?
✅ Keeps routes modular & separate from UI components
✅ Easy to scale—just add new route objects
✅ Supports layouts & nested routes
✅ Uses built-in React Router features (No extra dependencies like @react-router/dev)


🔄 JSX vs. @react-router/dev — Which One Should You Use?
Feature	     || JSX-Based (useRoutes)	                       || @react-router/dev
Ease of Use	 || ✅ Simple for JSX users	                       || 🔸 Requires learning config-based routing
Scalability  ||	✅ Modular & maintainable	                   || ✅ Even more structured for large apps
Stability    || ✅ Stable, industry standard	               || 🔸 Experimental, may change
Performance  || ✅ Uses built-in React Router features	       || ✅ Potentially optimized for large apps
Adoption	 || ✅ Widely used	                               || ❌ Not widely adopted yet

### New way of doing routing

#### Configuration-Based Routing (React Router Dev) 

    import { route, layout, index, prefix } from "@react-router/dev/routes";
        export default [
        route("signup", "./Signup.tsx"),
        route("signin", "./Signin.tsx"),
        route("blog/:id", "./Blog.tsx"),
        ];


- Pros:
  ✅ Keeps routing logic separate from UI components
  ✅ Easier to scale with large applications
  ✅ Built-in support for layouts and prefixes
- Cons:
  ❌ Not yet widely adopted
  ❌ More abstract, which may not be intuitive for beginners



### how do we use Configuration based routing

-   1️⃣ Create a routes.ts File
    This file defines your app's routes using the @react-router/dev/routes package.

        // routes.ts
        import { type RouteConfig, route, index, layout } from "@react-router/dev/routes";
        
        export default [
        index("./pages/Home.tsx"), // `/`
        route("signup", "./pages/Signup.tsx"), // `/signup`
        route("signin", "./pages/Signin.tsx"), // `/signin`
        route("blog/:id", "./pages/Blog.tsx"), // `/blog/:id`
        
        // Example of a layout with nested routes
        layout("./pages/dashboard/Layout.tsx", [
        route("profile", "./pages/dashboard/Profile.tsx"),
        route("settings", "./pages/dashboard/Settings.tsx"),
        ]),
        ] satisfies RouteConfig;


- 2️⃣ Use It in Your Main Router File (App.tsx)
React Router v7 has an API to load these routes dynamically

        // App.tsx
        import { BrowserRouter } from "react-router-dom";
        import { createRouter } from "@react-router/dev";
        import routes from "./routes";
        
        const Router = createRouter(routes);
        
        function App() {
        return (
        <BrowserRouter>
        <Router />
        </BrowserRouter>
        );
        }
        
        export default App;

Benefits of This Approach
✅ Keeps route definitions separate from UI components
✅ Supports layouts and nested routes easily
✅ Simplifies large-scale applications


#### For large application we should have Structure for routing

        /src
        │── /routes
        │   │── index.ts           # Main router entry point
        │   │── auth.ts            # Authentication-related routes
        │   │── dashboard.ts       # Dashboard-related routes
        │   │── blog.ts            # Blog-related routes
        │
        │── /pages
        │   │── Home.tsx
        │   │── Signup.tsx
        │   │── Signin.tsx
        │   │── Blog.tsx
        │   │── /dashboard
        │   │   │── Layout.tsx
        │   │   │── Profile.tsx
        │   │   │── Settings.tsx
        │
        │── App.tsx

- 1️⃣ Define Sub-Routes in Separate Files
  - 🔹 routes/auth.ts (Authentication Routes)

          import { route } from "@react-router/dev/routes";
        
          export default [
          route("signup", "../pages/Signup.tsx"),
          route("signin", "../pages/Signin.tsx"),
          ];
  
  -🔹 routes/blog.ts (Blog Routes)

        import { route } from "@react-router/dev/routes";
        
        export default [
        route("blog/:id", "../pages/Blog.tsx"),
        ];

  - 🔹 routes/dashboard.ts (Dashboard Routes)
        
        import { layout, route } from "@react-router/dev/routes";
        
        export default [
        layout("../pages/dashboard/Layout.tsx", [
        route("profile", "../pages/dashboard/Profile.tsx"),
        route("settings", "../pages/dashboard/Settings.tsx"),
        ]),
        ];
  
    - 2️⃣ Combine All Routes in routes/index.ts


        import { type RouteConfig, index } from "@react-router/dev/routes";
        import authRoutes from "./auth";
        import blogRoutes from "./blog";
        import dashboardRoutes from "./dashboard";
    
        export default [
        index("../pages/Home.tsx"), // Root "/"
        ...authRoutes, // Spread auth routes
        ...blogRoutes, // Spread blog routes
        ...dashboardRoutes, // Spread dashboard routes
        ] satisfies RouteConfig;


- 3️⃣ Use Routes in App.tsx

        import { BrowserRouter } from "react-router-dom";
        import { createRouter } from "@react-router/dev";
        import routes from "./routes";
        
        const Router = createRouter(routes);
        
        function App() {
        return (
        <BrowserRouter>
        <Router />
        </BrowserRouter>
        );
        }
        
        export default App;


🚀 Why Is This Better?
✅ Modular & Maintainable – Easier to manage and scale.
✅ Separation of Concerns – Keeps routes clean and categorized.
✅ Better Readability – Helps developers find routes quickly.