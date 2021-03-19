# Static Generation (Recommended)

При **статической генерации** HTML-код создается во время сборки проекта. И повторно используется при каждом запросе.

По умолчанию Next.js выполняет предварительную визуализацию страниц с использованием статической генерации.

## Статическая генерация с получением данных 

Для получения внешних данных надо экспортировать `getStaticProps` или `getStaticPaths` если пути к страницам зависят от внешних данных. Эти функции вызываются во время сборки.

`getStaticProps` и `getStaticPaths` должны находится в файле страницы.

В обычных случаях хватает `getStaticProps`:

```js
function Blog({ posts }) {
  // Render posts...
}

// This function gets called at build time
export async function getStaticProps() {
  // Call an external API endpoint to get posts
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // By returning { props: { posts } }, the Blog component
  // will receive `posts` as a prop at build time
  return {
    props: {
      posts,
    },
  }
}

export default Blog
```

Но если используется страница с динамическими маршрутами (`pages/posts/[id].js`) то надо еще использовать `getStaticPaths`.

`getStaticPaths` так же вызывается во время сборки и позволяет указать какие пути надо предварительно визуализировать:
```js
// This function gets called at build time
export async function getStaticPaths() {
  // Call an external API endpoint to get posts
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Get the paths we want to pre-render based on posts
  const paths = posts.map((post) => `/posts/${post.id}`)

  // We'll pre-render only these paths at build time.
  // { fallback: false } means other routes should 404.
  return { paths, fallback: false }
}
```
