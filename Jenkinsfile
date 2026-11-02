pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Render Kustomize') {
            steps {
                sh '''
                    # Every overlay must build, or Argo CD would fail to sync it.
                    for overlay in overlays/*/; do
                        echo "Rendering $overlay"
                        kubectl kustomize "$overlay" > /dev/null
                    done
                '''
            }
        }
    }
}
