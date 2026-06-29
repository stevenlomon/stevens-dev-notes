# What and Why

## Prerequisite Checklist

Next.js is a fantastic Full Stack framework. But it can only feel like a magic trick that lets us build super quickly and worry about super little because it abstracts away _a lot_ from us.  
And in order to both appreciate everything it abstracts away and to have a better chance of understanding the errors it gives when it breaks (it _will_ break in the beginning haha), it's recommended to have a somewhat strong foundation of the following before diving into learning Next:  
* **[React](./../react-fundamentals/what-and-why.md):** Next.js is built on top of React. If we don't already have a strong grasp or React and its fundamental principles, learning Next.js will be a lot harder than it needs to be. JavaScript builds into React which in turn builds into Next.js. It's a natural evolution
* **Backend principles:** Next.js is not a Frontend framework; it's a Full Stack framework. If we've never built a manual backend using a library like Express and we don't have a foundational grasp of writing endpoints, handling HTTP request/response cycles, talking to a database etc etc we will have a mental breakdown every time we use Server Components, Server Actions or anything else that touches the server
  * Directly tied to this; it serves us a lot to understand the basics of **[Client VS Server environments](./../web-dev-fundamentals/client-vs-server-environments.md)** in a web dev context.
* **TypeScript:** We don't _need_ to write using TypeScript when we use Next.js. But the Vercel team that built Next.js heavily pushes us to use it. And since it's a Full Stack framework that acts like the glue between backend and frontend, there is a lot of data that will have different shapes depending on where it is in the pipeline. TypeScript lets us see when variables don't follow the data shape contracts we set as Interfaces.

## What is Next.js?

Up next