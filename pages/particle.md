# particle

The CLI for particle.io products

- call a function:
1) verify function is available with
`particle list`
2)
`particle call {{product_name}} {{function}} {{arg1,arg2}}`

- compile a source code file (in the cloud!):
`particle compile {{argon}} {{file.ino}}`

- flash a source code file (compilation happens in the cloud!):
`particle flash {{product_name}} {{file.ino}}`
even after the command line says it's flashed, wait until the device looks normal again, might take some time.

- serial output: https://docs.particle.io/tutorials/device-os/usb-serial/
