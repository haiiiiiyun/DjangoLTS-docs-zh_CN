Docs of Django LTS version, currently 1.8.13.


git submodule add "git@github.com:django/django.git" django-lts
git submodule init
git submodule update

cd django-lts
git checkout 1.8.13
cd ..
git add django-lts
git commit -m "moved django to v1.8.13"
git push

UPDATE:
cd django-lts/docs/

This section describe to translate with Sphinx and sphinx-intl command.

Create your document by using Sphinx.

Add configurations to your conf.py:

locale_dirs = ['locale/']   #path is example but recommended.
gettext_compact = False     #optional.
locale_dirs is required and gettext_compact is optional.

Extract document’s translatable messages into pot files:

$ make gettext
Setup/Update your locale_dir:

$ sphinx-intl update -p _build/locale -l zh_CN
Done. You got these directories that contain po files:

./locale/zh_CN/LC_MESSAGES/
Translate your po files under ./locale/<lang>/LC_MESSAGES/.

Build mo files and make translated document:

$ sphinx-intl build
$ make -e SPHINXOPTS="-D language='ja'" html

get all the translations from online. this updates the translations/zh_CN/LC_MESSAGES/*.po

$ tx pull -a

you can also edit the po files from local machine. then upload them to online.

$ tx push -t

docs/ contains django v1.5.1 docs content. make that using translations from tx.

$ ./update.py
