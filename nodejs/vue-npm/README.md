# Node.js Sample app using Npm and a Vue framework

## Building

```
pack build vue-sample --buildpack gcr.io/paketo-buildpacks/nodejs \
                      --buildpack "https://github.com/ForestEckhardt/source-removal/releases/download/v0.0.7/source-removal-v0.0.7.tgz" \
                      --buildpack gcr.io/paketo-buildpacks/nginx \
                      --env "BP_NODE_RUN_SCRIPTS=build" \
                      --env "NODE_ENV=development" \
                      --env "BP_INCLUDE_FILES=nginx.conf:public/*"
```

## Running

`docker run --interactive --tty --init --publish 8080:8080 --env PORT=8080 vue-sample`

## Viewing

`curl http://localhost:8080`

### Note

We need the additional flag `--env "NODE_ENV=development"` when running `pack build` since we need the `vue-cli-service` provided in the devDependencies.
