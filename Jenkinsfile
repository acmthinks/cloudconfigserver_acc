/* DevOps Pipeline */
node('master') {
    stage('Checkout') {
        echo "Checkout"
    }
    stage('Build') {
        echo "compile"
        echo "package"
        echo "unit test"
        echo "static analysis tests"
    }
    stage('Deploy to IBM Cloud') {
        echo "integration tests"
    }
}