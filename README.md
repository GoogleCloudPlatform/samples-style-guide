# Samples Style Guide

This is the **home** of the Google Cloud Samples Style Guide.

You can [read the guide](https://googlecloudplatform.github.io/samples-style-guide/) and open issues for feedback.

## Building the site

This project uses [Hugo](https://gohugo.io/) with the [Docsy theme](https://www.docsy.dev/).
Follow these steps to build the site.

1. Clone this repository.

2. Download and [install Hugo (extended)](https://gohugo.io/getting-started/installing/) to your
path.

3. Install [Docsy dependencies](https://www.docsy.dev/docs/getting-started/#install-postcss):

    ```sh
    npm install
    ```

4. Install the site theme as git submodules:

    ```sh
    git submodule update --init --recursive
    ```

5. Run the local development server with the hugo CLI from the repository's root directory:

    ```sh
    hugo serve
    ```
