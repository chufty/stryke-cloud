## Stryke: DevOps Tooling

For now it's just a dockerfile to run Jenkins. Build the image with this:

`docker build -t chufty/stryke-jenkins .`

Then boot the container, for example:

`docker run -u root --rm -d -p 8080:8080 -p 50001:50000 -v jenkins-data-2:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock chufty/stryke-jenkins`