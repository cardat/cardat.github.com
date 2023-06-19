---
name: data
layout: default
title: Data Science Tips
---

<h2><abbr title="Centre for Air pollution, energy and health Research Data Analysis Technology">CARDAT</abbr> data</h2>
<hr class="car-red" />
<p><abbr title="Centre for Air pollution, energy and health Research Data Analysis Technology">CARDAT</abbr> stores
a wide array of population, health and environmental datasets. There are three types of data:</p>
<ul>
<li><strong>Open data</strong> - data that has been published on both CloudStor and in the public domain. These data don't require any special access requirements.</li>
<li><strong>General data</strong> - data that is published to CloudStor and is available to all <abbr title="Centre for Air pollution, energy and health Research Data Analysis Technology">CARDAT</abbr> users.</li>
<li><strong>Restricted data</strong> - data that is published to CloudStor, but require permission from the Data Owner before access can be granted.</li>
</ul>
<p>A catalogue of these datasets, including metadata in Ecological Metadata Language (EML) format is kept in the 
<abbr title="Centre for Air pollution, energy and health Research">CAR</abbr> data inventory. These records are published 
<a href="book_down/index.html">here</a>.</p>
<p> Access to <abbr title="Centre for Air pollution, energy and health Research Data Analysis Technology">CARDAT</abbr> data is 
administered by the <abbr title="Centre for Air pollution, energy and health Research">CAR</abbr> data management team 
(<a href="mailto:car.data@sydney.edu.au">car.data@sydney.edu.au</a>).</p>
<h2>Data cleaning</h2>
<p>It is inevitable that the data we work has imperfections. As part of storing data in CARDAT or EHI we often take steps to clean the data. When this is done, we always:</p>
<ul>
<li>save a copy of the original data in the data_provided folder,</li>
<li>save the code that is used to transform the data in the code folder,</li>
<li>save the resulting cleaned data in the data_derived folder, and</li>
<li>include a timestamp as part of the derived data file name,</li>
</ul>
<p>This ensures that the transformation process is transparent and reproducible.</p>

<h3>Data cleaning steps</h3>
<p>There are many issues with data that we see again and again when dealing with data. When cleaning data there are a number of things that may be required, including:</p>
<ul>
<li>fixing character conversion errors for extended character sets,</li>
<li>ensuring data is saved without embedded metadata such as leading rows with introductory text, summary text at the end or multiple header rows within the data,</li>
<li>removing commas from numbers and casting them to numeric format,</li>
<li>converting variables to relevant data formatting standards (for example the International Standards from ISO),</li>
<li>identification of miscellaneous errors such as data inconsistencies and duplicate variable names,</li>
<li>reformatting numeric or character strings where appropriate,</li>
<li>identification of any out-of-range values (based on the specified units), or questionable data in general,</li>
<li>rename all files and variables using lower_case_with_underscores naming convention,</li>
<li>tabulating frequencies and variable distributions, noting any outliers for review,</li>
<li>identification any opportunities to make wide data longer, or many files that can be merged,</li>
<li>if there are multiple linked tables, each table should include a key column that allows those tables to be linked unambiguously (such as the site_ID variables),</li>
<li>checking that values in linked files correspond up to values in related files (e.g. a site_ID in one file that is missing from the spatial data file),</li>
<li>writing as CSV with quote encapsulated strings (for archival purposes),</li>
<li>coding missing data as NA, or identify if these were actually censored,</li>
<li>coercing dates to ISO 8601 YYYY-MM-DD format,</li>
<li>casting nominal variables that use integer codes as character,</li>
<li>checking that all value labels in enumerated lists are described in the metadata (i.e. codes for “1” = “low”, “2” = “mid” and “3” = “high”)</li>
<li>attempt to identify and split any combined variables (for example, season AND year like “winter-97”),</li>
<li>identification of any characters in numeric or date variables and consider replacing with NA, (add to a comments variable if possible or state conversion in metadata),</li>
<li>identify any values that Excel may try to convert to date type (for e.g. Site code “1-5” will appear as 5-Jan and should be rewritten as “site_1-5”),</li>
<li>using a GIS to confirm the distribution of spatial coordinates, and transform geographical coordinates in decimal degrees (GDA94) if supplied in metres UTM or AMG, and</li>
<li>renaming files to be consistent within the framework of the data storage system.</li>
</ul>
<h3>References</h3>
<p>White, E., Baldridge, E., Brym, Z., Locey, K., McGlinn, D., & Supp, S. 2013. Nine simple ways to make it easier to (re)use your data. <em>Ideas in Ecology and Evolution</em>, <strong>6</strong>(2), 1–10. doi:10.4033/iee.2013.6b.6.f</p>

