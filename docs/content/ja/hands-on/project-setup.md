# プロジェクトのセットアップ

::: warning 🚧 開発中
このオンラインブックは開発中であり、ページ構成や各ページの内容は予告なく変更されます。
:::

::: tip 🎯 このページのゴール

- chibiviteを実装するためのプロジェクトを立ち上げましょう
  :::

さあ、chibiviteの実装をはじめましょう！

---

まずはchibiviteを開発するためのプロジェクトを準備します。このハンズオンでは、[Viteのレポジトリ](https://github.com/vitejs/vite)に準拠して[モノレポ](https://monorepo.tools/)を採用しています。本書ではchibiviteパッケージのみを開発するためモノレポを採用せずに開発することもできますが、可能な限りViteのコードベースと同じ構成を採用することで、Viteのコードベースに慣れることができるでしょう。

1. 開発エディタで、chibiviteを開発するディレクトリを開きます。
2. `package.json`を作成し、以下の内容をコピーしてください。

   ```json
   {
     "name": "chibivite-monorepo",
     "private": true,
     "version": "0.0.0",
     "type": "module",
     "sideEffects": false,
     "engines": {
       "node": ">=20.12.0"
     },
     "packageManager": "pnpm@9.1.2",
     "scripts": {},
     "devDependencies": {}
   }
   ```

3. ターミナルで以下のコマンドを実行して、Corepackとpnpmを有効化します。`package.json`に記載されているpnpmのバージョンが表示されれば成功です。

   ```bash
   corepack enable && pnpm --version
   ```

4. ターミナルで以下のコマンドを実行して、`packages/chibivite`ディレクトリを作成します。

   ```bash
   mkdir -p packages/chibivite
   ```

5. `packages/chibivite`ディレクトリに`package.json`を作成し、以下の内容をコピーしてください。

   ```json
   {
     "name": "chibivite",
     "private": true,
     "version": "0.0.0",
     "type": "module",
     "sideEffects": false,
     "engines": {
       "node": ">=20.12.0"
     },
     "packageManager": "pnpm@9.1.2",
     "scripts": {},
     "dependencies": {},
     "devDependencies": {}
   }
   ```

6. プロジェクトルートに`pnpm-workspace.yaml`を作成し、以下の内容をコピーしてください。

   ```yaml
   packages:
     - packages/*
   ```

7. ターミナルでプロジェクトルートに移動し以下のコマンドを実行して、`pnpm-lock.yaml`を作成します。

   ```bash
   cd /path/to/project/root
   ```

   ```bash
   pnpm install
   ```

---

おめでとうございます！これでchibiviteを開発する準備ができました！🎉
