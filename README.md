# David's Demise: A 5k Challenge

This is a SvelteKit project to publicly and humorously challenge my friend David to a 5k race on November 9th, 2025.

## How to Run Locally

1.  **Install dependencies:**
    ```bash
    npm install
    ```
2.  **Start the development server:**
    ```bash
    npm run dev
    ```
3.  Open your web browser and go to `http://localhost:5173`.

## How to Deploy to GitHub Pages

1.  **Install `gh-pages`:**
    ```bash
    npm install -D gh-pages
    ```
2.  **Configure `svelte.config.js`:**
    *   Update the `paths` configuration in `svelte.config.js` to include your repository name:
        ```javascript
        const config = {
            // ...
            paths: {
                base: process.env.NODE_ENV === 'production' ? '/YOUR_REPOSITORY_NAME' : '',
            }
            // ...
        };
        ```
3.  **Add a deploy script to `package.json`:**
    *   Add the following script to the `scripts` section of your `package.json`:
        ```json
        "deploy": "npm run build && gh-pages -d build"
        ```
4.  **Deploy the site:**
    ```bash
    npm run deploy
    ```

Your site will be live in a few minutes at `https://YOUR_USERNAME.github.io/YOUR_REPOSITORY_NAME/`.
