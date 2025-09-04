pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // 不需要再寫 git checkout，因為 Jenkins 會自動 checkout repo
                echo "✅ SCM 已自動 checkout"
            }
        }

        stage('Install') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                bat """
                if exist D:\\IIS_Fonghs\\next rmdir /s /q D:\\IIS_Fonghs\\next
                mkdir D:\\IIS_Fonghs\\next
                xcopy /s /i /y * D:\\IIS_Fonghs\\next
                """
            }
        }
    }
}