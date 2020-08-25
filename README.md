# await.ops proposal

The [rendered spec text](https://tc39.es/proposal-await.ops/). [Playground Link](https://www.staging-typescript.org/play?ts=4.0.0-pr-39224-4#code/IYZwngdgxgBAZgV2gFwJYHsIwB4AoCUMA3gFAzkzADuwqyAdMADZMwAMZF1tDATsFACmMANoAFXugC2qEIPq9BIdEwBug3AEZ8AXU7ludRiwDKg5MiaCAJqL0BfIA)

Introduce await.all / await.race / await.allSettled / await.any to simplify the usage of Promises

Stage: 1

Champions: [Jack Works](https://github.com/Jack-Works), [Jordan Harband](https://github.com/ljharb)

## Motivation

- To simplify the usage of a set of Promises. (Previous discussions: https://es.discourse.group/t/allow-awaiting-on-arrays/178/19)
- To simplify the usage of concurrent for loop in async functions.

Usage:

```js
// before
await Promise.all(users.map(async x => fetchProfile(x.id)))

// after
await.all users.map(async x => fetchProfile(x.id))
```

Syntax:

```js
await.all expr
// eq: await Promise.all(expr)

await.race expr
// eq: await Promise.race(expr)

await.allSettled expr
// eq: await Promise.allSettled(expr)

await.any expr
// eq: await Promise.any(expr)
```
