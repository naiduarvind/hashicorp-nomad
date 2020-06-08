# Hashicorp Nomad

> A collection of dabbling with Hashicorp Nomad.

### Getting Started

1. Download the Hashicorp Nomad's binary client as per your OS distribution [here](https://www.nomadproject.io/downloads/)

2. Extract the binary and move it to your executable directory.
```
$ unzip nomad_${VERSION}_${OS_BINARY}_${OS_ARCH}.zip
$ mv nomad /usr/local/bin/nomad
```

3. Start the agent in dev mode as this will be running locally in your machine (not the recommended for production usage). 

```
$ sudo nomad agent -dev

# OSX users: make sure to blacklist the JVM driver to prevent the constant pop-up dialog box

$ sudo nomad agent -dev -config=osx-driver-blacklist
```

**Note:** Please run nomad agent as `sudo` since it uses operating system primitives for resource isolation which require elevated permissions.

4. Generate a skeleton `Job` for Nomad to schedule tasks.
```
$ nomad job init
```

**Note:** Jobs can be written in JSON which can be evaluated using Open Policy Agent in a pipeline as part of a guardrails mechanim.

5. Run the job and apply it for Nomad to schedule it.
```
$ nomad job run jobs/redis.nomad
```

6. Check the status of the job deployed by Nomad.
```
$ nomad status job redis
```