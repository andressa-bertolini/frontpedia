## Website Scaffolding

```
src/
│
├── assets/               # Static files like images, fonts and icons
│   ├── images/
│   ├── fonts/
│   └── icons/
│
├── components/           # Reusable components (buttons, inputs, cards, etc.)
│   ├── Button/
│   │   ├── Button.js
│   │   └── Button.css
│   ├── Card/
│   │   ├── Card.js
│   │   └── Card.css
│   └── ...               # Other components
│
├── layouts/              # General layouts (e.g. Navbar, Footer, Sidebar)
│   ├── Navbar.js
│   ├── Footer.js
│   └── Sidebar.js
│
├── pages/                # Main pages of the website
│   ├── Home/
│   │   ├── Home.js
│   │   └── Home.css
│   ├── About/
│   │   ├── About.js
│   │   └── About.css
│   └── ...               # Other pages
│
├── services/             # API communication functions and settings
│   ├── api.js
│   └── auth.js
│
├── hooks/                # Custom Hooks for Reusable Logic
│   ├── useAuth.js
│   └── useFetch.js
│
├── context/              # Context API for global state management
│   ├── AuthContext.js
│   └── ThemeContext.js
│
├── styles/               # Global Project Styles
│   ├── variables.css
│   └── global.css
│
├── utils/                # Auxiliary/utility functions
│   ├── formatDate.js
│   └── validateForm.js
│
├── App.js                # Main component of the application
├── index.js              # React Entry Point
└── routes/               # Application Route Settings
    └── AppRoutes.js
```