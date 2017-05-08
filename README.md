# dev

hugo server -w -D -t theme-hugo-foundation6

npm run server --prefix themes/theme-hugo-foundation6/scripts

# prod - build on netlify

npm run build:prod && hugo -D -t theme-hugo-foundation6
