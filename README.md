# k8s-training

The objective of the project was to deploy a static website using nginx, docker and aws eks

**Steps to build and push the Docker image.**
    1. Navigate to the parent directory "k8s-training"
    2. Run `docker build -t \<build-name> -f website/Dockerfile`
    3. Then tag the build with `docker tag \<build-name> \<docker-user>/\<docker-repo>:\<tag-if-multiple-images>`
    4. Lastly, push `docker push \<docker-user>/\<docker-repo>:\<previously-defined-tag>`

**Instructions to apply Kubernetes manifests.**
    1. Navigate to k8s-training/k8s and run `kubectl apply -k .` - this will run the kustomization.yml file 

**Configuration details for NGINX.**
    The initial config file is simple. Location referring to where the html was saved during the build of the container. Port 90 is specified, as I thought it would help me to understand more which port is which in each of the manifest files. (which it did xo)

**Verification steps to access the deployed website via the external IP or DNS name.**
    The External IP, is the same as the aws dns which is the following;
    http://abdbc678b5bda4e618bea4929672ac77-303979073.eu-west-1.elb.amazonaws.com/

**Any challenges faced and how they were overcome.**
    Understanding the unspoken "build context" of docker build command. I thought it was just enough to put a relative port in my Dockerfile, pointing to the nginx.conf. This however was not enough, due to the build context being initially inside of only the website folder. Once I understood the build context, it was easy to understand how to reference the files to copy inside the Dockerfile, and how to call upon multiple different Dockerfiles inside of one context.
