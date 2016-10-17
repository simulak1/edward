# Edward website

The backend of our website depends on [pandoc](http://pandoc.org), [pandoc-citeproc](http://pandoc.org), and [beautifulsoup](https://www.crummy.com/software/BeautifulSoup/). This lets us write stand-alone pages for documentation using LaTeX. It also lets us auto-generate API documentation from the source code's docstrings.

The frontend of our website depends on [skeleton.css](http://getskeleton.com/), [Google Fonts](https://www.google.com/fonts), [highlight.js](https://highlightjs.org/), and [KaTeX](https://khan.github.io/KaTeX/).

## Editing the website

All stand-alone pages are in `docs/tex`. These compile to root level HTML pages. Our custom pandoc HTML template is `docs/tex/template.pandoc`.

## Building the website

+ Install the dependencies
```{bash}
pip install pandoc pandoc-attributes pandocfilters beautifulsoup4 ghp-import
```
+ You can build the website locally. Go to this `docs/` directory and run
```{bash}
./compile.sh
```
  The output of the compile script is a set of static HTML pages. The
  HTML pages use absolute filepaths. In order to view them locally, use
  a HTTP server such as Python's built-in
  [`SimpleHTTPServer`](https://docs.python.org/2/library/simplehttpserver.html)
  or Node.js'
  [`http-server`](https://www.npmjs.com/package/http-server).

## Deploying the website

+ We deploy the documentation so that it is available on this repo's
  Github pages (the `gh-pages` branch). To do this (and assuming you
  have push permission), go to this directory. Then run
```{bash}
./deploy.sh
```
  We forward the main domain url to the Github pages url,
  [blei-lab.github.io/edward](http://blei-lab.github.io/edward).
  Following
  [Github's guide](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages),
  namely, we make a `CNAME` file; then we update the DNS record on
  the DNS provider.
