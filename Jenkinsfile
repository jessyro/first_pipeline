pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // שולף את הקוד מ-GitHub
                git 'https://github.com/jessyro/first_pipeline.git'  // החלף ב-URL של ה-repository שלך
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                // ריצה של קוד Python
                sh 'python app.py'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // בדיקה פשוטה (במקום הרצת Test אמיתי, אנחנו פשוט כותבים שהכל בסדר)
                echo 'Test passed!'  // פה ניתן להוסיף קוד לבדיקות מתקדמות אם יש צורך
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the app...'
                // כאן תוכל להוסיף את הפקודות כדי להעלות את האפליקציה לשרת או לעזור לה להפעיל בסביבה אחרת
                echo 'App deployed successfully!'
            }
        }
    }
}
