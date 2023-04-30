# LCARS-ExpressJS
An Express.js and EJS implementation of the LCARS interface implemented  by Jim Robertus @ https://www.thelcars.com/

It's currently a lot of ESJ so far and the biolerplate Express. Some data is getting passed between pages using strings in the templates. Eventually, the Express middleware will read json data out of tiles, to pass into the templates.

About me: I'm learning ExpressJS and EJS for work.

## Initial Setup if not cloning the repository:

- This requires Node.JS npm and the express Generator
    > npm install -g express
    > express --view=ejs LCARS-ExpressJS
- If planning on cloning this repository:
    > git clone https://github.com/jeffcaradona/LCARS-ExpressJS.git
## After cloning:

1. Change directory:
    > cd LCARS-ExpressJS

2. Install dependencies:
    > npm install

3. Run the app from windows command prompt:
    > SET DEBUG=LCARS-expressJS:* & npm start
4. Run the app from windows power shell:    
    > $env:DEBUG='LCARS-ExpressJS:*'; npm start
5. Browse to http://localhost:1701/
## Building a docker image:

1. Create a builder using Docker buildx:
    > docker buildx create --name mybuilder
2. Switch to the new builder
    > docker buildx use mybuilder
3. Inspect the builder
    > docker buildx inspect --bootstrap
4. Build the container image with extra platform support and push it to Docker Hub
    > docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 -t [docker.hub.id]/lcars-expressjs:latest --push .
5. Inspect the image
    > docker buildx imagetools inspect itsgreyspot/lcars-expressjs:latest
6. Test the image
    > docker run -p 49160:1701 -d [docker.hub.id]/lcars-expressjs