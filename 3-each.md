One of the most common requirements when working with a dynamic page is displaying groups of data stored in a collection. To support this requirement, Svelte provides an `each` block, which behaves similar to a `for ... of ...` block in JavaScript.

## each block

The `each` block iterates through a collection of items. Just like a `for...of` block, `each` will provide a local variable for each item in the collection. The core syntax is `{#each <collection> as <item>}`, where \<collection\> is the name of the collection and \<item\> is the variable name you wish to use.

If you had an array of `products`, with each object containing `name` and `id` properties, you could display them as an unordered list by using the following code:

```html
<script>
    let products = [
        {id: 15, name: 'Bicycle'},
        {id: 42, name: 'Running shoes'},
        {id: 134, name: 'Basketball'}
    ];
</script>

<h1>Names</h1>
<ul>
    {#each products as product}
    <li>{product.name}</li>
</ul>
```

## Keyed items

Svelte automatically updates the display as items are added, removed or modified in the array. To support these updates, you should always provide a key for each item so Svelte has a better understanding of what changes to make and how to perform modifications. You provide the key as a final parameter to the `each` block.

As a best practice, always include a key for an `each` block. The key can be anything which is unique for each item.

To update the prior example to provide a key, you could use the following code:

```html
<script>
    let products = [
        {id: 15, name: 'Bicycle'},
        {id: 42, name: 'Running shoes'},
        {id: 134, name: 'Basketball'}
    ];
</script>

<h1>Names</h1>
<ul>
    {#each products as product (product.id)}
    <li>{product.name}</li>
</ul>
```
