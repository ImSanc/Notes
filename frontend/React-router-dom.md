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
