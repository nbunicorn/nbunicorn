.. nbunicorn documentation master file, created by
   sphinx-quickstart on Wed May 15 21:59:28 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. role:: bash(code)
   :language: bash

.. role:: python(code)
   :language: python

=========
nbunicorn
=========

``nbunicorn`` is the easiest way to turn a Jupyter notebook into a real product!

As data scientists, we understand just how difficult it is to create a great algorithm to solve a worthy problem. As engineers, we also know how challenging deploying, securing and scaling complex data science solutions can be... So we built ``nbunicorn`` to solve just this.

How it works
============

With ``nbunicorn``, you have everything you need to go from notebook to product, with only a few lines of code! Just import our package, decorate your functions, and upload your notebook.

We'll convert it into a REST API, build all the complex dependencies into a container, and deploy it to a highly scalable cluster backed by Google Cloud.

You can call the API directly, or embed our simple JavaScript client ``nbunicorn.js`` to access your functions in a website with ease!


Get started
===========

Getting started with ``nbunicorn`` is easy! 

Preparing your notebook
-----------------------

Run :bash:`pip install nbunicorn` to install the ``nbunicorn`` package.

Import the package with :python:`import nbunicorn` in the first cell of your notebook.

For each function you want ``nbunicorn`` to expose, decorate the function with :python:`@nbunicorn.expose`.

Your functions should look like this:

.. code-block:: python

	@nbunicorn.expose
	def your_function(x):
	    return x

Deploying your notebook
-----------------------

Login to ``nbunicorn``, and from the *Deploy a notebook* panel, select your notebook file and click **Deploy**.

This will start the deployment process for your notebook. Once deployment has started, you'll be able to see your notebook in the *Deployments* panel. Click on the URL of your deployment (e.g. *https://<notebook>-<hash>.on.nbunicorn.com*) to view the API documentation for your notebook.

Integrating your notebook
-------------------------

Once your deployment is complete, each function decorated with :python:`@nbunicorn.expose` is available as a REST endpoint. You might choose to integrate this using your own code in any language you prefer.

To make things simple, we provide ``nbunicorn.js``, which is a JavaScript client specific to your notebook.

You can use ``nbunicorn.js`` in any HTML page by sourcing *https://<notebook>-<hash>.on.nbunicorn.com/nbunicorn.js*:

.. code-block:: html

	<script src="http://<notebook>-<hash>.on.nbunicorn.com/nbunicorn.js"></script>
	<script type="text/javascript">
	    var inputs = {
	        x: 1
	    };
	    your_function(inputs).then(console.log);
	</script>
