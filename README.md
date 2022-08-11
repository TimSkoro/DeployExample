**Step 1: setup Heroku**
* install heroku
```
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh
```
* check version
```
heroku --version
```
* login on heroku
```
heroku login
```

**Step 2: setup Dependencies**
* libs
```
pip install gunicorn
pip install django-on-heroku
python -m pip freeze > requirements.txt
```
* create end config Procfile
```
touch Procfile
echo "web: gunicorn DeployExample.wsgi" > Procfile
```
* setup settings (*you can use the console, you can use your hands*)
```
echo "import django_on_heroku" >> DeployExample/settings.py
echo "django_on_heroku.settings(locals()) >> DeployExample/settings.py
```

**Step 3: create and deploy**
* create Heroku project
```
heroku create deploy-example
```
* deploy
```
heroku releases
git push heroku master
```
