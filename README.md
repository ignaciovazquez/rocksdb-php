RocksDB PHP Extension
===
RocksDB is a new embedded database for storing key-value pairs developed by Facebook. This project hosts a PHP extension for RocksDB. More information on RocksDB can be found here:

https://github.com/facebook/rocksdb

##Platforms
RocksDB is said to compile on Linux and Mac OS X. So far, I haven't seen anyone getting it to build on Windows, but it should work.
My build environment is:

* Ubuntu 13.10 x64
* GCC 4.8.1

All documentation, instructions and guides assume my configuration. If you were able to get it working on another platform, please let me know.

## Build
#### Building PHP
The RocksDB PHP extension is being written against PHP 5.5.3. To be able to build the RocksDB PHP extension, you need to install the following packages:

    sudo apt-get install php5-dev
    sudo apt-get install php5-cli

#### Building PHP-CPP
PHP-CPP is a C++ library which makes developing PHP extensions from C++ possible. It's also, way easier then using the native PHP C API. PHP-CPP can be found here:

https://github.com/EmielBruijntjes/PHP-CPP

To build, clone the repository:

	git clone https://github.com/EmielBruijntjes/PHP-CPP.git php-cpp

Go into the 'php-cpp' directory and run:

	make

After that, 'libphpcpp.so' should be present in the 'src' directory. To install the library, do one of the following thins:

* Add the path where you cloned PHP-CPP to LD_LIBRARY_PATH (`export LD_LIBRARY_PATH+=/path/to/php-cpp/src`)
* Create a new file in `/etc/ld.so.conf.d` with the `.conf` extension, where the path to the PHP-CPP src directory is on a single line
* Copy the file `libphpcpp.so` to `/usr/lib`
    
#### Building RocksDB
To build the RocksDB PHP Extension, you first need to build RocksDB. Clone the RocksDB git repository using:

    git clone https://github.com/facebook/rocksdb.git
  
To be able to build RocksDB, you first need to install all dependencies, this can be done using apt-get:

    sudo apt-get install libsnappy-dev
    sudo apt-get install zlib1g-dev
    sudo apt-get install libbz2-dev
    sudo apt-get install libgflags2
    
After you've install all dependencies, you can simply run:

    make clean
    make
    
To build and run all unit tests:

    make check
    
To install the RocksDB library you can do either of these three things:

* Add the path where you cloned RocksDB to LD_LIBRARY_PATH (`export LD_LIBRARY_PATH+=/path/to/rocksdb`)
* Create a new file in `/etc/ld.so.conf.d` with the `.conf` extension, where the path to RocksDB is on a single line
* Copy the file `librocksdb.a` to `/usr/lib`

Choose whatever you like :)
