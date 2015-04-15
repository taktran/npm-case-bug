# npm case bug

Replication of the bug for https://github.com/npm/npm/issues/7933

## Development

To see the bug, run

    npm install

Should get something like

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

Running it a second time installs everything.