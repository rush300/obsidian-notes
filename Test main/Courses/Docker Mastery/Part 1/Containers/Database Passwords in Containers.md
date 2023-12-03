

We all know databases usually need passwords, but since the dawn of Docker, the postgres image (and a few others like redis) has allowed you to do a simple `docker run` on it and it starts without a password. Sure you could set a password but it didn't require one.

**In Feburary 2020** [**that changed**](https://github.com/docker-library/postgres/issues/681)**,** and will affect using postgres in this course (and my others). **When running postgres now, you'll need to either set a password, or tell it to allow any connection** (which was the default before this change).

For `docker run`, and the forthcoming Docker Compose sections, you need to either set a password with the environment variable:

`POSTGRES_PASSWORD=mypasswd`

Or tell it to ignore passwords with the environment variable:

`POSTGRES_HOST_AUTH_METHOD=trust`

Note this change was in the Docker Hub image, and not a change in postgres itself.

Also note if I or you were pinning versions, as we should, this wouldn't have surprised us. I tend to only pin to the minor version **in this course** (9.6) rather than the patch version (9.6.16) to keep you a bit more secure in the course. In the real world, I always pin my production apps to the patch version. It's the only safe way to operate. By pinning to the minor version in the courses, I prevent any major changes from breaking the course (in theory ha ha), yet also ensure you're running the latest patches (which would fix any bugs or security problems). In this, *very rare case*, the maintainer of the official postgres decided to introduce a breaking change in the *image* to a patch release of the app. The two aren't related, and it kinda shows off a weakness of the Docker Hub model... that there is no version of the Docker Hub image really, it's just tracking the upstream postgres versions... so then if any Docker Hub change would break something, it can't easily be tracked as a separate version from the app itself. Oh well, just remember to always pin the whole image version for things you care about.

**I've updated the course repo files to indicate this change, but if you've cloned the repo before February 18th, 2020, you will need to update or replace your clone.**