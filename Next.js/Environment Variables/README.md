# Environment Variables

В **Next.js** существует встроенная поддержка переменных среды.

Возможности:

- Использовать `.env.local` для загрузки переменных среды
- Предоставить браузеру переменные среды

## Загрузка переменных среды

В **Next.js** встроена поддержка загрузки переменных среды из `.env.local` в `process.env`.

`.env.local`
```
DB_HOST=localhost
DB_USER=myuser
DB_PASS=mypassword
```

```js
// pages/index.js
export async function getStaticProps() {
  const db = await myDB.connect({
    host: process.env.DB_HOST,
    username: process.env.DB_USER,
    password: process.env.DB_PASS,
  })
  // ...
}
```

**Next.js** автоматически расширяет переменные `$VAR` внутри ваших файлов `.env`
```
# .env
HOSTNAME=localhost
PORT=8080
HOST=http://$HOSTNAME:$PORT
```

## Предоставление браузеру переменных среды

Чтобы открыть переменную браузеру, вы должны поставить перед переменной префикс `NEXT_PUBLIC_`.

Например:
```
NEXT_PUBLIC_ANALYTICS_ID=abcdefghijk
```

Это автоматически загружает `process.env.NEXT_PUBLIC_ANALYTICS_ID` в среду **Node.js**, позволяя вам использовать его в любом месте вашего кода. Значение будет встроено в **JavaScript**, отправленный в браузер, из-за префикса `NEXT_PUBLIC_`.

```js
// pages/index.js
import setupAnalyticsService from '../lib/my-analytics-service'

// NEXT_PUBLIC_ANALYTICS_ID can be used here as it's prefixed by NEXT_PUBLIC_
setupAnalyticsService(process.env.NEXT_PUBLIC_ANALYTICS_ID)

function HomePage() {
  return <h1>Hello World</h1>
}

export default HomePage
```

## Переменные среды по умолчанию

**Next.js** позволяет вам устанавливать значения по умолчанию в `.env` (все среды), `.env.development` (среда разработки) и `.env.production` (производственная среда).
`.env.local` всегда отменяет установленные значения по умолчанию.