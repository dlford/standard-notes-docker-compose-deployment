# Standard Notes Docker Compose Deployment

I didn't like that there were no official Docker images for the Standard Notes
front-end or back-end, so I decided it was best to set up a repository to build
the Docker images from source and deploy them with Docker Comopse.

There is also a GitLab CI configuration, which I set up to run on a schedule to
keep the deployment up to date.

## How to use this repository

1. Set up the environment

- Edit the `.env` file, or set up all variables from `.env` in your CI/CD solution.
- Change all the variables that are random strings, use `openssl rand -hex 32` to generate values

2. Fetch the latest sources

- `git submodule update --init --recursive`
- `git --git-dir ./web/.git pull origin master`

3. Prepare the default extensions (optional)

- `npm install --prefix ./web/public/extensions/batch-manager`
- `npm install --prefix ./web/public/extensions/extensions-manager`

4. Deploy

- `docker-compose build`
- `docker-compose up -d`
