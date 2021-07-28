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