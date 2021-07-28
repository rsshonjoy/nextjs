### Incremental Static Regeneration
1. There was a need to update only those pages which needed a change without having to rebuild the entire app.
2. Incremental Static Regeneration.
3. With ISR, Next.js allows you to update static pages after you have bulid your application.
4. You can statically generate individual pages without needing to rebuild the entire site, effectively solving the issue of dealing with state data.

### How Incremental Static Regeneration
1. In the getStaticProps function, apart from the props key, we can specify a revaildate key.
2. The value for revaildate is the number of seconds after which a page re-generation can occur.

### Re-generation
1. A re-generation is initiated only if a user makes a request after the revaildate time.
2. If a user visits our product details page but there is no other user hitting that page the entire day, the re-generation does not happen.
3. Revalidate does not mean the page automatically re-generates every 10 seconds.
4. It simple denotes the time after which, if a user makes a request, a re-generation has to be initiated.
5. The re-generation can also fail and the previouly cached HTML could be served till the subsequent re-generations succeed.

### Two forms of pre-rendering 
1. Static Generaion
2. Server-side Rendering

### Static Generaion

- The HTML is statically generated at build time. The build page is then cached and reused for each request.
- For a dynamic page with getStaticPaths and fallback set to true the page in not generated at build time but is generated on the initiat request.
- With Incremental static Regeneration, a page can be Regeneration for a request after the revalidation time has elapsed.
- For the most part, the pages are generated using getStaticProps when you build the project.

### Problems with Static Generaion

1. We cannot fetch data at request time.

- With not being able to fetch data per request, we run into the problem of stale data.
- Lets say we are building a news website.-. The content is very dynamic in the sense that new articles can be published almost every second.
- getStaticProps wil fetch the news at build time which is not suitable at all.
- getStaticPaths will help fetch the data on the initiat request but it is then cached for subsequent requests
- Incremental static regeneration (ISR) can help but if revaildate is 1 second, we still might not always see the most up to date news when the regeneration is happening in the background.
- Rather fetch the data on the client side by making a get requiest from the Component. But no SEO.

2. We do not get access to the incomming request

- Problem when the data needs to be fetched is specify to a user.
- Lets say we are building a website similar to twitter.
- As a user, I should be able to see tweets that are personalized based on my interests.
- The tweets that I see also need to be SEO friendly as it is public content that anyone in the world can see.
- To fetch tweets specify to the user, we need the userId. And that can be obtained only if have we access to the incomming request.
- You could do it client side in useEffect for example but that means you again miss out on SEO.
