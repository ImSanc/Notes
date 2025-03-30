### For adding alerts rather than browser alerts 


##### How to install 
 - npm install react-toastify
 - This is for types for ts
 npm install --save-dev @types/react-toastify

##### How to use 
- Starting from React-Toastify v7, the toast.configure() method has been deprecated.Instead, you should utilize the ToastContainer component to configure your toasts

1. Import the ToastContainer Component:
    - Replace the toast.configure() call with the ToastContainer component in your main application file (e.g., App.tsx):


        import React from 'react';
        import { ToastContainer, toast } from 'react-toastify';
        import 'react-toastify/dist/ReactToastify.css';
        
        function App() {
        const notify = () => toast('Wow, so easy!');
        
        return (
        <div>
        <button onClick={notify}>Notify!</button>
        {/* Place ToastContainer once in your application tree */}
        <ToastContainer />
        </div>
        );
        }
        
        export default App;

By including <ToastContainer /> once in your component tree, typically near the root, you set up the necessary context for displaying toast notifications

2. Ensure TypeScript Compatibility:
   - install the type definitions for React-Toastify:

            npm install --save-dev @types/react-toastify


3. Configure TypeScript Compiler Options:

   - Some users have encountered type errors related to module imports. To address this, consider enabling the esModuleInterop and allowSyntheticDefaultImports options in your tsconfig.json:

           {
           "compilerOptions": {
           "esModuleInterop": true,
           "allowSyntheticDefaultImports": true,
           // other options...
           }
           }


##### Customize 


- Use Built-in Themes
  React-Toastify provides three built-in themes:

 - "light" (default)
 - "dark"
 - "colored"


- Fully Customize with CSS

 - If you want a completely custom look, you can override the default styles using CSS.

Step 1: Create a CSS File (e.g., toast.css)

        .custom-toast {
        background-color: #1e293b !important; /* Dark Blue */
        color: #f8fafc !important; /* Light Text */
        border-radius: 8px;
        font-size: 16px;
        }
        
        .custom-toast .Toastify__progress-bar {
        background: #facc15 !important; /* Yellow Progress Bar */
        }

Step 2: Import the CSS in Your Component

    import "./toast.css";
    
    toast.info("Custom Styled Toast!", { className: "custom-toast" });
