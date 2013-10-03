---
layout: article
title: Upload a directory via the Web IDE
published: true
categories: [usage]
---

The File Upload/ide-file-uploads feature on the Web IDE is intended for individual files.

If you need to upload an entire directory, we suggest using either SFTP or Git. Another option you have, is to zip your application into an archive and then upload the zipped archive via the Web IDE upload.

First, zip up your project using your favorite archving application. On later versions of Mac OS X and Windows this is built in.

![Compress](https://raw.github.com/action-io/action-assets/master/support/screenshots/compress-menu.png)

Then, open up the IDE in your box on Nitrous.IO and below the file browser, click the "Upload Files" button.

![IDE Upload](https://raw.github.com/action-io/action-assets/master/support/screenshots/ide-upload.png)

<p class="alert">The file upload tool in the web IDE has a size limit of 20MB. If you have a large project, we suggest uploading the file via SFTP or Git</p>

Once you have your archive uploaded, you'll need to unzip it using the console. Click into the console and navigate to your directory:

    cd workspace

Then unzip the package using the "unzip" command:

    unzip help-articles.zip

<p class="note">Make sure you've moved the archive into the desired directory before unzipping.</p>
