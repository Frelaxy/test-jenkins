pipeline {
    agent any
    environment {
        COMPONENT = "support"
        VERSION = "master"
        DEPLOY_ID = "${BUILD_TIMESTAMP}"
        CUSTOMERS_DIRECTORY = "/home/active/mgmt/ansible/customers"
        PYENV_VERSION = "3.8.3"
        PYENV_ROOT = "/home/active/.pyenv"
        PATH = "$PYENV_ROOT/bin:$PATH"
    }
    stages {
        stage('Deploy scripts ya') {
            steps {
                script {
                    env.SOFLINE_INVENTORY_PATH = "softline/production/ya/ansible/inventory"
                    env.INVENTORY_DIR = "${CUSTOMERS_DIRECTORY}/${SOFLINE_INVENTORY_PATH}"
                    env.AP_CONFIG_FILE = "${INVENTORY_DIR}/group_vars/all/ap.yml"
                }
                sh "echo INFO: Deploy - ${COMPONENT} scripts for softline installation."
                sh "echo ${AP_CONFIG_FILE}"
                script {
                    env.SOFLINE_INVENTORY_PATH = "noventiq/production/aws/ansible/inventory"
                    env.INVENTORY_DIR = "${CUSTOMERS_DIRECTORY}/${SOFLINE_INVENTORY_PATH}"
                    env.AP_CONFIG_FILE = "${INVENTORY_DIR}/group_vars/all/ap.yml"
                }
                sh "echo INFO: Deploy - ${COMPONENT} scripts for noventiq installation."
                sh "echo ${AP_CONFIG_FILE}"
            }
        }
    }
}
