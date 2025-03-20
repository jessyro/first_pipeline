pipeline {
    agent any

    environment {
        // אם יצרת סביבה וירטואלית בתיקיית workspace
        VENV_PATH = "${workspace}/my_venv"
    }

    stages {
        stage('Checkout') {
            steps {
                // שלב זה מבצע את ההורדה של קוד ה-Git
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // יצירת סביבה וירטואלית אם לא קיימת
                    sh """
                    if [ ! -d "${VENV_PATH}" ]; then
                        python3 -m venv ${VENV_PATH}
                    fi
                    """
                    // התקנת pytest (תוכל להוסיף חבילות נוספות כאן)
                    sh """
                    source ${VENV_PATH}/bin/activate
                    pip install --upgrade pip
                    pip install pytest
                    """
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // הפעלת הפקודות הנדרשות כדי לבנות את הפרויקט שלך
                    sh """
                    source ${VENV_PATH}/bin/activate
                    python3 app.py
                    """
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // הפעלת בדיקות עם pytest
                    sh """
                    source ${VENV_PATH}/bin/activate
                    pytest --maxfail=1 --disable-warnings -q
                    """
                }
            }
        }

        stage('Deploy') {
            steps {
                // אם יש צורך, אפשר להוסיף שלב דיפלוי כאן
                echo 'Deploying the app...'
            }
        }
    }
    
    post {
        always {
            // הסרת הסביבה הוירטואלית בסוף כדי לא להשאיר שאריות
            echo 'Cleaning up...'
            sh "deactivate"
        }
    }
}
