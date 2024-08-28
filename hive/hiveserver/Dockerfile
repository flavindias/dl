# Use the Apache Hive 4.0.0 base image
FROM apache/hive:4.0.0

# Set environment variables for Ranger
ENV RANGER_VERSION=2.4.0
ENV RANGER_HIVE_PLUGIN=ranger-${RANGER_VERSION}-hive-plugin

# Copy and install Ranger Hive plugin
COPY plugins/ranger-2.4.0-hive-plugin /opt/ranger-hive-plugin/

WORKDIR /opt
 
# Download and install Ranger Hive plugin
# RUN tar -xzf /tmp/apache-ranger-hive-plugin.tar.gz -C /tmp/ \
#     && mv /tmp/${RANGER_HIVE_PLUGIN}/ /opt/ranger-hive-plugin/ \
#     && rm /tmp/apache-ranger-hive-plugin.tar.gz

# Configure the Ranger Hive plugin
run echo whoami
# RUN chown hive:hive /opt/ranger-hive-plugin/enable-hive-plugin.sh
# RUN chmod 4755 /opt/ranger-hive-plugin/enable-hive-plugin.sh
# RUN /opt/ranger-hive-plugin/enable-hive-plugin.sh

# Set up the necessary configuration files for Ranger
COPY conf/hive-site.xml $HIVE_HOME/conf/
COPY conf/ranger-hive-security.xml /opt/ranger-hive-plugin/conf/

# Expose necessary ports
EXPOSE 10000 10002

# Start HiveServer2 with Ranger enabled
CMD ["hive", "--service", "hiveserver2"]
