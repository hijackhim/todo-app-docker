# Django-todo
A simple todo app built with Django

![todo App](https://raw.githubusercontent.com/shreys7/django-todo/develop/staticfiles/todoApp.png)
### Setup
To get this repository, run the following command inside your git-enabled terminal
```bash
$ git clone https://github.com/shreys7/django-todo.git
```
You will need Django to be installed on your computer to run this app. Head over to https://www.djangoproject.com/download/ for the download guide

Once you have downloaded Django, go to the cloned repo directory and run the following command

```bash
$ python manage.py makemigrations
```

This will create all the migrations files (database migrations) required to run this App.

Now, to apply these migrations run the following command
```bash
$ python manage.py migrate
```

One last step and then our todo App will be live. We need to create an admin user to run this App. On the terminal, type the following command and provide username, password, and email for the admin user
```bash
$ python manage.py createsuperuser
```

 
That was pretty simple, right? Now let's make the App live. We just need to start the server now and then we can start using our simple todo App. Start the server by following the command

```bash
$ python manage.py runserver
```

Once the server is hosted, head over to http://127.0.0.1:8000/todos for the App.

Now if We want to deploy it through Docker
we can automate the whole process using Docker
The steps to it are-
1. Install Docker through --> $ sudo apt install docker.io   #this is for Ubuntu, the command may be changed for different Linux flavors.
2. Create  dockerfile by --> $ vi Dockerfile
3. In the above Dockerfile write the command as follows

FROM python:3
RUN  pip install django==3.2

COPY . .

RUN python manage.py migrate
CMD ["python","manage.py","runserver","0.0.0.0:8000"]

4. Now run the docker file by building it --> docker build . -t todo-app
5. Now $ docker run -p 8000:8000 docker-image-id    #will get the image id from executing above command.
   like this![image](https://github.com/hijackhim/todo-app-docker/assets/105789918/f5affc8c-acbc-4795-9578-450659b4668c)
6. Now use your machine's public IP with the port given in the above command and try to open it in the browser.
   Ex - 3.256.152.95:8000    #IP will be changed for your machine.


