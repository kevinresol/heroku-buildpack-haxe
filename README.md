# heroku-buildpack-haxe

Heroku Buildpack for Haxe

Allows you to use the following commands in your scripts:

- `haxe`
- `haxelib`
- `neko`

Use config var `HAXEVER` and `NEKOVER` to specify the version of Haxe and Neko respectively.

Currently, the defaults are 3.3.0-rc.1 and 2.1.0 respectively.

### Example Usage

The following demonstrate the use of the hooks in `package.json` to invoke a Haxe build for a NodeJS project:

0. Config the following buildpacks in heroku dashboard (or through command line)

  - `https://github.com/kevinresol/heroku-buildpack-haxe`
  - `heroku/nodejs`
	
0. Add a pre/postinstall hook in your `package.json`
```javascript
"scripts": {
    "start": "node server.js",
    "postinstall": "haxelib install hxnodejs && haxe server.hxml"
  }
```