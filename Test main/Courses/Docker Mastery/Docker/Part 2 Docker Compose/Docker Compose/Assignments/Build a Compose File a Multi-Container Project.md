- Build a basic compose file for a Drupal content management system website. Docker Hub is your friend
- Use the drupal image along with the postgres image
- Use ports to expose Drupal on 8080 so you can localhost:8080
- Be sure to set POSTGRES_PASSWORD for postges
- Walk though Drupal setup via browser
- Tip: Drupal assumes DB is localhost, but it's service name
- Extra Credit: Use volumes to store Drupal unique data

Create directory compose-assignment-2, open with
```bash
code .
```
```yml
version: '2'

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
			- POSTGRES_PASSWORD=mypasswd

volumes:
	drupal-modules:
	drupal-profiles:
	drupal-sites:
	drupal-themes:
```

