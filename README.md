# Standard Notes Docker Compose Deployment

I didn't like that there were no official Docker images for the Standard Notes
front-end or back-end, so I decided it was best to set up a repository to build
the Docker images from source and deploy them with Docker Comopse.

There is also a GitLab CI configuration, which I set up to run on a schedule to
keep the deployment up to date.

## How to use this repository

1. Edit the `docker-compose.yml` file
  - Update all the values that include `changeme`
  - The `SECRET_KEY_BASE` for both `api` and `web` should each be a unique random string, you could use the command `openssl rand -hex 64` for example to generate these keys
  - Change the port on the NGINX container if needed
2. Fetch the latest sources
  - `git submodule update --init --recursive`
  - `git --git-dir ./web/.git pull origin master`
  - `git --git-dir ./syncing-server/.git pull origin master`
3. Prepare the default extensions (optional)
  - `npm install --prefix ./web/public/extensions/batch-manager`
  - `npm install --prefix ./web/public/extensions/extensions-manager`
4. Deploy
  - `docker-compose build`
  - `docker-compose up -d`
