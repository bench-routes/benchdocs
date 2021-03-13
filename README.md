# Website

This repository contains code for Bench-routes website.

In order to run this locally, you need:
1. Hugo locally installed. See [here](https://gohugo.io/getting-started/installing/) for installation instructions. (Might require installation of golang as well)
2. Clone the project
3. Change dir to `website`
4. To run: `hugo server --theme ../.. --disableFastRender`

Please make sure for any new changes, please build the website using
```shell
cd website && hugo --minify && mv public ../docs && cd ..
```

This will allow the recent content to be deployed as the PR gets merged.
(Github pages deploys the contents in the `docs/` dir)
