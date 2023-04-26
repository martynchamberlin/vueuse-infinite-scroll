# VueUse Infinite Scroll

<p><strong>Bug described:</strong> every time you scroll to the bottom of this scroll view, the <code>getMoreItems()</code> gets called twice when it should only be called once. This results in the <code>count</code> variable increasing by <em>two</em>. Note that this is only reproducible when the callback passed to <code>useInfiniteScroll</code> resolves asynchronously.</p>

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```
