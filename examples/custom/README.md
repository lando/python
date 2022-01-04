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
# Should use the user specified version when set
lando ssh -s custom -c "python --version | grep 3.6."

# Should run on the custom port when specified
lando ssh -s custom -c "curl http://localhost:8000 | grep CUSTOMZ"

# Should run over ssl when specified
lando ssh -s customssl -c "curl https://localhost:443 | grep ANDTHEFUTURETO"
```

Destroy tests
-------------

Run the following commands to trash this app like nothing ever happened.

```bash
# Should be destroyed with success
lando destroy -y
lando poweroff
```
