# React + Vite

# Project Setup Instructions

This guide provides step-by-step instructions on how to set up and run the project. Our setup uses Vite for the frontend and Express for the backend, and it's configured for easy deployment on platforms like Heroku.

## 1. Initializing the Project with Vite

To start the project, run the following command:


`npm init vite@latest .` 

This initializes a new project using Vite, a modern frontend build tool, in the current directory.

## 2. Node Version Management

Install and use Node.js version 20.5.0 using nvm (Node Version Manager) with these commands:

nvm install stable

This is what i used:
- nvm install 20.5.0
- nvm use 20.5.0` 

## 3. Updating npm Globally

Update npm, the Node package manager, to version 10.2.5 globally:


`npm install -g npm@10.2.5` 

## 4. Installing Dependencies

Install the required dependencies:



`npm install
npm install express
npm install compression` 

-   The first command installs all dependencies listed in your project's `package.json`.
-   The second and third commands install `express` and `compression` packages for server optimization.

## 5. Installing Frontend Libraries

Install frontend libraries with:


`npm install axios react-router-dom bootstrap` 

-   `axios`: For making HTTP requests.
-   `react-router-dom`: For routing in a React application.
-   `bootstrap`: For styling.

## 6. Configurations in `package.json`

Ensure the following configurations are set in your `package.json`:

-   `"engines"`: Specifies the Node.js version, here any version starting with 20.
-   `"scripts"`: Contains scripts for development and production:
    -   `"dev"`: Runs Vite in development mode.
    -   `"heroku-postbuild"`: Script for Heroku deployment.
    -   `"start"`: Starts the server.
    -   `"build"`: Creates a production build.
    -   `"lint"`: Runs ESLint.
    -   `"preview"`: Previews the production build.

## Server Configuration

### Set up the server using Express:
<article>
import  express  from  'express';
import  path  from  'path';
import { fileURLToPath } from  'url';
import  compression  from  'compression';  

const  __dirname = path.dirname(fileURLToPath(import.meta.url));  

const  app = express();
app.use(compression());
app.use(express.static(path.join(__dirname, 'dist')));

app.get('*', (req, res) => {
res.sendFile(path.join(__dirname, 'dist', 'index.html'));
});
const  port = process.env.PORT || 3000;
app.listen(port, () => {
console.log(`Server is running on port ${port}`);
});`
</article>
## 7. Procfile for Deployment

Create a Procfile for deployment platforms like Heroku:


`web: node server.js` 

## 8. Building the Application

Build the application for production with:


`npm run build`




This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh
