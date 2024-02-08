# PGBIN-BUILD

## Creating a Build Environment on el8 or el9

1. First, set up a CLI environment to be able to test. You can refer to the [pgEdge CLI repository](https://github.com/pgEdge/cli).

2. Change the ownership of the `/opt` directory to be `$USER:$USER` so you can write there.

```bash
sudo chown -R $USER:$USER /opt
```

From the /opt directory, clone the pgbin-build repository:

```bash
git clone https://github.com/pgedge/pgbin-build
```

The BLD and IN environment variables are set up in your .bashrc from step #1 installing the CLI.

Configure your ~/.aws/config credentials for access to s3://pgedge-xxxxxxxx/IN.

In the setup directory, run the 1-pgbin-build.sh script to set up all compilation tools needed.

In the setup directory, run the 2-pull-IN.sh script to pull in all the source binaries into the IN directory structure.

Navigate to the $BLD directory:

```bash
cd $BLD
```
a) Run ./sharedlibs.sh the first time and each time you do incremental PostgreSQL releases (after dnf update).

b) Run the following commands to confirm the environment:

```bash
./build-all-pgbin.sh 16
./build-all-components.sh spock32 16
```

c) Execute build-scripts as necessary and maintain IN directory binaries via push & pull scripts
