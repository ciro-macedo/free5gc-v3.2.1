<p align="center">
<a href="https://free5gc.org"><img width="40%" src="https://forum.free5gc.org/uploads/default/original/1X/324695bfc6481bd556c11018f2834086cf5ec645.png" alt="free5GC"/></a>
</p>

<p align="center">
<a href="https://github.com/free5gc/free5gc/releases"><img src="https://img.shields.io/github/v/release/free5gc/free5gc?color=orange" alt="Release"/></a>
<a href="https://github.com/free5gc/free5gc/blob/master/LICENSE.txt"><img src="https://img.shields.io/github/license/free5gc/free5gc?color=blue" alt="License"/></a>
<a href="https://forum.free5gc.org"><img src="https://img.shields.io/discourse/topics?server=https%3A%2F%2Fforum.free5gc.org&color=lightblue" alt="Forum"/></a>
<a href="https://www.codefactor.io/repository/github/free5gc/free5gc"><img src="https://www.codefactor.io/repository/github/free5gc/free5gc/badge" alt="CodeFactor" /></a>
<a href="https://goreportcard.com/report/github.com/free5gc/free5gc"><img src="https://goreportcard.com/badge/github.com/free5gc/free5gc" alt="Go Report Card" /></a>
<a href="https://github.com/free5gc/free5gc/pulls"><img src="https://img.shields.io/badge/PRs-Welcome-brightgreen" alt="PRs Welcome"/></a>
</p>

## What is free5GC

The free5GC is an open-source project for 5th generation (5G) mobile core networks. The ultimate goal of this project is to implement the 5G core network (5GC) defined in 3GPP Release 15 (R15) and beyond.

For more information, please refer to [free5GC official site](https://free5gc.org/).

## Documentation

For document, please reference to [Documentation](https://github.com/free5gc/free5gc/wiki).

## Discussion

For questions and support please use the [official forum](https://forum.free5gc.org). The issue list of this repo is exclusively for bug reports and feature requests.

## Contributing

We're welcome for contribution via [GitHub Pull Request](https://github.com/free5gc/free5gc/pulls).

## Release Note

Detailed changes for each release are documented in the release notes.Detailed changes for each release are documented in the [release notes](https://github.com/free5gc/free5gc/releases).

## License

free5GC is now under [Apache 2.0](https://github.com/free5gc/free5gc/blob/master/LICENSE.txt) license.

## Additional Information

### Dependencies
####  User-plane Supporting Packages

``
sudo apt -y update
sudo apt -y install git gcc g++ cmake autoconf libtool pkg-config libmnl-dev libyaml-dev ansible
``

####  MongoDB (Ubuntu 20.04 [Focal])

Import the public key used by the package management system

``
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
``

Create the ``/etc/apt/sources.list.d/mongodb-org-6.0.list`` file for Ubuntu 20.04 (Focal)

``
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
``

Reload local package database
``
sudo apt-get update
``

Install the MongoDB packages
``
sudo apt-get install -y mongodb-org
``

Start MongoDB
``
sudo systemctl start mongod
``

Verify that MongoDB has started successfully
``
sudo systemctl status mongod
``

Ensure that MongoDB will start following a system reboot
``
sudo systemctl enable mongod
``

### Git Clone with submodules
``
git clone --recursive -b main -j `nproc` https://github.com/ciro-macedo/free5gc-v3.2.1.git
``

### Config Dev Mode Steps

To configure project to local debu just run ansible playbook (sudo access is need):

``
ansible-playbook -K DevelopmentEnvironmentConfigByAnsible.yml 
``



### Start Order NFs Functions
``
NRF > UDR > UDM > AUSF > NSSF > AMF > PCF > UPF (sudo -E ./bin/free5gc-upfd) > SMF > SERVER-WEB > SERVER-FRONT-END ( REACT_APP_HTTP_API_URL=http://core_ip_address:5000/api PORT=3000 yarn start )
``
