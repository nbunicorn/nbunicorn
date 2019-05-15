# nbunicorn

To push update to PyPi:

	python setup.py sdist
	twine upload dist/*

Validate push (you may have to wait a minute for PyPi to reflect the latest version):
	
	pip install --upgrade nbunicorn
	pip freeze | grep nbunicorn

To locally rebuild docs (into \_build):

	cd docs
	make html