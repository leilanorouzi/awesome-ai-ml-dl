# JuPyteR

[JuPyteR notebooks](https://jupyter.org/) also gives us the facility to write notebooks using Java, Scala and other JVM and non-JVM languages in addition to Python, R and Julia.

### Kernels
These are provided using via kernels, for e.g. the [IJava kernel](https://github.com/SpencerPark/IJava) when installed, provides Java language support in Jupyter notebooks. Take a look at the docs and examples provided on https://github.com/SpencerPark/IJava.

### Additional source of kernels
[beakerx](http://beakerx.com/) Is another source where a wider range of kernels can be found.

## Get started: Automated (via scripts)

### Local environment

```
./install-java-kernel.sh
```

We should see the below output:

```
A list of already installed kernels in your jupyter environment
Available kernels:
  python2    /[User home]/[path/to]/jupyter/kernels/python2
Downloading the Java kernel version 1.2.0
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   606    0   606    0     0   1419      0 --:--:-- --:--:-- --:--:--  1415
100 5397k  100 5397k    0     0  2321k      0  0:00:02  0:00:02 --:--:-- 4213k
Unzipping the Java kernel version 1.2.0
Archive:  ijava-1.2.0.zip
   creating: java/
  inflating: java/ijava-1.2.0.jar
  inflating: java/kernel.json
   creating: java/dependency-licenses/
   creating: java/dependency-licenses/commons-io-2.5.jar/
   [...snipped...]
  inflating: install.py
Using the install.py command to install Java kernel version 1.2.0.
[InstallKernelSpec] Installed kernelspec java in /[path/to]/jupyter/kernels/java
A list of already installed kernels in your jupyter environment
Available kernels:
  java       /[User home]/[path/to]/jupyter/kernels/java
  python2    /[User home]/[path/to]/share/jupyter/kernels/python2
```

### Docker

...To follow ASAP...

## Get started: Manual steps (via CLI)

### Check for available kernels

Let's find out what exists in our development environment:

```
$ jupyter kernelspec list
```

Here is a sample output depending on what is installed in our development environment:

```
Available kernels:
  python2    /[User home]/[path/to]/jupyter/kernels/python2
```

Output might vary slightly depending on how your `python` environment has been setup.

### Download and unzip the kernel (from pre-compiled binary release)

Download the [IJava kernel](https://github.com/SpencerPark/IJava) version 1.2.0 with:

```
$ curl -L https://github.com/SpencerPark/IJava/releases/download/v1.2.0/ijava-1.2.0.zip -O ijava-1.2.0.zip

### ~~~ choose a destination to unzip the archive ~~~

$ unzip ijava-1.2.0.zip
```

### Install the kernel

**Pre-requisite:** Java 9 when installing the pre-compiled binary from https://github.com/SpencerPark/IJava/releases/

#### Method 1: via the `jupyter` command on the command-line

```    
$ jupyter kernelspec install java
```

```
[InstallKernelSpec] Installed kernelspec java in /[path/to]/jupyter/kernels/java
```

Note: destination paths may vary hence `[path/to]`.

#### Method 2: via the `python3` command on the command-line

```
$ python3 install.py --sys-prefix
```

```
Installed java kernel into "/[path/to]/jupyter/kernels/java"
```

Note: destination paths may vary hence `[path/to]`.

### Recheck for the now available kernels

Let's find out if the installation was successful:

```
$ jupyter kernelspec list
```

We could expect an output like the below:

```
Available kernels:
  java       /[User home]/[path/to]/jupyter/kernels/java
  python2    /[User home]/[path/to]/jupyter/kernels/python2
```

Output might vary slightly depending on how your `python` environment has been setup.

### Kernel installation: variety of combinations of environments and JDKs 

See [Other kernel installation methods](Other-kernel-installation-methods.md)

Please take a glance at the above link, especially if `jupiter-notebook` or `jupyter-lab` has trouble locating the kernels.

### Removing the installed kernel

```    
$ jupyter kernelspec remove java
```

Interaction to confirm removal of the kernel:

```
Kernel specs to remove:
  java                  /[User home]/[path/to]/jupyter/kernels/java
Remove 1 kernel specs [y/N]: y
[RemoveKernelSpec] Removed /[User home]/[path/to]/jupyter/kernels/java
```

Note: destination paths may vary hence `[path/to]`.

## Scripts provided:

- Jupyter-Dockerfile: a dockerfile script to help build a docker image of Jupyter with the IJava kernel running on Java 9 (with Graal enabled)
- buildJupyterDockerImage.sh: build the Jupyter-Dockerfile dockerfile
- runJupyterDockerContainer.sh: run the Jupyter docker image, exposing port 8080 to point your browser to (http://localhost:8080)

Enjoy writing prototypes, experiments or do some real work with it, in Java, Scala or any other kernel of your choice.