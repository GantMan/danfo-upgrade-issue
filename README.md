# This code shows two issues.

## The first issue

is the double CSV load. You can see it takes twice as long because the HUGE CSV is loaded twice.

That issue is captured here: https://github.com/opensource9ja/danfojs/issues/107

## The second issue

is much harder to understand. When you use `danfojs@0.1.2/dist/index.min.js` instead of latest, everything seems to work just fine!

The issue seems to be this code here, which seems unrelated to Danfo.js.  However, the only thing I'm changing between the two, is the version of Danfo and that seems to break this code.

```ts
const history = await transferModel.fit(featureX, Y, {
  validationSplit: 0.2,
  epochs: 20,
  callbacks: { onEpochEnd: console.log },
})
```

If you take a look, data shape is fine! So why is it erroring? And especially, why is it erroring with `Error: Size(53248) must match the product of shape 1664`? The shape should be fine.

Is Danfo accidentally messing with something?



