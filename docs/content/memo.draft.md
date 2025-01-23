# ハンズオン目次

## Hello, chibivite!

```ts
const app = connect()

app.use(function () {
  return 'Hello, chibivite!'
})

app.listen()
```

```sh
node index.mjs
```

## `index.html` へのアクセス

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>chibivite</title>
  </head>
  <body>
    <h1>Hello, chibivite!</h1>
  </body>
</html>
```

```ts
import fs from 'fs/promises'
import connect from

const app = connect()

app.use(async function () {
  const content = await fs.readFile('./index.html', 'utf-8')
  return content
})

app.listen()
```

```sh
node index.mjs
```

## JavaScript へのアクセス

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>chibivite</title>
  </head>
  <body>
    <h1>Hello, chibivite!</h1>
    <script type="module" src="/src/index.mjs"></script>
  </body>
</html>
```

```js
console.log('Hello, chibivite!')
```

```ts
import fs from 'fs/promises'
import connect from

const app = connect()

app.use(async function (req, _, next) {
  if (req.path.endsWith('.mjs')) {
    const content = await fs.readFile('./src/index.mjs', 'utf-8')
    return content
  }
  next()
})

app.use(async function () {
  const content = await fs.readFile('./index.html', 'utf-8')
  return content
})

app.listen()
```

```sh
node index.mjs
```

---

- ツールのセットアップ
- プロジェクトのセットアップ
- Hello, chibivite!
  - Nodeのビルド
- chibivite CLI
  - CLIのビルド
- Dev Serverのセットアップ
  - `createServer()`
  - `listen()`
- `index.html` の処理
- Plugin Container
- TypeScript Transform
- HMR
  - Clientのビルド

# Viteの構成

**Client**

- ブラウザで動作するコード
  - client.ts => HMRの受信側
  - env.ts => 環境変数のインジェクション

**Node**

- CLI
  - cac
    - dev command
    - build command
    - preview command => 対象外(?)
- DevServer
  - connect
    - HTTP Server => ファイルへのリクエストの処理
    - WebSocket Server => HMRの送信側
- PluginContainer
  - Rollupエミュレーション
    - Rollup Plugin
    - Transformation
- esbuild

**HMR**

- HMR Context
- HRM Boundary
- あとで読む：https://bjornlu.com/blog/hot-module-replacement-is-easy

**その他**

- Dependency Pre-Bundling (https://vite.dev/guide/dep-pre-bundling.html)
  - Dependencies vs. DevDependencies
