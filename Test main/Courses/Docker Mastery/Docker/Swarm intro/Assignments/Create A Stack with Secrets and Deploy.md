- Let's use our Drupal compose file from last assignment
	- (Compose-assignment-2)
- Rename image back to official drupal:8.2
- Remove build:
- Add secret via external:
- use environment variable POSTGRES_PASSWORD_FILE
- Add secret via cli echo `"<pw>"` | docker secret create psql-pw -
- Copy compose into a new yml file on your Swarm node1

Create the secret:
`echo "mypasswd" | docker secret create psql-pw - `
```yml
version: '3.1'

services:
	drupal:
		image: drupal
		ports:
			- "8080:80"
		volumes:
			- drupal-modules:/var/www/html/modules
			- drupal-profiles:/var/www/html/profiles
			- drupal-sites:/var/www/html/sites
			- drupal-themes:/var/www/html/themes
	postgres:
		image: postgres
		environment:
			- POSTGRES_PASSWORD=/run/secrets/psql-pw
		secrets:
			- psql-pw
		volumes:
			- drupal-data:/var/lib/postgresql/data

volumes:
	drupal-modules:
	drupal-profiles:
	drupal-sites:
	drupal-themes:
	
secrets:
	psql-pw:
		external: true
```
On node1:
```bash
docker stack deploy -c docker-compose.yml drupal
```
