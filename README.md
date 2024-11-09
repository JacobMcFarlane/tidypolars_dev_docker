# tidypolars_dev_docker
This is the docker image I use for using Tidypolars locally. Built off rocker/tidyverse:4.

# Build container
Clone this repo, and run this command from the root of the repo.
```
docker build -t tidypolars:1.0 .
```

## Start container
Navigate your terminal to the directory that you cloned tidypolars into and call:
```
docker run --rm -ti -e PASSWORD=yourpassword -v ./tidypolars:/home/rstudio/tidypolars -p 8787:8787 tidypolars:1.0
```

## Connect to container
From your browser, navigate to localhost:8787 and login with username rstudio and whatever password you entered in the start command.

In the R console run 

```
install.packages("devtools") # can and should add these to Dockerfile
Sys.setenv(NOT_CRAN = "true")
install.packages("polars", repos = "https://community.r-multiverse.org")
devtools::install("tidypolars")
```

And you are all set to develop!

