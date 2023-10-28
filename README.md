# Maps UI with Road Safety: Repo for the System

This repo contains the code of the system used for a user study on Maps UI with Road Safety. Frontend and backend are included as git submodules. For original repos, check out [frontend repo](https://github.com/alicia-lyu/road-safety-ui.git) and [backend repo](https://github.com/alicia-lyu/graphhopper-for-safety.git) respectively.

Both repos are based on open-source repos of graphhopper ([graphhopper](https://github.com/graphhopper/graphhopper) and [graphhopper-maps](https://github.com/graphhopper/graphhopper-maps)).

## How to run the system locally

First, ensure you have [a public SSH key added to your GitHub account](https://docs.github.com/en/github-ae@latest/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). We are going to use SSH to clone submodules.

In desired directory, clone this repository and pull submodules by running

```
git clone https://github.com/alicia-lyu/road-safety.git
git submodule update --init
```

At anytime during your usage of this code base, you need to keep an eye on whether there is a new release of the submodules. Just `cd` into each of the two submodules and run `git pull` beforehand.

### First, host the backend on your machine

Prerequisites:

1. [JDK 17+](https://www.oracle.com/java/technologies/downloads/)
2. [Maven](https://maven.apache.org/install.html)
3. Git
4. wget

Run the following commands

```
cd graphhopper-for-safety
make ${STATE}
```

Replace `${STATE}` with the state you want to do routing in. Any state in the continental US is automatically enabled. This will first retrieve `${STATE}-latest.osm.pbf`, if not already present. Then maven will compile the code and build the application. 

Note that if you recently changed `${STATE}`, cache will be removed and it takes longer to start the application.

Once it's done, you can check whether the backend is running on [http://localhost:8989](http://localhost:8989). You may need to refresh to zoom into the correct area. Note that we have a separate UI for user study, and this built-in UI is only for previewing purposes.

### Second, run the frontend

Prerequisites:

1. [Node.js](https://nodejs.org/en)
2. [NPM](https://www.npmjs.com/package/npm)

Run the following commands

```
cd road-safety-ui
npm install
npm run serve
```

Now, you can visit [http://localhost:3000](http://localhost:3000) and our interface will be running there!