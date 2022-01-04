Python Example
==============

This example exists primarily to test the following documentation:

* [Python Service](https://docs.devwithlando.io/tutorials/python.html)

Start up tests
--------------

Run the following commands to get up and running with this example.

```bash
# Should start up successfully
lando poweroff
lando start
```

Verification commands
---------------------

Run the following commands to validate things are rolling as they should.

```bash
# Should use 2.7 as the default version
lando ssh -s defaults -c "python --version 2>&1" | grep "2.7."

# Should use the user specified patch version when set
lando ssh -s patch -c "python --version 2>&1" | grep "2.7.14"
```

Destroy tests
-------------

Run the following commands to trash this app like nothing ever happened.

```bash
# Should be destroyed with success
lando destroy -y
lando poweroff
```
