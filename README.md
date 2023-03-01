## This is the batch script I used to generate this.
```bat
set /p project_name= Project Name: 
call npm create vite@latest %project_name% -- --template react
cd %project_name%
call npm i
echo %project_name%
call npm install -D tailwindcss postcss autoprefixer react-icons react-router-dom express cross-env
call npx tailwindcss init -p



echo /** @type {import('tailwindcss').Config} */ > tailwind.config.cjs
echo module.exports = { >> tailwind.config.cjs
echo   content: [ >> tailwind.config.cjs
echo     "./index.html", >> tailwind.config.cjs
echo     "./src/**/*.{js,ts,jsx,tsx}", >> tailwind.config.cjs
echo   ], >> tailwind.config.cjs
echo   theme: { >> tailwind.config.cjs
echo     extend: {}, >> tailwind.config.cjs
echo   }, >> tailwind.config.cjs
echo   plugins: [], >> tailwind.config.cjs
echo } >> tailwind.config.cjs

cd src
DEL App.css App.jsx index.css 

call mkdir components
call mkdir pages

echo @tailwind base; > style.css
echo @tailwind components; >> style.css
echo @tailwind utilities; >> style.css
echo. >> style.css
echo @layer base { >> style.css
echo 	/* for elements */ >> style.css
echo } >> style.css
echo. >> style.css
echo @layer components { >> style.css
echo 	/* for classes */ >> style.css
echo } >> style.css
echo. >> style.css
echo @layer utilities { >> style.css
echo 	/* for text gradients, usage "text-gradient from-[color] to-[color]" */ >> style.css
echo 	.text-gradient { >> style.css
echo 		@apply inline-block bg-clip-text text-transparent; >> style.css
echo 	} >> style.css
echo. >> style.css
echo 	/* vertical and horizontal centering */ >> style.css
echo 	.VHcenter { >> style.css
echo 		@apply items-center justify-center; >> style.css
echo 	} >> style.css
echo } >> style.css

echo import React from 'react'; > main.jsx
echo import ReactDOM from 'react-dom/client'; >> main.jsx
echo import App from './App'; >> main.jsx
echo import ^'./style.css^'; >> main.jsx
echo. >> main.jsx
echo ReactDOM.createRoot(document.getElementById('root')).render^( >> main.jsx
echo     ^<React.StrictMode^> >> main.jsx
echo         ^<App /^> >> main.jsx
echo     ^</React.StrictMode^>, >> main.jsx
echo ^); >> main.jsx


echo import ^'./style.css^'; > App.jsx
echo. >> App.jsx
echo function App() { >> App.jsx
echo   return ( >> App.jsx
echo     ^<div^> >> App.jsx
echo     ^</div^> >> App.jsx
echo   ) >> App.jsx
echo } >> App.jsx
echo. >> App.jsx
echo export default App; >> App.jsx


cd assets
DEL react.svg
cd ../../public
DEL vite.svg

cd ..
mkdir server
cd server

echo const express = require('express'); > server.js
echo const path = require('path'); >> server.js
echo. >> server.js
echo const app = express(); >> server.js
echo const port = process.env.PORT ^|^| 3000; >> server.js
echo const DIST_DIR = path.join(__dirname, '../dist'); >> server.js
echo const HTML_FILE = path.join(DIST_DIR, 'index.html'); >> server.js
echo const mockResponse = { >> server.js
echo   far: 'boo', >> server.js
echo   boo: 'far', >> server.js
echo }; >> server.js
echo app.use(express.static(DIST_DIR)); >> server.js
echo app.get('/api', (req, res) =^> { >> server.js
echo   res.send(mockResponse); >> server.js
echo }); >> server.js
echo app.get('/', (req, res) =^> { >> server.js
echo   res.sendFile(HTML_FILE); >> server.js
echo }); >> server.js
echo app.listen(port, function () { >> server.js
echo   console.log('App listening on port: ' + port); >> server.js
echo }); >> server.js
```