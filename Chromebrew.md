[![Fork me on GitHub](https://chromebrew.github.io/images/forkme_right_gray_6d6d6d.png)](https://github.com/chromebrew/chromebrew)

![centered image](https://chromebrew.github.io/images/brew.png)

# Chromebrew

The missing package manager for Chrome OS

#### Chromebrew installs what you need with its dependencies:

```
$ crew install vim
```

#### It also registers the changes being made, so you can easily remove anything:

```
$ crew remove vim
```

#### See which packages are currently available:

```
$ crew search
```

#### Look for a package:

```
$ crew search vim
```

#### Update software lists:

```
$ crew update
```

#### Update Chromebrew packages:

```
$ crew upgrade
```

#### Install Chromebrew (along with Ruby and Git).

##### Supported on Chrome OS systems running on an ARM (ARMv7+), legacy 32-bit x86 (without GUI support) or x86-64 processor.

```
curl -Ls git.io/vddgY | bash
```

### What is it?

Chromebrew is an [open source](https://github.com/skycocker/chromebrew/blob/master/LICENSE) package manager / source builder hybrid targeting Chromebooks and Chrome OS.

### What does it do?

It installs the software you need that hasn't been provided by Google. Many important packages are already precompiled and it's enough to just type `crew install package_name`, but if something's not already there, you can easily build and install it from source.

### How does it work?

In fact, Chromebrew is a simple Ruby script. There's also some Git involved, so we needed both of these things to run it on a bare Chrome OS. We have prebuilt them along with their dependencies to install into your system during installation. So, basically, after installing Chromebrew, you will have fully functional Ruby with Rubygems, Git and a package manager dedicated just for your Chromebook. Cool, huh?

### How is it different from Crouton/Linux (Beta)?

Well, Chromebrew doesn't install an operating system. :p

The idea is that you may be on a weak internet connection and cannot download too much data, but you don't have Crouton and need just a few small packages. Also, you may be on a good internet connection and need just a few small packages. Also, why not use Chrome OS as the operating system?

### Is GUI supported?

Chromebrew supports most GUI apps with help from the sommelier daemon. We don't support legacy 32-bit x86 architecture, due to Google dropping support.

### How can I help?

If you have a compatible Chromebook, you can fork my Github repo and add new packages to the `packages/` directory if you managed to build them from source successfully on your device. Package recipes are simple Ruby files - here is an example:

```ruby
#!/usr/bin/env ruby <- This line is not necessary, just for GitHub's language detection# It is recommended that you investigate other files in the 'packages/' directory# to help get an idea of how existing packages are being installed through Chromebrew. require 'package' class Template < Package  description ''  homepage ''  version ''  license ''       # Package license (eg. GPL-3, MIT, etc.)  compatibility '' # Package architecture compatibility (eg. aarch64, armv7l, i686, x86_64 or all)  source_url ''    # The url to the source code (eg. https://ftpmirror.gnu.org/sed/sed-4.8.tar.xz)  source_sha256 ''   # Optional: Prebuilt binary  #  binary_url ({  #    aarch64: '',  #     armv7l: '',  #       i686: '',  #     x86_64: '',  #  })  #  binary_sha256 ({  #    aarch64: '',  #     armv7l: '',  #       i686: '',  #     x86_64: '',  #  })    # Register dependencies (use the following line as a basis)  #  # depends_on '*'  #   # Function to check if install should occur.  def self.preflight   end   # Function to perform patch operations prior to build from source.  def self.patch   end   # Function to perform pre-build operations prior to build from source.  def self.prebuild   end   # Function to perform build from source.  def self.build   end   # Function to perform check from source build.  # This is executed only during `crew build`.  def self.check   end   # Function to perform pre-install operations prior to install for both source build and binary distribution.  def self.preinstall   end   # Function to perform install from source build.  def self.install   end    # Function to perform post-install for both source build and binary distribution  def self.postinstall   endend
```

© 2013-2022 Michal Siwek