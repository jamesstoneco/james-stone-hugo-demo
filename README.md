This is a demo of how I approached a project using Hugo on [Netlify](https://netlify.com.

You can view the live site at:

[https://james-stone-hugo-demo.netlify.com](https://james-stone-hugo-demo.netlify.com)

## Installation Instructions

Run the following to install hugo on a Mac

`brew update && brew install hugo`

Run the following to install the files required by the theme / gulp build system

`bower install && npm install`

## Running Locally

To run locally and set up a watcher to update files run the following:

`hugo server -w -D -t theme-hugo-foundation6`

To rebuild the CSS and JavaScript from the theme, run the following

`npm run build:dev`

# Netlify Deploy

To deploy on [Netlify](https://netlify.com use the following command:

`npm run build:prod && hugo -D -t theme-hugo-foundation6`

Set the directory to `public`
