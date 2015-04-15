# npm case bug

Replication of the bug for https://github.com/npm/npm/issues/7933

Basically, `node-hue-api` has `"parseUri": "~1.2.3-2"` as a dependency, and `socket.io-client` has `"parseuri": "0.0.2"` as a dependency. `parseUri` vs `parseuri`.

## Development

To see the bug, run

    npm install

Depending on which dependency is installed, I get one of the two errors

1) `node-hue-api` installed first

    $ npm install
    npm ERR! Darwin 12.5.0
    npm ERR! argv "node" "/usr/local/bin/npm" "install"
    npm ERR! node v0.10.32
    npm ERR! npm  v2.7.6

    npm ERR! version not found: parseuri@0.0.4
    npm ERR!
    npm ERR! If you need help, you may report this error at:
    npm ERR!     <https://github.com/npm/npm/issues>

    npm ERR! Please include the following file with any support request:
    npm ERR!     /Users/.../npm-case-bug/npm-debug.log

2) `socket.io-client` installed first

    $ npm install
    |
    > ws@0.4.31 install /Users/.../npm-case-bug/node_modules/socket.io-client/node_modules/engine.io-client/node_modules/ws
    > (node-gyp rebuild 2> builderror.log) || (exit 0)

      CXX(target) Release/obj.target/bufferutil/src/bufferutil.o
      SOLINK_MODULE(target) Release/bufferutil.node
      SOLINK_MODULE(target) Release/bufferutil.node: Finished
      CXX(target) Release/obj.target/validation/src/validation.o
      SOLINK_MODULE(target) Release/validation.node
      SOLINK_MODULE(target) Release/validation.node: Finished
    npm ERR! Darwin 12.5.0
    npm ERR! argv "node" "/usr/local/bin/npm" "install"
    npm ERR! node v0.10.32
    npm ERR! npm  v2.7.6
    npm ERR! code ETARGET

    npm ERR! notarget No compatible version found: parseuri@'>=1.2.3-2 <1.3.0'
    npm ERR! notarget Valid install targets:
    npm ERR! notarget ["0.0.1","0.0.2","0.0.3","0.0.4"]
    npm ERR! notarget
    npm ERR! notarget This is most likely not a problem with npm itself.
    npm ERR! notarget In most cases you or one of your dependencies are requesting
    npm ERR! notarget a package version that doesn't exist.
    npm ERR! notarget
    npm ERR! notarget It was specified as a dependency of 'node-hue-api'
    npm ERR! notarget

    npm ERR! Please include the following file with any support request:
    npm ERR!     /Users/.../npm-case-bug/npm-debug.log

Running `npm install` a second time installs everything ok.