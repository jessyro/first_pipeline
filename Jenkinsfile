pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // שולף את הקוד מ-GitHub
                git url: 'https://github.com/jessyro/first_pipeline.git', branch: 'main'  // החלף ב-URL של ה-repository שלך
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                // התקנת pytest
                sh 'pip3 install pytest'  // מתקין את pytest אם הוא לא מותקן
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                // ריצה של קוד Python
                sh 'python3 app.py'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // הרצת בדיקות עם pytest
                sh 'pytest --maxfail=1 --disable-warnings -q'  // --maxfail=1 מגביל את הבדיקות ל-1 כישלון בלבד
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
