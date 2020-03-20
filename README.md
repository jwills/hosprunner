The docker container with the dependencies for the R code we're using:

`docker pull shahsam/covidscenariopipeline:latest`

From that container, the code to run the simulations (single threaded)
is:

`Rscript R/hosp_run.R model_output/unifiedNPI/ high 1`

The output of the run will be written to `hospitalization/model_output/unifiedNPI/`
and the expected outputs are in `hospitalization/model_output/goldenNPI`.

There are a few tweaks to the hosp_run.R code-- we use `%do%` instead of `%dopar%`
for the loops in order to make debugging easier, and I used a `set.seed` call
at the top of the file to make the randomization parts of the run reproducible.

