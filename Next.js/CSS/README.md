# CSS

## Global Stylesheet

Чтобы добавить глобальные стили в приложение, импортируйте файл CSS в файл pages/_app.js.

```js
import '../styles.css'

// This default export is required in a new `pages/_app.js` file.
export default function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```

Эти стили будут применяться ко всем страницам и компонентам вашего приложения.
Глобальные стили можно импортировать только в внутри `pages/_app.js`.

## Импортировать стили из node_modules

Импорт файла CSS из node_modules разрешен в любом месте вашего приложения.

## CSS Modules

Next.js поддерживает **CSS Modukes**, используя соглашение об именах файлов `[name].module.css`.
В процессе производства все файлы модуля CSS будут автоматически объединены во множество минифицированных и разделенных кодом файлов .css.

## Sass

Для поддержки Sass в Next.js обязательно надо установить пакет sass.

```npm
npm install sass
```

Если вы хотите настроить компилятор Sass, вы можете сделать это с помощью sassOptions в `next.config.js`.

## CSS-in-JS

`CSS-in-JS` тоже поддерживается с небольшими настройками, подробные примеры есть в документации.