# Standard Notes Docker Compose Deployment

Full stack Standard Notes deployment including the web app, and an NGINX reverse proxy to put the syncing server at the `/api` route so you only need one hostname.

There is also a GitLab CI configuration, which I set up to run on a schedule to
keep the deployment up to date.

## How to use this repository

1. Set up the environment

- Copy the `example.env` file to `.env`, or set up all variables from `example.env` in your CI/CD solution (take a look at `.gitlab-ci.yml` for hints, note that `.env` file must exist but can be empty if getting varaibles from CI).
- Change all the variables that are random strings, use `openssl rand -hex 32` to generate values

2. Fetch the latest sources

- `git submodule update --init --recursive`
- `git --git-dir ./web/.git pull origin main`

3. Prepare the default extensions (optional)

- `npm install --prefix ./web/public/extensions/batch-manager`
- `npm install --prefix ./web/public/extensions/extensions-manager`

4. Deploy

- `docker-compose build`
- `docker-compose up -d`
