FROM tomcat

RUN apt-get update \
    && apt-get install -y xmlstarlet \
    && apt-get install -y wget \
    # Get Birt
    && cd ~ && wget http://mirror.dkm.cz/eclipse/birt/downloads/drops/R-R1-4.8.0-201806261756/birt-runtime-4.8.0-20180626.zip \
    # Install Birt
    && unzip birt-runtime-4.8.0-20180626.zip -d birt-runtime-4.8.0 \
    && cd birt-runtime-4.8.0 \
    && cp -r WebViewerExample $CATALINA_HOME/webapps/birt-viewer \
    # Get JDBC drivers
    && cd ../ \
    && wget https://jdbc.postgresql.org/download/postgresql-42.2.6.jar \
    && wget https://download.microsoft.com/download/4/D/C/4DCD85FA-0041-4D2E-8DD9-833C1873978C/sqljdbc_7.2.2.0_enu.tar.gz \
    # Install Jdbc Drivers
    && mv postgresql-42.2.6.jar $CATALINA_HOME/webapps/birt-viewer/WEB-INF/lib \
    && tar xvzf sqljdbc_7.2.2.0_enu.tar.gz \
    && mv sqljdbc_7.2/enu/mssql-jdbc-7.2.2.jre8.jar $CATALINA_HOME/webapps/birt-viewer/WEB-INF/lib \
    # Cleanup
    && rm -r * \
    # Add rights for access manager gui, host-gui
    && cd $CATALINA_HOME/webapps/manager/META-INF \
    && xmlstarlet ed -d "//Valve" context.xml > tmp.xml \
    && mv tmp.xml context.xml \
    && cd $CATALINA_HOME/webapps/host-manager/META-INF \
    && xmlstarlet ed -d "//Valve" context.xml > tmp.xml \
    && mv tmp.xml context.xml
