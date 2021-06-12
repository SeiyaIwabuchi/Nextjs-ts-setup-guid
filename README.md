# nextjsの始め方
- https://nextjs.org/docs
- ディレクトリの構成はこのようになる
``` text
project-root
├ pages
│ └ index.js(option)
├ .gitignore
└ package.json
```
- ディレクトリツリーの作成に使用 https://codogue.com/asciitree/
1. node.jsを入れる！
2. プロジェクトディレクトリを作る
3. npm init
4. npm install next react react-dom
5. package.jsonの編集
  1. scriptを以下のように書き換える
  ``` json
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  }
  ```
  2. mainを削除
6. pagesディレクトリを作成
7. npx next build でビルド
8. npx next start でサーバーの起動
9. .vscode/にlaunch.jsonやtasks.jsonを作成
- launch.json
   ``` json
   {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "attach",
            "name": "debugger",
            "skipFiles": [
                "<node_internals>/**"
            ],
            "port": 9229,
            "preLaunchTask" : "npm: dev - nextjs-blog"
        }
    ]
   }
   ```
   - tasks.json
   ``` json
   {
  "version": "2.0.0",
  "tasks": [
    {
      "type": "npm",
      "script": "build",
      "path": "nextjs-blog/",
      "group": "build",
      "problemMatcher": [],
      "label": "npm: build - nextjs-blog",
      "detail": "next build"
    },
    {
      "type": "npm",
      "script": "dev",
      "path": "nextjs-blog/",
      "problemMatcher": [],
      "label": "npm: dev - nextjs-blog",
      "detail": "next dev",
      "group": {
        "kind": "build",
        "isDefault": true
      },"dependsOn" : [
        "npm: build - nextjs-blog"
      ]
    }
  ]
  }
   ```
10. .gitignoreを作成
  ``` gitignore
  # See https://help.github.com/articles/ignoring-files/ for more about ignoring files.

  # dependencies
  /node_modules
  /.pnp
  .pnp.js

  # testing
  /coverage

  # next.js
  /.next/
  /out/

  # production
  /build

  # misc
  .DS_Store
  *.pem

  # debug
  npm-debug.log*
  yarn-debug.log*
  yarn-error.log*

  # local env files
  .env.local
  .env.development.local
  .env.test.local
  .env.production.local

  # vercel
  .vercel
  ```
## typescript対応
1. npm install --save-dev @types/react
2. npx tsc --init
