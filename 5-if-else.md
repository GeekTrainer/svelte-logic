Quite commonly you will need to modify the display based on boolean logic. You may need to show a banner if an item is on sale, or display either a login or logout link depending on the state of the current user. You can use `if...else` blocks in Svelte to modify display based on boolean logic.

## if blocks

A Svelte `if` block behaves just like an `if` statement in JavaScript. It accepts a boolean or boolean-like value, and will display the contents of the block if the expression is evaluated to true. Just like the JavaScript `if`, any values which are `null`, `unknown`, 0 or an empty array evaluate as `false`.

One very common scenario for an `if` block is toggling display between login and logoff. As you might suspect, `if` also includes an `else` block, which will display should the expression evaluate as `false`. The code below could be used to toggle login/logoff displays.

```html
<script>
    let user = {
        authenticated: true,
        admin: true,
        name: 'demo'
    }
</script>

{#if user.authenticated}
    <div>
        Welcome {user.name}!
    </div>
    <div>
        <a href="#">Logout</a>
    </div>
{:else}
    <div>
        <a href="#">Login</a>
    </div>
{/if}
```

## else if

Similar to JavaScript, you can create an `else if` block by using `{:else if}`. As with any programming language, only the first `if` block to evaluate as `true` will be executed.

Imagine you were displaying information about a product for an e-commerce site. If supplies were low you might want to display an "order soon!" message. Of course, if no items were in stock, you would want to display a "sold out" message. The code below would work for this scenario:

```html
<script>
    let product = {
        name: 'Widget',
        price: 42
        inStock: 5
    }
</script>

<div>{product.name} §{product.price}</div>
{#if product.inStock < 5}
    <div>Order soon! Supplies are limited.</div>
{#else if product.inStock === 0}
    <div>Sorry, this item is out of stock</div>
{/if}
```
