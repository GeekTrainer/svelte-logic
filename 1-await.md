Many webpages load data from an external resource such as an application programming interface (API). These types of calls to a remote system are done asynchronously, allowing the browser to perform other operations while awaiting a response. When making asynchronous calls in a webpage it's important to update the user as there is no default behavior in the browser to indicate an operation is being performed. Svelte provides an `await` block to help support these types of situations.

## await blocks

The `await` block allows you to add a call to an asynchronous function inside of your template. This allows you to customize the display for the three main states of an asynchronous call:

- Executing
- Completed
- Reject (or error)

### Executing

The first section of an `await` block displays while the asynchronous function is executing. You can use this to add a loading message or show an animation.

To create an `await` block you use `{#await}` to start it, and `{/await}` to close. The template to display while the function executes. `await` can use either a reference to a promise, or call the function directly.

Imagine you have a long-running function which calls a remote server named `loadData`. You could use the following code to display a loading message while `loadData` executes.

```html
<script>
    async function loadData() {
        // call to remote server
    }
</script>

{#await loadData()}
    <div>Loading... Please wait...</div>
{/await}
```

## Completed

The `then` block is used to create the template to display when the function completes. If your function returns a value, you can provide a variable to `then` which will contain the return value. This variable will behave like a normal Svelte variable. In the example below, the data will be displayed to the user when the function completes.

You could use the following code to display a loading message while `loadData`, and then update the display with the loaded value by using the following code:

```html
<script>
    async function loadData() {
        // call to remote server
        return data;
    }
</script>

{#await loadData()}
    <div>Loading... Please wait...</div>
{:then value}
    <div>Loading completed! The result is {value}</div>
{/await}
```

## Rejected

If an exception is thrown from an asynchronous function, it is said to have been rejected. The `catch` block allows you to create a template to display should an error occur. `catch` behaves similar to a `catch` block allowing you to declare a variable to store the error. The example below displays the error message to the user.

You could update the code above to add a `catch` block to display an error message if `loadData` threw an error.

```html
<script>
    async function loadData() {
        // call to remote server
        return data;
    }
</script>

{#await loadData()}
    <div>Loading... Please wait...</div>
{:then value}
    <div>Loading completed! The result is {value}</div>
{:catch error}
    <div>Sorry, something went wrong:</div>
    <div>{error.message}</div>
{/await}
```
