# application-my-very-first-test

This application is based on a tutorial on [titl example-python](https://docs.tilt.dev/example_python.html) page.


## How to set the dev environment

1. Install prerequisites (docker, kind, kubectl, ctlptl), described on [tilt install page](https://docs.tilt.dev/install.html)

2. Start cluster:
```shell
ctlptl apply -f ctlptl_config.yaml
```
3. start tilt
```shell
tilt up
```
4. Enjoy online development possibilities!
