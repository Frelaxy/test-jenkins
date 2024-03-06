pipeline {
    agent {
        label "any"
    }
    environment {
        COMPONENT = "support"
        VERSION = "master"
        DEPLOY_ID = "${BUILD_TIMESTAMP}"
        CUSTOMERS_DIRECTORY = "/home/active/mgmt/ansible/customers"
        PYENV_VERSION = "3.8.3"
        PYENV_ROOT = "/home/active/.pyenv"
        // PATH = "$PYENV_ROOT/bin:$PATH"
    }
    stages {
        stage('Deploy scripts') {
            environment {
                SOFLINE_INVENTORY_PATH = "softline/production/ya/ansible/inventory"
                INVENTORY_DIR = "${CUSTOMERS_DIRECTORY}/${SOFLINE_INVENTORY_PATH}"
                AP_CONFIG_FILE = "${INVENTORY_DIR}/group_vars/all/ap.yml"
            }
            steps {
                print("INFO: Deploy - ${COMPONENT} scripts for softline installation.")
                {
                    sh "echo ${AP_CONFIG_FILE}"
                }
            }
        }
    }
}
