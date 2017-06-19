# webmethods-integrationserver-wxmfthelper
Package for generating MFT configs from json files

## Installation
1) Copy the package WxMFTHelper to <<IS_root>>/instances/default/replicate/inbound
2) In IS Admin-GUI go to Packages->Management. Click on "Install Inbound Releases", and select "WxMFTHelper.zip".
3) Click "Install Release"

## Package Description
The package has the following content.

### WxMFTHelper.services
WxMFTHelper.services:createMD5				- creates an md5 hash value<br />
WxMFTHelper.services:deleteConfig			- deletes the MFT config of the MFT server (choices: all,ports,users,vfs)<br />
WxMFTHelper.services:generate				- generates a new MFT config specified in the given json file<br /> 
WxMFTHelper.services:startUp				- checks whether the dir ./packages/WmMFTHelper/resources is readable for the package<br />
WxMFTHelper.services:verifyMD5				- verifies an md5 hash value<br />

### WxMFTHelper/resources
at_https_cert.jks							- Java key store holding the cert for https connections<br />
at_sftp_server_cert.jks						- Java key store for sftp connections holding the private key for the sftp port
at_sftp_server_cert.openssl					- private key for sftp port
complex_setup.json							- mft setup for a complex mft scenario in json format
simple_setup.json							- mft setup for a simple mft scenario in json format

### WxMFTHelper.utils
Service used by deleteConfig and generate


## Samples
Running WxMFTHelper.services:generate specifying either complex_setup.json or simple_setup.json as input 
will generate the corresponding MFT scenario on the local IS.
**Attention**:If testing the ports is leading to login erros in the clients, e.g. winscp,
you have to restart the IS after applying the MFT scenarios.

### simple_setup.json
Generates the http port, one user, and one vfs.

### complex_setup.json
Generates several ports, multiple system users as well as ldap users - if possible -,
and multiple local vfs as well as remote vfs - if possible.

The results of the generation can be viewed in server.log.
