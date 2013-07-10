Nitrous-Help
============

Nitrous Support Site (proposed)

This is a proposed Support Site for Nitrous.IO. It is similar to the other site except for it uses Jekyll to simplify the process of posting a new article a bit.

### Getting Started

+ Clone the master branch of the repo, and from there run bundler.

    $ git clone REPO_ADDRESS
    $ bundle

+ Create or edit a post within the _posts folder. If you add a Category tag then the document you create will display within the help site's main page under that category.

> Note: You can preview your site by running 'jekyll serve'. You could also use 'jekyll serve --watch' if you are still editing and want to see the changes by refreshing the page.

+ Once finished, push your changes back to the master branch

    $ git add .
    $ git commit -m "blah"
    $ git push origin master

+ From there you will simply need to run Rake in order to publish the static site to the gh-pages branch. There is no need for you to switch to this branch on your own.

    $ rake
