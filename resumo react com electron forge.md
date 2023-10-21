Seguido a documentação do Electron Forge: https://www.electronforge.io/

Iniciando o projeto:

Para iniciar um projeto electron forge Vite modificado para trabalhar com react primeiro devemos rodar o seguinte comando:

```bash
npm init electron-app@latest my-new-app -- --template=vite-typescript
```
lembrando trocar my-new-app pelo nome desejado.

Após o codigo gerado deve se criar um arquivo chamado main-react.ts com o código:

```typescript
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./app";

ReactDOM.createRoot(document.getElementById("root") as HTMLElement).render(
  <React.StrictMode>
    <App/>
  </React.StrictMode>
);
```
depois devemos importar para o arquivo renderer.ts ficando dessa forma:

```typescript
/**
 * This file will automatically be loaded by vite and run in the "renderer" context.
 * To learn more about the differences between the "main" and the "renderer" context in
 * Electron, visit:
 *
 * https://electronjs.org/docs/tutorial/application-architecture#main-and-renderer-processes
 *
 * By default, Node.js integration in this file is disabled. When enabling Node.js integration
 * in a renderer process, please be aware of potential security implications. You can read
 * more about security risks here:
 *
 * https://electronjs.org/docs/tutorial/security
 *
 * To enable Node.js integration in this file, open up `main.ts` and enable the `nodeIntegration`
 * flag:
 *
 * ```
 *  // Create the browser window.
 *  mainWindow = new BrowserWindow({
 *    width: 800,
 *    height: 600,
 *    webPreferences: {
 *      nodeIntegration: true
 *    }
 *  });
 * ```
 */

import "./index.css";
import "./main-react";

console.log(
  '👋 This message is being logged by "renderer.ts", included via Vite'
);
```

após isso não esqueça de criar o arquivo chamado app.tsx e colocar o seguinte código inicial:
```typescript
import { useState } from "react";
import Routes from "./routes";

const App = (): JSX.Element => {
  const [logged, setLogged] = useState<boolean>(false)

  return (
    <>
      <Routes logged={logged} setLogged={setLogged} />
    </>
  );
};

export default App;

```





