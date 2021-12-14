## development

This project used [Lerna](https://lerna.js.org/)

### premise

```bash
yarn global add lerna
```

### environment creation

```bash
mkdir monorepo
cd monorepo

yarn create next-app client
rm -rf client/.git

nest new server
rm -rf server/.git

lerna init
mv server packages
mv client packages
lerna create @monorepo/server ./packages/server
lerna create @monorepo/client ./packages/client

```

in package.json

```bash
{
  "name": "root",
  "private": true,
  "scripts": {
    "dev": "lerna run dev --parallel --stream --scope=@monorepo/{client,server}"
  },
  "devDependencies": {
    "lerna": "^4.0.0"
  }
}
```
