1. According to the Pipit repository [1] Pipit requires F* and Karamel for generating C code. Pipit uses opam, the OCaml package manager 
   1. opam does is not available for Windows 
2. Using WSL to run Linux [3]
   1. Create a folder where I want to create the local dev environment
   2. To open the folder on VSCode on my local machine:
      1. [2] Using the "From the WSL terminal" option
3. Clone the Pipit repository [1] in the folder 
4. Create an SSH Key for Github authentication/permission to get the fstar and Karamel dependencies
   1. To generate the public/private rsa key pair: `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` 
   2. To add the SSH private key to the ssh-agent: `ssh-add ~/.ssh/id_rsa`
   3. Add the public ssh key `id_rsa.pub` to Github
5. Install the following dependencies that will be required later
   1. `sudo apt-get install libgmp-dev`
   2. `sudo apt-get install python3-distutils`
6. Enter the `pipit` folder in the respository
7. To setup an OPAM environment: Run `opam init`
8. To intialise a local development environment: Run `make dev-init`. It runs the following commands:
```sh
     # Make sure the opam index is up-to-date
     opam update

     # Create a local opam switch with OCaml 4.14
     opam switch create . 4.14.1

     # Initialise git submodules (FStar and Karamel)
     git submodule update --init

     # Tell opam to use the development version of F* but don't install it yet
     opam pin add fstar file://submodules/FStar --no-action

     # Tell opam where to find the local repo for Karamel and install it and F*
     opam pin add karamel file://submodules/karamel --yes
```
- Issues faced here:
    - Failed checksum for both the Ftar and Karamel repos
        - `error 67: Checksum specified with a non archive url:"https://github.com/FStarLang/karamel/archive/refs/tags/v1.0.0.zip -`
        - But pinning seems to be a temporary solution
    - Due to missing dependencies, had to remove existing opam switch `opam switch remove /home/mifta/PipitExploration/pipit` and start from step 7 again. 
              
1.  Add the directory containing `fstar.exe` to the `PATH` environment variable. Adding `fstar.exe` to your PATH environment variable in the `.bashrc file` makes the F* compiler executable accessible from any terminal session without needing to specify its full path. This  allows you to run F* commands simply by typing `fstar.exe yourFile.fst` instead of the full path to fstar.exe every time you want to use it.
   1. `nano ~/.bashrc`
   2. At the end of the file, add: `export PATH="/home/mifta/PipitExploration/pipit/_opam/bin:$PATH"`
2.  Try running `make extract -j8` to extract C code for the Pump example
3.  If I create  `test.fst` file and write some pipit code there, I think the way to run it is `fstar.exe test.fst`

Resources:
- [1] https://github.com/songlarknet/pipit
- [2] https://code.visualstudio.com/docs/remote/wsl
- [3] https://techcommunity.microsoft.com/t5/windows-11/how-to-install-the-linux-windows-subsystem-in-windows-11/m-p/2701207
