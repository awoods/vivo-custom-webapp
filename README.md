# VIVO Custom Webapp

This project replaces the legacy "VIVO Installer". It is used to create a "third-tier" overlay on the standard `vivo.war` file.

## Usage

1. Clone this repository
2. Add any overlay files to their expected location with the `src` directory tree
   e.g.
   ```
   src/main/webapp/themes/custom-theme
   src/main/java/com/wok/vivo/dataservice/MyCustomClass.java
   ```
3. Add any overlay files to their expected location with the `home` directory tree
   e.g.
   ```
   home/src/main/resources/config/applicationSetup.n3
   home/src/main/resources/config/runtime.properties
   home/src/main/resources/rdf/display/firsttime/menu.n3
   ```
4. Build the custom webapp
   ```
   mvn clean install -Dapp-name=<my-app> -Dvivo-dir=<path-to-vivo-home>
   ```
   - The provided 'app-name' will be the name of the produced `.war` file (e.g. `my-app.war`) as well as the name of the application log file (`my-app.all.log`).
      - Default: "vivo-custom-webapp"
   - The provided 'vivo-dir' must be the absolute path of an existing directory in which VIVO home files will be copied. The directory must have "write" permissions for the system user from which the Tomcat service will be running.
      - Default: current-working-directory

## Use in development

This custom webapp template is intended for use with VIVO version 1.12 and later. For use with previous versions, see https://github.com/vivo-community/vivo-project-template. For use with unreleased development branches of VIVO, you must build VIVO locally prior to installing your custom webapp. 

1. Clone this repository
2. Add any overlay files to their expected location with the `src` directory tree
   e.g.
   ```
   src/main/webapp/themes/custom-theme
   src/main/java/com/wok/vivo/dataservice/MyCustomClass.java
   ```
3. Add any overlay files to their expected location with the `home` directory tree
   e.g.
   ```
   home/src/main/resources/config/applicationSetup.n3
   home/src/main/resources/config/runtime.properties
   home/src/main/resources/rdf/display/firsttime/menu.n3
   ```
4. Change the version in the custom webapp's pom.xml file to match the development version of VIVO in https://github.com/vivo-project/VIVO/blob/main/pom.xml
5. Build base VIVO webapp
   ```
   cd <location of VIVO source code>
   mvn clean install
   ```  
6. Build the custom webapp
   ```
   cd <location of custom webapp code>
   mvn clean install -Dapp-name=<my-app> -Dvivo-dir=<path-to-vivo-home>
   ```
   - The provided 'app-name' will be the name of the produced `.war` file (e.g. `my-app.war`) as well as the name of the application log file (`my-app.all.log`).
     - Default: "vivo-custom-webapp"
   - The provided 'vivo-dir' must be the absolute path of an existing directory in which VIVO home files will be copied. The directory must have "write" permissions for the system user from which the Tomcat service will be running.
     - Default: current-working-directory