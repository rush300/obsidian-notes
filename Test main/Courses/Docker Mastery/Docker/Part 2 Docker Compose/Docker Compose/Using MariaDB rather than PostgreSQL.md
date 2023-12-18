
Throughout this course, I will give you many database examples and assignments. Some are MySQL, and some are Postgres. There have been various issues over time when using those in this course, including:

  

- MySQL doesn't always have an arm64 image version (Apple Silicon, M1/M2/etc. and Raspberry Pi's)
    
- Postgres isn't easily supported in [newer Drupal versions](https://www.drupal.org/docs/system-requirements/database-server-requirements).
    

For those reasons, I recommend you check out [MariaDB](https://hub.docker.com/_/mariadb), which is a fork of MySQL that has proper arm64 versions and also is better supported in recent Drupal versions.

For the next assignment, I recommend replacing Postgres with MariaDB, and the only other thing to change would be the environment variables like:

1. MARIADB_ROOT_PASSWORD
2. MARIADB_DATABASE
3. MARIADB_USER
4. MARIADB_PASSWORD

These videos are in line to get updated to reflect this recommendation.