# TypeScript

**Next.js** поддерживает `TypeScript` из коробки. Для подключения создайте файл `tsconfig.json` в корне проекта.
**Next.js** использует `Babel` для обработки `TypeScript`.

Запустите 
```npm
npm run dev
```
или
```npm
yarn dev
```
что бы установить недостающие пакеты и завершить настройку `TypeScript`.

По умолчанию **Next.js** выполняет проверку типов во время сборки.

## Типы для рендеринга

```js
import { GetStaticProps, GetStaticPaths, GetServerSideProps } from 'next'

export const getStaticProps: GetStaticProps = async (context) => {
  // ...
}

export const getStaticPaths: GetStaticPaths = async () => {
  // ...
}

export const getServerSideProps: GetServerSideProps = async (context) => {
  // ...
}
```

## Маршруты API

```js
import type { NextApiRequest, NextApiResponse } from 'next'

export default (req: NextApiRequest, res: NextApiResponse) => {
  res.status(200).json({ name: 'John Doe' })
}
```

```js
import type { NextApiRequest, NextApiResponse } from 'next'

type Data = {
  name: string
}

export default (req: NextApiRequest, res: NextApiResponse<Data>) => {
  res.status(200).json({ name: 'John Doe' })
}
```