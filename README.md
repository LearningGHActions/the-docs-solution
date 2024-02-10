# CorpX Documentation

Welcome to CorpX documentation! Our documentation serves as a vital resource for understanding our products, services, and processes. It ensures clarity, consistency, and accessibility for both internal teams and external users. We value your contributions to keeping our documentation robust and up-to-date.

## Why Documentation Matters

Clear and comprehensive documentation is essential for several reasons:

- **Accessibility**: It provides easy access to information for all stakeholders, including developers, designers, and end-users.
- **Consistency**: It ensures consistency in communication, reducing confusion and errors.
- **Onboarding**: New team members can quickly familiarize themselves with our products and processes, accelerating their onboarding process.
- **Troubleshooting**: It serves as a reference point for troubleshooting common issues and resolving queries efficiently.

## Why Eleventy (11ty)?

We've chosen eleventy (11ty) as our static site generator for several reasons:

- **Simplicity**: Eleventy offers a simple and intuitive approach to building static sites, making it easy for contributors to focus on content creation.
- **Flexibility**: It provides the flexibility to structure content in various formats, including Markdown, HTML, and JavaScript templates.
- **Performance**: Eleventy generates fast and lightweight static sites, ensuring optimal performance for users.
- **Community Support**: With a growing community and active development, Eleventy is continuously improving and evolving to meet the needs of developers and content creators.

## How to Contribute

Contributing to our documentation is straightforward. Follow these steps to make changes:

1. **Clone the Repository**: Clone the documentation repository to your local machine.

2. **Install Dependencies**: Navigate to the root of the project and install dependencies using npm:

    ```shell
    npm install
    ```

3. **Run Development Mode**: Start the development server and watch for changes:

    ```shell
    npm start
    ```

4. **Run Production Mode**: Before deploying changes live, compress the Sass files:

    ```shell
    npm run prod
    ```

For additional npm scripts and details, refer to the [package.json](https://github.com/conedevelopment/sprucecss-eleventy-documentation-template/blob/main/package.json).

## Content Management

Adding content to the documentation template is straightforward with Eleventy:

### Basic Structure

- The base folder for documentation pages is `posts`.
- Follow the folder structure, including the category. Each category folder must have a list page with the same name.
- Create another `posts` folder under each category folder for your posts.
- Create a `posts.json` file to set layout and permalink values.

### Eleventy Navigation

Utilize the [Eleventy Navigation plugin](https://www.11ty.dev/docs/plugins/navigation/) to set up hierarchy for automatic sidebar navigation, navigation order, and breadcrumb generation.

### Other Pages

For simple pages, create a file directly under the `src` folder and configure it with available front matter.

## Project Structure

```plaintext
spruecss-eleventy-documentation-template/
├─ node_modules/
├─ dist/
├─ src/
│  ├─ _data/
│  ├─ _includes/
│  ├─ css/
│  ├─ filters/
│  ├─ font/
│  ├─ img/
│  ├─ js/
│  ├─ posts/
│  ├─ scss/
│  ├─ shortcodes/
│  ├─ transforms/
│  ├─ changelog.md
│  ├─ faq.md
│  ├─ index.md
├─ .eleventy.js
├─ package.json
├─ README.md
├─ ...
```

- **_data**: Some global data, like the name of your site and helpers like the active navigation element or current year.
- **__includes**: All of the layout and partial templates.
- **css**: The compiled CSS.
- **filters**: The additional filters that you can use.
- **font**: The custom fonts.
- **img**: The static image files.
- **posts**: The markdown contents.
- **scss**: The Sass files.
- **shortcodes**: The available shortcodes.
- **transforms**: The transformations.
