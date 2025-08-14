ARG BASE_IMAGE=wso2/wso2mi:4.4.0
FROM ${BASE_IMAGE}
ENV WSO2_SERVER_HOME=/home/wso2carbon/wso2mi-4.4.0
COPY deployment/docker/CompositeApps/*.car ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/
COPY deployment/docker/resources/wso2carbon.jks ${WSO2_SERVER_HOME}/repository/resources/security/wso2carbon.jks
COPY deployment/docker/resources/client-truststore.jks ${WSO2_SERVER_HOME}/repository/resources/security/client-truststore.jks
RUN chmod 644 ${WSO2_SERVER_HOME}/repository/deployment/server/carbonapps/*.car && \
    chmod 644 ${WSO2_SERVER_HOME}/repository/resources/security/*.jks