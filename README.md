# how-to-make-aws-lambda-layer
This tells you how to make an aws lambda layer on macos.

To do it for python:
0. Create folder with lambda layer name, then a folder called python inside of it, and traverse inside the folder with lambda ln.
1. Create python venv: python3 -m venv venv
2. Active venv: source venv/bin/activate
3. Install reqd libs in python folder: (from main folder containing venv & python) pip install openai -t python

NOTE: must use following command to assure it will work on platform: https://docs.aws.amazon.com/lambda/latest/dg/python-package.html#python-package-native-libraries
pip install \
--platform manylinux2014_x86_64 \
--target=package \
--implementation cp \
--python-version 3.x \
--only-binary=:all: --upgrade \
<package_name>

input: package name and python version

4. Go back to the parent folder and zip the python foler and create the layer package: zip -r layer-package.zip python

Upload to AWS in lambda -> layers.

---------

To do it for Node.js:
0. Create folder with lambda layer name, then a folder called nodejs inside of it and traverse there.
1. Create node js project: npm init -y
2. Install reqd libs: npm install aws-jwt-verify
3. Go back to the parent folder and zip the nodejs foler and create the layer package: zip -r layer-package.zip nodejs

Upload to AWS in lambda -> layers.

---------

Zip file:
zip output_filename.zip input_filename

Change permissions (optional)
chmod u=rwx,go=r
