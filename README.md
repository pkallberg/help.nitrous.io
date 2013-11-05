Nitrous-Help
============

Nitrous Support Site at http://help.nitrous.io/ built with [Jekyll](http://jekyllrb.com/).

### Getting Started

+ Clone the master branch of the repo, and from there run bundler.

```
$ git clone git@github.com:action-io/help.nitrous.io.git
$ bundle
```

+ Create or edit a post within the `_posts` folder. If you add a Category tag then the document you create will display within the help site's main page under that category.

+ Preview your site by running `jekyll serve`. You could also use `jekyll serve --watch` if you are still editing and want to see the changes by refreshing the page.

+ Once finished, push your changes back to the master branch

```
$ git add .
$ git commit -m "blah"
$ git push origin master
```

+ Run Rake in order to publish the static site to the `gh-pages` branch. There is no need for you to switch to this branch on your own.

```
$ rake
```

### Editing CSS

+ This project uses SASS/SCSS implementation, so you will want to only edit the *.scss files within 'css/'. Jekyll will automatically generate *.css files within the same directory, so you do not want to make changes to the CSS files.
