# onvif-relay
An onvif device request relay.
Accepts ONVIF defined SOAP requests and forwards them to ONVIF compliant devices

See: https://tips.graphica.com.au/onvif-ws-client-consumption/

## Tools:

This project uses Apaxche Maven to generate client/server stubs using:
- Java (Open SDK 11)
- Java EE JAVAX-WS/JAX-WS to parse WSDL and generate Java code or
- Jakarta EE/JAX-WS to parse WSDL and generate Java code
- Apache Maven build system
- Developed and tested on Ubuntu 22.04

Maven Targets:
- mvn -X jaxws:wsimport : to generate java stubs and client
- mvn -X initialize : to download and patch ONVIF wsdl for jaxws:wsimport (runs get-and-patch.sh)

NOTE 1: Currently automtic download and patch of ONVIF wsdls does not work via Maven.

Run manually via:
- $ get-and-patch.sh <filelist.txt> <download.dir> <destination.dir> <patch.dir>
- src/main/sh/get-and-patch.sh src/main/sh/files.txt target/generated-sources/wget/ src/main/resources/META-INF/wsdl/ src/main/patch/

NOTE 2: You can generate code with javax or jakarta inclusions
- To change between Java EE (import javax.PKG) or Jakarta EE (import jakarta.PKG) requires editing of Maven pom.xml properties

# Author:

John Hartley

# License

None

This repository is just to for purpose of documenting and getting feedback from others working to test/interface with ONVIF devices, 

If you are looking to solve using Jakarta EE/wsimport to automatically generate interfaces to ONVIF device, then please fork and submit pull requests

# Status:

- Jan 2023 - Added Embedded Jetty based onvif test device, but not tested
- Jan 2023 - Tested Embedded Jetty based onvif test device, exposing SOAP 1.1 not SOAP 1.2
 