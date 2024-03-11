# FlaskTest

# dockerfile

```
FROM python:3.8 AS builder


WORKDIR /app


COPY requirements.txt .


RUN pip install --no-cache-dir -r requirements.txt


FROM python:3.8-slim


WORKDIR /app


COPY --from=builder /usr/local/lib/python3.8/site-packages/ /usr/local/lib/python3.8/site-packages/


COPY . .


EXPOSE 5000


ENV FLASK_APP=app.py


CMD ["flask", "test"]

```

```
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout main
            }
        }


        stage('Run tests') {
            steps {
                sh './venv/bin/activate && python3 -m pytest'
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    if (currentBuild.result == 'SUCCESS') {
                        sh 'docker build -t flask-test .'
                    } else {
                        echo 'Build failed'
                    }
                }
            }
        }
    }
}

```


![Screenshot (3116)](https://github.com/Akhilbmsb/FlaskTest/assets/54345937/cce8dce6-dc03-46da-bd7a-1ea2ea96000f)
![Screenshot (3115)](https://github.com/Akhilbmsb/FlaskTest/assets/54345937/f20a090f-8026-49ee-91d2-7e47aeca55a3)
![Screenshot (3114)](https://github.com/Akhilbmsb/FlaskTest/assets/54345937/8776a5c2-686e-4baa-9044-a808e617a299)
