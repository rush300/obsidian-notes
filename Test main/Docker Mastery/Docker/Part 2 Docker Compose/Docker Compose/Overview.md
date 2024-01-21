In 2022, Docker announced the General Availability of Docker Compose V2.

It supports all the same commands taught in this course and is meant to be fully backward compatible. It's auto-installed by Docker Desktop.

All you need to do is simply remove the dash from your Docker Compose commands:

`docker-compose up` becomes `docker compose up`, etc.

Behind the scenes, Docker has rebuilt the old docker-compose Python binary with go, the same language as the Docker CLI, and added Compose V2 as a CLI plugin rather than a separate command. It's now faster and more stable, and should "just work" as a drop-in replacement for the V1 docker-compose CLI.

**So anywhere in this course that I type** `**docker-compose**`**, just replace that with** `**docker compose**`**!**

Remove all
```bash
sudo docker compose down --rmi all --volumes

```

## Version Dependencies in Multi-Tier Apps

#### App versions in Docker

Now that you're learning Docker Compose for managing multi-container apps, it's important to remember that every app with dependencies, will also have _version requirements_ for those dependencies.

If you add an app and a database to a Compose file, then that app is going to have specific database versions it is compatible with.

Version dependencies aren't new, so they aren't technically a Docker thing, but we _*do*_ use Docker and Compose to control versions of apps like Drupal, PostgreSQL, MySQL, Redis, Wordpress, etc.

Therefore, when building your `Dockerfile` and `docker-compose.yml` file, remember that you'll need to check the compatible versions in that apps documentation.

#### Coming up

In the next few Assignments, you'll be using a Drupal web server with a compatible database server. For this course, I pick specific versions of these dependencies so they are certain to work together. I've done the research and found which versions work together through reading and testing.

You may need to do the same, especially if you want to use versions together that I haven't tested.  I will often leave old versions in this course (as long as they still work) for several reasons:

1. During your career, you'll be running lots of old versions of apps. It's worthwhile learning about how various app versions work together with other apps.   
2. Learning "the latest version of every sample app" isn't the focus of this course, but rather how to manage _*any*_ versions of an app in Docker and Kubernetes.

#### Drupal changes

Due to recent breaking changes in Drupal, be sure you're using the below versions in docker commands and YAML, so that it'll work as expected. While a lecture video might show a slightly older version, know that any code examples and answer files in the course repository have been updated to reflect these versions:

1. drupal:9
2. postgres:14

Now let's build some Compose files!