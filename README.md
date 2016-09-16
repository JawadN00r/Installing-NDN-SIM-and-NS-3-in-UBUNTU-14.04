# Installing NDN-SIM and NS-3 in UBUNTU-14.04
Open a terminal and run these commands to install dependencies:
 ```bash   
    sudo apt-get install build-essential libsqlite3-dev libcrypto++-dev
    sudo apt-get install libboost-all-dev
    sudo apt-get install python-dev python-pygraphviz python-kiwi
    sudo apt-get install python-pygoocanvas python-gnome2
    sudo apt-get install python-rsvg ipython unzip
    sudo apt-get install g++
    sudo apt-get install gccxml
    sudo apt-get install libboost-all-dev
    sudo apt-get install libsqlite3-dev
```
Go to the directory where you want to install 
```bash
    mkdir ndnSIM
    cd ndnSIM

    wget https://github.com/named-data-ndnSIM/ns-3-dev/archive/2c66f4c02008805eaa7f2a21b88162b4f46e5ec2.zip -O ns-3.zip
    unzip ns-3.zip
    mv ns-3-dev-2c66f4c02008805eaa7f2a21b88162b4f46e5ec2/ ns-3

    wget https://github.com/cawka/pybindgen/archive/e11c02d87924d92ee80991c9d663e1398a468008.zip -O pybindgen.zip
    unzip pybindgen.zip
    mv pybindgen-e11c02d87924d92ee80991c9d663e1398a468008/ pybindgen


    wget https://github.com/named-data-ndnSIM/ndnSIM/archive/5897c967f6fa64755fd08ea29657c9525d7d76ce.zip -O ndn.zip
    unzip ndn.zip
    mv ndnSIM-5897c967f6fa64755fd08ea29657c9525d7d76ce/ ns-3/src/ndnSIM

    wget https://github.com/named-data-ndnSIM/NFD/archive/bd8eea71137bc382fe1fb8225334b926a5484527.zip -O nfd.zip
    unzip nfd.zip
    mv NFD-bd8eea71137bc382fe1fb8225334b926a5484527/ NFD
    mv NFD/ ns-3/src/ndnSIM/

    wget https://github.com/named-data-ndnSIM/ndn-cxx/archive/36ec104e23ba5395a8b4df411b776cdbef9c5cd4.zip -O ndn-cxx.zip
    unzip ndn-cxx.zip
    mv ndn-cxx-36ec104e23ba5395a8b4df411b776cdbef9c5cd4/ ndn-cxx
    mv ndn-cxx ns-3/src/ndnSIM/

    cd pybindgen/
    ./waf configure
    ./waf
    sudo ./waf install

    cd ..
    cd ns-3/

    gedit bindings/python/wscript
```
change line **16** to:
```bash
    REQUIRED_PYBINDGEN_VERSION = '0.17.0.887'
```
**save and exit**

Now run
```bash
    ./waf configure -d debug --enable-example --enable-tests
    ./waf
    sudo ./waf install
```