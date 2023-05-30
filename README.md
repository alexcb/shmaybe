## shmaybe

shmaybe is a retry wrapper that calls a user-supplied command and retries the command if it fails.

### Usage

    shmaybe <command> <arg> ...

### Example

An example of running a custom python script that will randomly fail 75% of the time:

    ./shmaybe python3 -c 'import random; import sys; x=random.randint(0,4); print("pass") if x==0 else print("fail"); sys.exit(x)'

Which will output:

    fail
    (1/5) command failed with exit code 2; sleeping for 1
    fail
    (2/5) command failed with exit code 3; sleeping for 2
    pass

### Environment Variables

#### `MAX_ATTEMPTS`

Controls the maximum number of attempts before permanently failing; defaults to 5.

#### `SLEEP_SECONDS`

Controls the number of seconds to sleep before retrying; defaults to 1.

#### `EXPONENTIAL_BACKOFF`

Enables or disables the exponential backoff retry mechanism; defaults to true.

When enabled, the `SLEEP_SECONDS` value is doubled between retries.

### License

shmaybe is free and unencumbered software released into the public domain; see [Unlicense](Unlicense) for details.

