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

## Cube-OS framework
[cubeos-service](https://github.com/Cube-OS/cubeos-service)  

API for Services on Cube-OS. Please read the README file before making your own code.  

## Cube-OS Payload APIs, Services and Apps + Interactions
Here's an example how to write an API, Service and App for your Payload or Subsystem.

The API describes how the OBC interacts with the payload.

[example-api](https://github.com/Cube-OS/example-api)

The Service can be compiled for use on the satellite and as a ground station twin. On the satellite the service allows Apps and the satellite controller on the ground to interact with the payload. The ground station twin enables the communication with the satellite service by translating JSON commands from the command line interface to UDP commands.

[example-service](https://github.com/Cube-OS/example-service)

The App enables autonomy on the satellite. During the mission the controller will schedule Apps for execution to run payloads autonomously in orbit.

[example-app](https://github.com/Cube-OS/example-app)

The command line interface (CLI) enables the user to send commands and receive telemetry from the satellite.
 
[cli](https://github.com/Cube-OS/cli)

The WebApp is a graphical version of the CLI.

!!!TODO

## Compile your service (requires rust 1.69.0 or above)
As shown above, **cubeos-service** uses features so the user can decide the use case at compile time.

**UDP handling**

`cargo build`

or with cross compiler

!!!!! NEW !!!!!

Use [cross](https://github.com/cross-rs/cross) which makes the SDK obsolete. Once set up use as follows:

OBC: `cross build --release --target=armv5te-unknown-linux-gnueabi`

BBB: `cross build --release --target=arm-unknown-linux-gnueabihf`

PI: `cross build --release --target=armv7-unknown-linux-musleabihf` (WARNING NOT TESTED)

------- OLD WAY (with SDK) --------

OBC: `cargo kubos -c build --target kubos-linux-isis-gcc -- --release` (requires KubOS SDK)

BBB: `cargo kubos -c build --target kubos-linux-beaglebone-gcc -- --release` (requires KubOS SDK)

**terminal:**

`cargo build --features terminal`

Additionally the UDP handling and terminal features can be combined with **debug**, e.g.:

`cargo build --features debug`

`cargo build --features terminal,debug`

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

e.g. ssh-add ./.ssh/id_rsa, or ssh-add .ssh/id_ed25519
