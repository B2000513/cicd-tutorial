ARG BASE_IMAGE=wso2/wso2mi:4.4.0
FROM ${BASE_IMAGE}

ENV WSO2_SERVER_HOME=/home/wso2carbon/wso2mi-4.4.0

# Switch to wso2carbon user for copying files
USER wso2carbon

# Copy CAR file as wso2carbon user
COPY --chown=wso2carbon:wso2 deployment/docker/CompositeApps/*.car ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/

# Copy keystore files as wso2carbon user
COPY --chown=wso2carbon:wso2 deployment/docker/resources/wso2carbon.jks ${WSO2_SERVER_HOME}/repository/resources/security/wso2carbon.jks
COPY --chown=wso2carbon:wso2 deployment/docker/resources/client-truststore.jks ${WSO2_SERVER_HOME}/repository/resources/security/client-truststore.jks

# Ensure correct permissions
RUN chmod 644 ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/*.car && \
    chmod 644 ${WSO2_SERVER_HOME}/repository/resources/security/*.jks