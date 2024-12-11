# React + TypeScript + Vite + Supabase

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) + [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

## Project Setup

### Prerequisites
- Node.js (version 18.0 or higher)
- npm or Yarn
- A GitHub account

### Setting up Supabase

#### 1. Create a Supabase Account

1. Visit [Supabase](https://supabase.com/) and click "Start Your Project"
2. Sign up using GitHub, Google, or email
3. Verify your email address

#### 2. Create a New Supabase Project

1. Log in to the [Supabase Dashboard](https://supabase.com/dashboard)
2. Click "New Project"
3. Choose a unique project name
4. Set up your database password
5. Select your region

#### 3. Locate Project Credentials

1. Go to Project Settings (gear icon)
2. Navigate to the "API" section

##### Find SUPABASE_URL
- Look for the "Project URL"
- It looks like: `https://your-project-id.supabase.co`

##### Find SUPABASE_ANON_KEY
- Find the "anon (public)" key under "Project API Keys"

#### 4. Configure Environment Variables

Create a `.env` file in your project root:
```
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

**Note:** Prefix Vite environment variables with `VITE_`

## Expanding the ESLint Configuration

### Type-Aware Lint Rules

For production applications, update ESLint configuration:

1. Configure `parserOptions`:
```js
export default tseslint.config({
  languageOptions: {
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

2. Update ESLint configs:
- Replace `tseslint.configs.recommended` with `tseslint.configs.recommendedTypeChecked`
- Optionally add `...tseslint.configs.stylisticTypeChecked`

### React Plugin Configuration

Install eslint-plugin-react:
```bash
npm install -D eslint-plugin-react
```

Update `eslint.config.js`:
```js
import react from 'eslint-plugin-react'
export default tseslint.config({
  settings: { 
    react: { version: '18.3' } 
  },
  plugins: {
    react,
  },
  rules: {
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```

## Recommended Plugins

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Additional Resources

- [Supabase Docs](https://supabase.com/docs)
- [React Documentation](https://reactjs.org/)
- [Vite Documentation](https://vitejs.dev/)

## Troubleshooting

- Ensure environment variables are correctly set
- Check Supabase project status
- Verify network configurations
- Review Supabase and Vite documentation for the latest updates
