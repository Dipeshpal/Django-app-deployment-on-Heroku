
# Django-app-deployment-on-Heroku
Tutorial step by step for Django app deployment on Heroku

This guide will help you to deploy Django App on Heroku

## Steps-

1. You need to create Django App (or you can [download](https://github.com/Dipeshpal/Dipesh-Pal-Django_Website) this sample dipeshpal's blog app). If you are using your app then just use your app for next few steps or if you want you can use our app.

2. Copy the project seperetely in folder name "Publish" anywhere in your computer.
![Sampe App](https://i.ibb.co/DrNw75B/1.png)

3. Delete unnecessary folders like ".git", ".idea" and "venv" folder if you have  (make sure hidden files are enabled)
![Delete files](https://i.ibb.co/gv9v2SY/2.png)

4. Create Heroku account from [here](https://id.heroku.com/login).

5. [Python](https://www.python.org/) should be installed on your computer.

6. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) should be installed on your computer.

7. Install the Heroku Command Line Interface (CLI) from [here](https://devcenter.heroku.com/articles/getting-started-with-python#set-up)

8.  [Pipenv](https://pypi.org/project/pipenv/) should be installed.

9. After Installing above tools, open command prompt in "Publish" directory and run following command in command prompt to login on Heroku-

       heroku login

 ![Heroku login](https://i.ibb.co/m57X3cP/3.png)

11.  Now you have to create virtual environment, open command prompt in "Publish" directory and run following command in command prompt-

    virtualenv .

![virtualenv](https://i.ibb.co/n3cgjHr/4.png)


12. Activate virtual environment

        .\Scripts\activate

![activate venv](https://i.ibb.co/RjRfkT7/5.png)

10. Create requirements.txt file with all your project requirements.	
	
	 - Go to your production app and activate it's virtual environment and run following commands- 
		
		    pip freeze > requirements.txt
	
	- It will create txt file and now move this file to your app folder. Example- "Publish/your_app_dolder/requirements.txt". 
	![requirements.txt](https://i.ibb.co/G9yPg3P/6.png)

	- Check your python version

		    python -V
	
		![Python Version](https://i.ibb.co/4JGYRG5/7.png)

	- Create "runtime.txt" file in your app directory and type your python version on it so that Heroku will identify your python version.
	
		![python version](https://i.ibb.co/y6Yh2q1/8.png)

11. Create file "**Procfile**" without any extension in your app directory. And enter following lines on it by replacing "myproject" with your app name.

	```
	web: gunicorn myproject.wsgi
	```
	![Prrocfile](https://i.ibb.co/CQzHNSv/9.png)

12. Install following on your virtual envirenment (our virtual enviroment is already activate in command prompt, you just need to install following)-

	- **Installing gunicorn**
	
		    pip install gunicorn
	
	- **Installing django-heroku**:

		    pip install django-heroku

13. Open your project in "Publish" folder in  any editor and edit "settings.py" file-

	- Add the following  `import`  statement to the top of  `settings.py`:

		```python
		import django_heroku
		```


	- Then add the following to the bottom of  `settings.py`:

		```python
		# Activate Django-Heroku.
		django_heroku.settings(locals())
		``` 
 
14. Now type following to check version of django-heroku, gunicorn and others files with following output-
		
		pip freeze
	
	- Copy the output and add paste it on the bottom of the "requirements.txt" we create in step number 10 above.
	
		![add new lines](https://i.ibb.co/fMhdT0w/10.png)

15. Login in heroku and just check your [heroku dashboard](https://dashboard.heroku.com/apps), it should look like this-

	![Heroku Dashboard](https://i.ibb.co/2N571HB/11.png)

16. Run following command in command prompt to create your django app on heroku-
	
	    heroku create yourappname

	![creaet app](https://i.ibb.co/zPF5zJj/12.png)
   
    - Now just check your heroku [heroku dashboard](https://dashboard.heroku.com/apps)
		
		![dashboard](https://i.ibb.co/56XfGfD/13.png)

17. Now initialize git in your app directory (not in Publish directory)-

	    git init
	![git init](https://i.ibb.co/rHBQPb7/14.png)

18. Now run following command to check status, then add files in git, then commit all the files in directory and then stablish remote connection with your heroku app, then push all the files to server (You need to follow all these steps in step number 18 whenever you makes changes in your code of your app).

	- `git status`
	- `git add --all`
	- `git commit -m "First Commit"`
	- `heroku git:remote -a yourappname`
	- `git push heroku master`

19. Once all these files are push to server open your dashboard in heroku and go to setting and find your domain name-
	![domain name](https://i.ibb.co/KmCWv7K/15.png)
	
	If you try to access your website you may not be able to browse your website because migrations are not applied yet.

20. Now you need to run linux terminal (bash) of heroku in your command prompt, type following command in command prompt-
	
	    heroku run bash

21. Now type following-

	- `ls` (Just for checking files in server)

	- `python manage.py makemigrations`

	- `python manage.py migrate`

	- `python manage.py create superuser`

23.  That's it, now browse your website.
