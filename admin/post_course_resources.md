-   [Overview](#overview)
-   [High Priority](#high-priority)
    -   [Important Notes](#important-notes)
-   [Maintaining Personal Files](#maintaining-personal-files)
    -   [Tar and Download](#tar-and-download)
        -   [Tarring](#tarring)
        -   [Downloadng the tarball](#downloadng-the-tarball)
        -   [Unpacking the tarball](#unpacking-the-tarball)
-   [Accessing Course Material](#accessing-course-material)
-   [Course Data](#course-data)
-   [MIC Computing Environment](#mic-computing-environment)
    -   [Using the MIC Computing Environment After the
        Course](#using-the-mic-computing-environment-after-the-course)
        -   [Duke Affiliates](#duke-affiliates)
        -   [People from outside Duke](#people-from-outside-duke)
    -   [The MIC Course Singularity Image and
        Recipe](#the-mic-course-singularity-image-and-recipe)

``` r
library(here)
```

    ## here() starts at /hpc/home/josh/project_repos/mic_course/2022-mic_ssh

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

# Overview

1.  [Personal Notebooks](#Maintaining-Personal-Files): Downloading
    notebooks that you modified
2.  [MIC Course Material](#Accessing-Course-Material): Downloading
    official course material: notebooks, lecture slides, etc
3.  [Course Data](#Course-Data): How to download the data we used in the
    MIC Course
4.  [MIC Computing Environment](#MIC-Computing-Environment): Downloading
    and running the HTS Image in Docker or Singularity

<!-- #region -->

# High Priority

If you have **created or modified files** in your Jupyter container that
you would like to preserve, we recommend that you follow the
instructions for [Maintaining Personal
Files](#Maintaining-Personal-Files). - We recommend you do this before
*as soon as possible*, if you are not a Duke affliate, you may lose
access to your account as soon as the last day of the course. - Keep in
mind that you only need to worry about this for files that you have
**created or modified**. The course material that we created and shared
with you will continue to be publicly available.

## Important Notes

See details below, but please keep the following in mind: 1. The course
material will remain in the [2022 MIC Course
Content](https://gitlab.oit.duke.edu/mic-course/2022-mic) and will be
publicly available, in perpetuity (or as long as
<https://gitlab.oit.duke.edu/> continues to exist), regardless of your
affiliation with Duke (or lack thereof). See below for details. 2. The
configuration and build information for the course Docker container will
remain in the [2022 MIC RStudio Singularity
Image](https://gitlab.oit.duke.edu/mic-course/2022-mic-r-studio-singularity-image)
and will be publicly available, in perpetuity (or as long as
<https://gitlab.oit.duke.edu/> continues to exist), regardless of your
affiliation with Duke (or lack thereof). 3. The 2022 MIC RStudio
Singularity Image will remain in the Duke Singularity Registry and will
be publicly available, in perpetuity (as long as the Duke Singularity
Registry continues to exist and freely host images), regardless of your
affiliation with Duke (or lack thereof).

You can pull (download) the singularity image to your current directory
by running the following command in a terminal on a computer where
singularity is installed

    singularity pull --dir . oras://gitlab-registry.oit.duke.edu/mic-course/2022-mic-r-studio-singularity-image:ver009

> This command will not work within the MIC course environment, because
> Singularity is not installed within it.

# Maintaining Personal Files

## Tar and Download

### Tarring

#### Tarring: Only Notebooks

If you only want to get *Rmarkdown notebooks*, you could use the
following to only grab the notebooks from 2022-mic. This will skip a lot
of stuff you probably don’t want. This archive file will be in your home
directory and will be named 2022-mic-notebooks.tar.gz
<!-- #endregion -->

``` r
tarfile_path=path.expand("~/2022-mic-notebooks.tar.gz")
here() %>%
  setwd

here() %>%
  list.files(recursive = TRUE, 
             pattern=".Rmd",
             full.names = FALSE) %>%
  tar(tarfile=tarfile_path,
      files=.,
      compression = "gzip")
```

    ## Warning in sprintf(gettext(fmt, domain = domain, trim = trim), ...): one
    ## argument not used by format 'invalid gid value replaced by that for user
    ## 'nobody''

    ## Warning: invalid gid value replaced by that for user 'nobody'

#### Tarring: Only Notebooks with a common name

If you want only modified notebooks **and** you saved them with a
standard naming scheme, e.g. leaving `-Copy1` in the name, for example,
renaming `demultiplex.Rmd` to `demultiplex-Copy1.Rmd`, you could use the
following to only grab the modified files from 2022-mic

``` r
tarfile_path=path.expand("~/2022-mic-copyof.tar.gz")
here() %>%
  setwd

here() %>%
  list.files(recursive = TRUE, 
             pattern="CopyOf",
             full.names = FALSE) %>%
  tar(tarfile=tarfile_path,
      files=.,
      compression = "gzip")
```

    ## Warning in sprintf(gettext(fmt, domain = domain, trim = trim), ...): one
    ## argument not used by format 'invalid gid value replaced by that for user
    ## 'nobody''

    ## Warning: invalid gid value replaced by that for user 'nobody'

<!-- #region -->

### Downloadng the tarball

Now you can do one of the following to download the tarball to your
laptop.

1.  In the RStudio *Files* pane, click on *Home* to navigate to the
    directory where you saved the tarball. T
2.  Click the checkbox next to `2022-mic-notebooks.tar.gz`
3.  In the *More* menu of the *Files* pane, select *Export*, then click
    the *Download* in the dialog box that pops up.

### Unpacking the tarball

On a Mac you can “untar” by double clicking on the file in finder, or at
the terminal with the command `tar -zxf 2022-mic-notebooks.tar.gz`.

On Windows, you can download software that will do it, such as
[7-Zip](http://www.7-zip.org/)

> If you named your tarball differently, you should substitute whatever
> name you used above.

# Accessing Course Material

You can access the course material in three different ways:

1.  You can browse and download the material from the [2022 MIC Course
    Repository](https://gitlab.oit.duke.edu/mic-course/2022-mic) by
    clicking on the Download button, which is right next to the blue
    **Clone** button. It will give you a choice of format you want. The
    best options are probably “zip” or “tar.gz”
2.  You can **clone** the repo using git:
    `git clone git@gitlab.oit.duke.edu:mic-course/2022-mic.git`

# Course Data

The data that we used in the course can be downloaded from [Mendeley
Data](https://data.mendeley.com/datasets/3f4rsk96kf/3)

# MIC Computing Environment

## Using the MIC Computing Environment After the Course

### Duke Affiliates

If you are a Duke Affiliate, you can continue to use DCC OnDemand.

1.  If you did not have a DCC account before the course, you will need
    to [follow these
    instructions](https://oit-rc.pages.oit.duke.edu/rcsupportdocs/dcc/#getting-a-dcc-account)
    to request one.
2.  When launching a container, you will need to change the *Account*
    and *Partition* values to an account and partition to which you have
    access.

### People from outside Duke

#### Open OnDemand

The computing environment for our course ran within an [Open
OnDemand](https://openondemand.org/) system. Look at your own
institution to find out if you have access to a cluster running [Open
OnDemand](https://openondemand.org/). If so, you can ask the
administrators if you can run the MIC Course environment there.

1.  You will need the [Singularity Recipe or Singularity
    Image](#The-MIC-Course-Singularity-Image-and-Recipe)
2.  You may need our [Open OnDemand Batch Connect
    App](https://gitlab.oit.duke.edu/chsi-informatics/ood_apps/mic-course-bc)

If [Open OnDemand](https://openondemand.org/) is not installed on your
local cluster, ask the system administrators to install it. It is free,
was developed with funding from the US National Science Foundation, and
is becoming a standard!

You can also run the Singularity image on a cluster or a local server
without Open OnDemand, but that is more complicated!

## The MIC Course Singularity Image and Recipe

The computing environment that we used in the MIC course ran withing a
Singularity Container. The Singularity Image Recipe is here: [2022 MIC
RStudio Singularity
Image](https://gitlab.oit.duke.edu/mic-course/2022-mic-r-studio-singularity-image)
and the built image can be pulled (downloaded) to your current directory
by running the following command in a terminal on a computer where
singularity is installed \> This command will not work within the MIC
course environment, because Singularity is not installed within it.

    singularity pull --dir . oras://gitlab-registry.oit.duke.edu/mic-course/2022-mic-r-studio-singularity-image:ver009

The [SingularityCE User
Guide](https://docs.sylabs.io/guides/latest/user-guide/) has information
on installing and using Singularity
