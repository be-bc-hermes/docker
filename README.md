# Authentication

- create PAT (Personal Access Token) with permissions:
	- read:packages
	- write:packages
	- delete:packages

- save PAT as environment variable
	> `echo "export CR_PAT=<PAT>" >> ~/.bachrc`

- authenticate with Github Registry
	> `echo $CR_PAT | docker login ghcr.io -u <USERNAME> --password-stdin`


# Publish to Github Registry

- Commit current state of the repository to an image
	> `docker commit -a "<AUTHOR>" -m "<MESSAGE>" <CONTAINER> <REPOSITORY:TAG>`
	> example:
	> `docker commit -a "emin" -m "Add product price change exchange, queue and binding" rabbitmq ghcr.io/be-bc-hermes/rabbitmq:1.0.0`

- Tag image with 'latest' if it is stable
	> `docker tag ghcr.io/be-bc-hermes/rabbitmq:<VERSION> ghcr.io/be-bc-hermes/rabbitmq:latest`

- Push versions
	> `docker push ghcr.io/be-bc-hermes/rabbitmq:<VERSION>`
	> `docker push ghcr.io/be-bc-hermes/rabbitmq:latest # if stable`
