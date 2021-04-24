# [kcal](https://github.com/kcal-app/kcal) for Docker!

[![Docker build status](https://img.shields.io/docker/cloud/build/kcalapp/kcal)](https://hub.docker.com/r/kcalapp/kcal/builds)
[![Docker version](https://img.shields.io/docker/v/kcalapp/kcal?sort=semver)](https://hub.docker.com/r/kcalapp/kcal/tags?page=1&ordering=last_updated)
[![Docker pulls](https://img.shields.io/docker/pulls/kcalapp/kcal)](https://hub.docker.com/r/kcalapp/kcal)
[![Docker image size](https://img.shields.io/docker/image-size/kcalapp/kcal)](https://hub.docker.com/r/kcalapp/kcal/tags?page=1&ordering=last_updated)

# :construction: **WORK IN PROGRESS** :construction:

This is a template repository for running [kcal](https://github.com/kcal-app/kcal)
with Docker Compose. Visit the main [kcal](https://github.com/kcal-app/kcal) repository
for more information about the application.

## 1. Clone

Clone this repo.

    git clone https://github.com/kcal-app/kcal-docker.git

## 2. Create `.env` file.

    cd kcal-docker
    cp .env.example .env

## 3. Generate and add an `APP_KEY` to the `.env` file.

    docker-compose run app php artisan key:generate --show

This command will output a suitable key. Copy the key value and add it to the
`APP_KEY` value in the `.env` file. This also a good time to review make other
changes to the `.env` file (e.g. set the `APP_TIMEZONE` and `APP_URL` values as
desired).

## 4. Launch! :rocket:

    docker-compose up -d

## 5. Set up application.

    docker-compose exec app php artisan optimize
    docker-compose exec app php artisan migrate
    docker-compose exec app php artisan elastic:migrate

## 6. Create initial user.

    docker-compose exec app php artisan user:add --admin