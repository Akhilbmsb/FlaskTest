# FlaskTest

# dockerfile

```
FROM python:3.8


WORKDIR /app


COPY . /app


RUN pip install --no-cache-dir -r requirements.txt


EXPOSE 5000


ENV FLASK_APP=app.py


CMD ["flask", "test"]


```


![Screenshot (3116)](https://github.com/Akhilbmsb/FlaskTest/assets/54345937/cce8dce6-dc03-46da-bd7a-1ea2ea96000f)
![Screenshot (3115)](https://github.com/Akhilbmsb/FlaskTest/assets/54345937/f20a090f-8026-49ee-91d2-7e47aeca55a3)
![Screenshot (3114)](https://github.com/Akhilbmsb/FlaskTest/assets/54345937/8776a5c2-686e-4baa-9044-a808e617a299)
