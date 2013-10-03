---
layout: article
title: Uploading files via the Web IDE
published: true
categories: [usage]
---

Uploading files to Nitrous.IO is quick and easy. There's no need to FTP or SCP files to your development box (although you can, if you want to).

<p class="alert">This article describes how to upload individual files. If you need to upload an entire project / complex directory structure, please read [this article]()</p>

In the file browser, right-click the destination directory where you'd like to upload the image and click "Upload files to \[your folder name\]".

![Directory Menu](https://raw.github.com/action-io/action-assets/master/support/screenshots/file-uploads-1.png)

A file upload modal will appear, where you can drag & drop multiple files or browse for files manually. You can upload a bunch of files at once, so feel free to add up to 5 files at a time.

![File Upload Modal](https://raw.github.com/action-io/action-assets/master/support/screenshots/file-uploads-2.png)

Once you've dropped the files you want to upload, click the "Upload" button at the bottom right-hand side of the modal.

You'll see the status of each file uploaded via the progress bar to the right of the filename.

![File Upload Status](https://raw.github.com/action-io/action-assets/master/support/screenshots/file-uploads-3.png)

<div class="alert alert-notice">
  We support .png, .jpeg, .gif, and .pdf file uploads
</div>

After each file is uploaded successfully, the modal will disapear and you'll be back in the Nitrous.IO IDE. The file browser should refresh automatically and you should see your uploaded files in the correct directory.

![File Directory](https://raw.github.com/action-io/action-assets/master/support/screenshots/file-uploads-4.png)

If you don't see the files you've uploaded, you can right click and select "Refresh" to refresh the contents of a folder, or click the refresh icon at the top of the file browser to refresh the entire tree.

If you want to view an image in the browser, simply click the image to open a preview tab inside of the web ide.

![Airmax](https://raw.github.com/action-io/action-assets/master/support/screenshots/airmaxpair.png)

#Upload a directory via the Web IDE

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
