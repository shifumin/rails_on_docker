Rails on Docker
=====
Template for building rails application development environment on Docker.

## Operation Environment

- Docker version 17.09.0-ce
- docker-compose version 1.16.1
- docker-machine version 0.12.2

## Stack

- Rails 5.1 (+ Ruby 2.4.2)
- Mysql 5.7

## Readying

```
$ docker pull ruby:2.4.2
$ docker pull mysql:5.7
```

```
$ git clone https://github.com/shifumin/rails_on_docker
$ cd rails_on_docker
```

## Usage

```
# rails new
$ docker-compose run --rm web rails new . --database=mysql --skip-bundle --skip-test

# after `rails new`, you need to replace `config/database.yml`
$ cp database.yml.sample config/database.yml

# bundle install
$ docker-compose run --rm web bundle install

# rails g
# the following is examples
$ docker-compose run --rm web rails g rspec:install
$ docker-compose run --rm web rails g controller welcome index
$ docker-compose run --rm web rails g model user name:string

# rake db
$ docker-compose run --rm web rake db:create
$ docker-compose run --rm web rake db:migrate

# create and start containers
# boot the app (= `rails s`)
$ docker-compose up

# stop and remove containers
$ docker-compose down

# build or rebuild services
# (e.g.: after changing Gemfile or Dockerfile)
$ docker-compose build  # or `docker-compose up --build`
```
