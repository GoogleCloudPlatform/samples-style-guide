# Samples Style Guide

This is the prototype for the samples style guide. 

## Building the site

This project uses [Hugo](https://gohugo.io/) with the [Docsy theme](https://www.docsy.dev/).
Follow these steps to build the site.

1. Clone this repository.

2. Download and [install Hugo (extended)](https://gohugo.io/getting-started/installing/) to your
path.

3. Install [Docsy dependencies](https://www.docsy.dev/docs/getting-started/#install-postcss):
    ```
    npm install -D --save autoprefixer
    npm install -D --save postcss-cli
    ```

4. Get local copies of the theme's submodules:
    ```
    git submodule update --init --recursive
    ```

5. Now run the following command from this project's root directory:
    ```
    hugo serve
    ```