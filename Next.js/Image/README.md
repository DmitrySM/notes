# Image Optimization

Next.js использует компонент `next/image` для отображения и оптимизации изображений.
Этот компонент позволяет изменить размер, обслуживать изображения современных форматах,избежать отправки больших изображений.
По умолчанию изображения загружаются лениво.

```js
import Image from 'next/image'

function Home() {
  return (
    <>
      <h1>My Homepage</h1>
      <Image
        src="/me.png"
        alt="Picture of the author"
        width={500}
        height={500}
      />
      <p>Welcome to my homepage!</p>
    </>
  )
}

export default Home

```

В `next.config.js` можно более детально настроить оптимизацию изображений.