<p>Wickham, H., 2014. Tidy Data. <em>Journal of Statistical Software</em>, <strong>VV</strong> (Ii). Available at: http://vita.had.co.nz/papers/tidy-data.pdf</p>

<p>Leek, J. 2014. https://github.com/jtleek/datasharing</p>

<p>Borer, E., Sea bloom, E., Jones, M., and Schildhauer, M. 2009. Some Simple Guidelines for Effective Data Management. <em>Bulletin of the Ecological Society of America</em> <strong>90</strong>:205–214. http://dx.doi.org/10.1890/0012-9623-90.2.205</p>

<p>Campbell, J. L., Rustad, L. E., Porter, J. H., Taylor, J. R., Dereszynski, E. W., Shanley, J. B., Gries, C., Henshaw, D. L., Martin, M. E., Sheldon, W. M., and Boose, E. R. 2013. Quantity is Nothing without Quality: Automated QA/QC for Streaming Environmental Sensor Data. <em>BioScience</em>, <strong>63</strong>, 574-585. http://dx.doi.org/10.1525/bio.2013.63.7.10</p>

<h3>Working with Github Branches</h3>
<ul>
<li>create a branch using: git checkout -b working_joe</li>
<li>work on stuff</li>
<li>use Github to make a pull request then merge and delete</li>
<li>on your local version delete the branch: git branch -D working_joe</li>
<li>and delete the remote link branch: git fetch origin --prune</li>
</ul>	      


## "Setting up CloudStor WebDav using Rclone"
author: "Lucas Hertzog"
date: "2023-04-12"
output: html_document

CloudStor WebDav is a service provided by AARNet that allows you to access and manage your files stored in the CloudStor platform using the WebDav protocol. Rclone is a command-line tool that allows you to interact with CloudStor WebDav and perform various operations such as syncing, copying, and moving files.

In this guide, we will show you how to set up CloudStor WebDav using Rclone on Windows, Mac, and Linux.

## Windows

1. Download and install Windows File System Proxy (WinFsp) from https://winfsp.org/.
2. Download and install Rclone from https://rclone.org/downloads/.
3. Configure Rclone by following these steps:

- Open a command prompt and run the command "rclone config".
- Follow the on-screen instructions to configure Rclone.
- When prompted for the WebDav URL, enter "https://cloudstor.aarnet.edu.au/plus/webdav/" and press Enter.
- When prompted for the username and password, enter your CloudStor login credentials.

Optionally, you can create a .bat file named "mountrclone.bat" with the following content to automatically mount the drive:

>@echo off
>
>start c:\rclone\rclone mount --vfs-cache-mode full CloudStor:/ z:

This command will mount the CloudStor drive to the Z: drive letter.

## MacOS

1. Install Rclone by running the command "brew install rclone" in Terminal.
2. Configure Rclone by running the command "rclone config" in Terminal.
3. Follow the on-screen instructions to configure Rclone.
4. When prompted for the WebDav URL, enter "https://cloudstor.aarnet.edu.au/plus/webdav/" and press Enter.
5. When prompted for the username and password, enter your CloudStor login credentials.

## Linux

1. Install Rclone by running the command "sudo apt-get install rclone" in Terminal.
2. Configure Rclone by running the command "rclone config" in Terminal.
3. Follow the on-screen instructions to configure Rclone.
4. When prompted for the WebDav URL, enter "https://cloudstor.aarnet.edu.au/plus/webdav/" and press Enter.
5. When prompted for the username and password, enter your CloudStor login credentials.
