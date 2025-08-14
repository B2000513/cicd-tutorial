ARG BASE_IMAGE=wso2/wso2mi:4.4.0
FROM ${BASE_IMAGE}

ENV WSO2_SERVER_HOME=/home/wso2carbon/wso2mi-4.4.0

# Create carbonapps directory and set ownership
RUN mkdir -p ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps && \
    chown wso2carbon:wso2 ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps && \
    chmod 755 ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps

# Copy CAR file and set permissions
COPY deployment/docker/CompositeApps/*.car ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/
RUN chown wso2carbon:wso2 ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/*.car && \
    chmod 644 ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/*.car

# Copy keystore files and set permissions
COPY deployment/docker/resources/wso2carbon.jks ${WSO2_SERVER_HOME}/repository/resources/security/wso2carbon.jks
COPY deployment/docker/resources/client-truststore.jks ${WSO2_SERVER_HOME}/repository/resources/security/client-truststore.jks
RUN chown wso2carbon:wso2 ${WSO2_SERVER_HOME}/repository/resources/security/*.jks && \
    chmod 644 ${WSO2_SERVER_HOME}/repository/resources/security/*.jks

# Optional: Uncomment if custom libraries are needed
# COPY libs/*.jar ${WSO2_SERVER_HOME}/lib/
# RUN chown wso2carbon:wso2 ${WSO2_SERVER_HOME}/lib/*.jar && \
#     chmod 644 ${WSO2_SERVER_HOME}/lib/*.jar

# Ensure the container runs as wso2carbon (should be default in base image)
USER wso2carbon