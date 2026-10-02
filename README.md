# SparrowdoRISCV

How to run Rocky Linux Sparky tests on your RISCV box over ssh or localhost

# Prerequisites 

You have box with RISCV architecture with Rocky Linux OS installed

# Install Rakupp

```
sudo yum -q -y install curl wget openssl-devel perl-JSON-PP
sudo curl -L -s -f  http://sparrowhub.io/riscv/rakupp -o /usr/local/bin/rakupp
sudo chmod a+x /usr/local/bin/rakupp
sudo ln -fs /usr/local/bin/rakupp /usr/local/bin/raku
rakupp install --no-test Sparrow6
```

# Install Sparrowdo

You'll need the latest Sparrowdo version from GitHub:

```
git clone https://github.com/melezhik/sparrowdo.git
cd sparrowdo
rakupp install —test .
export PATH=~/.raku/bin:$PATH
```

Run `sparrowodo --version`, you should see something like 

```
0.1.57.a
```

# Checkout some Rocky Linux Sparky Test

```
git clone https://git.resf.org/testing/Sparky-Python-SSL.git
```

Run tests

## Localhost

If you want to run against your local host box:

```
cd Sparky-Python-SSL
sparrowdo --localhost --no_sudo --sparrowfile main.raku --color 
```

## Ssh

If you want to run against some RISC-V ssh box:

```
cd Sparky-Python-SSL
sparrowdo --host some.remote.host --bootstrap --no_sudo --sparrowfile main.raku --color 
```

Notice `bootstrap` flag in the second (ssh) case, it's important.

---

That's it. Happy testing 
