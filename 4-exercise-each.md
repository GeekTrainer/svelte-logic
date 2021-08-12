With the data loaded for the available vacation options, you want to display them to the page.

## Display the list of options

You will add the code to *App.svelte* to display the list of options to the user. You'll use the provided `row` class to display the information in rows and columns.

1. Inside Visual Studio Code, open *src/App.svelte*.
1. Directly below the line which reads `TODO: Add code to display options`, add the following code to create the output:

    ```html
    <!--TODO: Add code to display options-->
    {#each options as option}
        <div class="row">
            <div>
                {option.name}
            </div>
            <div>
                <!--TODO: Add sale display-->

            </div>
            <div>
                §{option.price}
            </div>
        </div>
    {/each}
    ```

    > [!NOTE] You are adding another `TODO` block to mark where you'll insert the last piece of code for this module.

## Test the page

With the code added, you can test your results!

1. Save all files by selecting *File* > *Save All*.
1. Return to your browser, and the page should automatically refresh. If the server was stopped, you can restart it by selecting *View* > *Terminal* inside Visual Studio Code and running `npm run dev`.

    ![Screenshot of the final result showing a header and the number of available options](./media/await.png)

## Summary

You have now added the code to display a list of items in the browser using Svelte.
