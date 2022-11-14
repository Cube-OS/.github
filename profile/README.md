<!--

## Hi there 👋

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

# Cube-OS

Cube-OS is an OpenSource Linux based operating system and framework for CubeSats and other satellites. (based on [KubOS](https://github.com/kubos))

On this page you find all the repositories you need to run your own satellite.

[More Documentation can be found here](https://github.com/Cube-OS)

## Cube-OS SDK
Please follow the instructions provided in the repository to install the Cube-OS SDK

[cubeos-dev](https://github.com/Cube-OS/cubeos-dev)
<!-- *insert missing links*
 -->
## Cube-OS framework
[cubeos-service](https://github.com/Cube-OS/cubeos-service)  
API for Services on Cube-OS. Please read the README file before making your own code.  
  
[system-api](https://github.com/Cube-OS/system-api)  
Helper API for performing various general system actions

[cubeos-error](https://github.com/Cube-OS/cubeos-error)  
Error handling for Services on Cube-OS 

### HAL
I2C
[rust-i2c](https://github.com/Cube-OS/rust-i2c) 

UART
[rust-uart](https://github.com/Cube-OS/rust-uart) 

UDP
[rust-udp](https://github.com/Cube-OS/rust-udp) 

SPI
!!!TODO

<!-- *insert missing links*
 -->
## Cube-OS Payload APIs, Services and Apps
[example-api](https://github.com/Cube-OS/example-api)

[example-service](https://github.com/Cube-OS/example-service)

[example-app](https://github.com/Cube-OS/example-app)
<!-- *insert missing links* -->

## Compile your service (requires rust 1.55.0 or above)
As shown above, **cubeos-service** uses features so the user can decide the use case at compile time.

**UDP handling**

`cargo build`

or with cross compiler

`cargo kubos -c build --target kubos-linux-isis-gcc -- --release` (requires KubOS SDK)


**Ground:**

`cargo build --features ground`

Additionally the UDP handling and Ground features can be combined with **debug**, e.g.:
`cargo build --features debug`
`cargo build --features ground,debug`

## Run a service
To run a service simply transfer the executable to the satellite or ground station to a desired folder (e.g. /home/kubos/) and run:

`./executable`

This requires a config file `/etc/kubos-config.toml`. Alternatively run the executable with the -c flag to specify a config file:

`./executable -c path/to/config`

## Troubleshooting
CubeOS uses git ssh URL's for dependencies within the Organisation. Pls make sure to add your to the repository:

**start ssh-agent**
```` eval `ssh-agent` ````

**add key (in repo)**
`ssh-add ~/.ssh/$your-key`
e.g. ssh-add ~/.ssh/id_rsa
