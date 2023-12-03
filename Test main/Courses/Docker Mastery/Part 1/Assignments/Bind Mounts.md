## Edit Code Running In Containers

- Use a Jekyll "Static Site Generator" to start a local web server
- Don't have to be web developer: this is example of bridging the gap between local file access and apps running in containers
- source code is in the course repo(udemy-docker-mastery/) under /bindmount-sample-1
- We edit files with editor on our host using native tools
- Container detects changes with host files and updates web server
- start container with 
```bash
docker run -p 80:4000 -v $(pwd):/site bretfisher/jekyll-serve
```
- Refresh our browser to see changes
- Change the file in _posts\ and refresh browser to see changes

```bash
docker run -p 80:4000 -v $(pwd):site bretfisher/jekill-serve


```