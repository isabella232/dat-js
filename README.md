# dat-js [![Travis](https://api.travis-ci.org/karissa/dat-js.svg)](https://travis-ci.org/karissa/dat-js)  [![NPM version](https://img.shields.io/npm/v/dat-js.svg?style=flat-square)](https://npmjs.org/package/dat)

A pure JavaScript browser-friendly api for using dat.

[Dat](http://datproject.org) is a decentralized tool for distributing data and files, built for scientific and research data. **dat-node** is a module to help you build node applications using Dat on the *file system*. For a Node.js api for working with dats on the filesystem, see [dat-node](http://github.com/datproject/dat-node).

Want to use Dat in the command line or an app (not build applications)? Check out:

* [Dat CLI](https://github.com/datproject/dat): Use Dat in the command line
* [Dat-Desktop](https://github.com/datproject/dat-desktop): A desktop application for Dat

#### Learn more! [docs.datproject.org](http://docs.datproject.org/) or [chat with us](https://gitter.im/datproject/discussions) ([#dat on IRC](http://webchat.freenode.net/?channels=dat))

## API

#### `var dat = new Dat([options])`

Creates a new dat object. The options passed here will be default for any dats created using the `add` method.

 * `options`: any options you can pass to [mafintosh/hyperdrive](https://github.com/mafintosh/hyperdrive) or [karissa/hyperdiscovery](https://github.com/karissa/hyperdiscovery). These options will become default for all dats.

#### `dat.add(key, [options], [onrepo])`

Adds a new dat with the given key. Joins the appropriate swarm for that key and begins to upload and download data. The `onrepo` function will be called when the dat is finished being created.

 * `options`: These options will override any options given in the Dat constructor.

### Properties

#### `dat.repos`

Array of repo instances

### Repo

The repo object managed by dat.

#### `repo.key`

The key of the repo

#### `repo.resume()`

Joins the swarm for the repository, beginning to find peers in the network to share with.

#### `repo.pause()`

Pause syncing. This disconnects from any peers currently syncing data with the repo.

#### `repo.destroy()`

Destroys the swarm and underlying database.

#### `repo.swarm`

Get to the original `discovery-swarm` instance, where the swarm can be managed.

#### `repo.archive`

Get to the original `hyperdrive archive` instance, where files can be managed using that api.

### Events

#### `repo`

Fired every time a new repo is ready.

#### `close`

Fired when dat is finished closing, including swarm and database.
