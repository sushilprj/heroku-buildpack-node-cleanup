# Heroku Buildpack: Node Cleanup

The maximum allowed Heroku slug size (after compression) is 300MB. Image-heavy apps can somethings butt up against this limit, especially when using multiple buildpacks.

If you're using Node.js to compile your front-end assets, but not to run your app, you may be able to save a large amount of space by deleting the `node_modules` directory before slug compilation.

## Usage

First, set the Node.js buildpack to compile your assets:

```bash
$ heroku buildpacks:set heroku/nodejs
```

Next, add the Node Cleanup buildpack to get rid of the `node_modules` directory:

```bash
$ heroku buildpacks:set --index 1 https://github.com/istrategylabs/heroku-buildpack-node-cleanup
```

Finally, add whichever buildpack runs your app:

```bash
$ heroku buildpacks:set --index 2 heroku/python
```

## Documentation

For more general information about buildpacks on Heroku:

- [Using Multiple Buildpacks for an App](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app)
- [Slug Compiler](https://devcenter.heroku.com/articles/slug-compiler)
