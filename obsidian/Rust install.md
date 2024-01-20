```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
package manager: Cargo

```
Rustup metadata and toolchains will be installed into the Rustup

home directory, located at:


  /Users/feng/.rustup


This can be modified with the RUSTUP_HOME environment variable.
  

The Cargo home directory is located at:

  

  /Users/feng/.cargo

  

This can be modified with the CARGO_HOME environment variable.

  

The **cargo**, **rustc**, **rustup** and other commands will be added to

Cargo's bin directory, located at:

  

  /Users/feng/.cargo/bin

  

This path will then be added to your **PATH** environment variable by

modifying the profile files located at:

  

  /Users/feng/.profile

  /Users/feng/.bash_profile

  /Users/feng/.zshenv

  

You can uninstall at any time with **rustup self uninstall** and

these changes will be reverted.
```

cargo --version