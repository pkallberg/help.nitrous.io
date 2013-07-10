Nitrous-Help
============

Nitrous Support Site (proposed)

This is a proposed Support Site for Nitrous.IO. It is similar to the other site except for it uses Jekyll to simplify the process of posting a new article a bit.

### Getting Started

Clone the master branch of the repo, and from there run bundler.

    $ git clone REPO_ADDRESS
    $ bundle

Create or edit a post within the _posts folder. If you add a Category tag then the document you create will display within the help site's main page under that category.

Once finished, push your changes back to master to keep this branch up to date. 

Next, switch to (create) the gh-pages branch. This is the branch used for Github Pages:

    $ git checkout -b gh-pages master

Now you will want to generate the static site as Github Pages doesn't allow the plugins being used.

    $ rake site:publish
    
Once this has been successfully done it will automatically force push to the gh-pages branch.
