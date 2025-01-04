# 環境

::: tip 🎯 このページのゴール

- TBD
  :::

Viteには環境の概念があります。ここでいう環境とは、コードの実行環境のことです。

## 関数のふるまい

関数は、引数で変える。

```ts
function getMessageTo(name) {
  return `Hello, ${name}!`
}

console.log(getMessageTo('Alice')) // Hello, Alice!
console.log(getMessageTo('Bob')) // Hello, Bob!
```

## 関数のカーリー化

関数を返す。

```ts
const createGetMessageTo = function (name) {
  return function () {
    console.log(`Hello, ${name}!`)
  }
}

const getMessageToAlice = createGetMessageTo('Alice')
const getMessageToBob = createGetMessageTo('Bob')

console.log(getMessageToAlice()) // Hello, Alice!
console.log(getMessageToBob()) // Hello, Bob!
```

## 関数のメタプログラミング

関数のカーリー化では、関数のふるまいの一部を変更することができました。
Functionコンストラクターを使用して、任意のコードを実行できます。

```ts
const codeOfSayHelloToAlice = `console.log('Hello, Alice!')`
const codeOfSayHelloToBob = `console.log('Hello, Bob!')`

const sayHelloToAlice = new Function(codeOfSayHelloToAlice)
const sayHelloToBob = new Function(codeOfSayHelloToBob)

sayHelloToAlice() // Hello, Alice!
sayHelloToBob() // Hello, Bob!
```

Functionコンストラクターに渡す文字列がどのように定義されているかに制限はないため、任意のJavaScriptファイルを読みこんで、その内容を実行することができます。

```ts
// mycode.mjs
return `Hello, Alice!`
```

```ts
// runner.mjs
import fsPromises from 'fs/promises'

async function runCode() {
  const code = await fsPromises.readFile('./mycode.mjs', 'utf-8')

  return new Function(code)
}

console.log(await runCode()) // Hello, Alice!
```

---

::: info ✨ まとめ

- TBD
  :::
