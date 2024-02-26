# Rust Backdoors

This repository contains bind and reverse shells implemented in Rust programming language. The bind shell serves as a simple multithreaded server providing bash sessions, while the reverse shell establishes a connection to a specified location and provides a bash shell. To compile and use these shells, you need to [install Rust](https://www.rust-lang.org/tools/install).

## Bind Shell

To utilize the bind shell, clone the repository and navigate to the `bind-shell` directory. For a quick test, execute the `cargo run` command, which will start a bind shell on port 4444 by default. You can verify its functionality using tools like netcat (`nc localhost 4444`) or any preferred programming language. Upon establishing a TCP connection, you will be presented with a shell session on your local machine:

![Rust bind shell example.](https://i.imgur.com/WwkbYUd.png "Rust bind shell example.")

_Note: `ncat` is a newer version of the standard `nc`, but functions the same here._

To change the listening port, modify the code in `main.rs`. _Additionally, the implementation for handling multiple connections requires improvement._

## Reverse Shell

To use the reverse shell, clone the repository and navigate to the `reverse-shell` directory. For testing, set up a netcat listener in one terminal (`nc -lvp 4444`) and execute the program in another terminal (`cargo run`):

![Rust reverse shell example.](https://imgur.com/QxRj8dj.png "Rust reverse shell example.")

_Ensure to specify port 4444 for it to function out of the box._

To connect to a different location, replace `"localhost:4444"` with the desired connection string (IP address, hostname, etc.).

## Application in Ethical Scenarios

While I won't lecture on the misuse of these shells, it's crucial to prioritize ethical use.

In ethical scenarios, you'd likely use the compiled binary rather than the entire Rust project. For Rust newcomers, compiling a release binary is straightforward:

```bash
cargo build --release
```

To use:

1. Navigate to the shell directory.
2. Modify the code as necessary.
3. Run `cargo build --release`.
4. Copy the generated binary to the desired location.
5. Execute the binary.

Example:

```bash
git clone https://github.com/LukeDSchenk/rust-backdoors.git

cd rust-backdoors/bind-shell     # or rust-backdoors/reverse-shell

# Modify code as needed

cargo build --release
cp target/release/bind-shell new_dir/new_name  # or target/release/reverse-shell

cd new_dir
./new_name
```

Wishing you the best in your ethical endeavors, and may these shells facilitate learning.
