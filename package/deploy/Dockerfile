FROM gcr.io/google-appengine/python

# Create a virtualenv for dependencies. This isolates these packages from
# system-level packages.
# Use -p python3 or -p python3.7 to select python version. Default is version 2.
RUN virtualenv -p python3.7 /env

# Setting these environment variables are the same as running
# source /env/bin/activate.
ENV VIRTUAL_ENV /env
ENV PATH /env/bin:$PATH

# Copy the application's requirements.txt and run pip to install all
# dependencies into the virtualenv.
ADD requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

# Add the application source code.
#ADD . ./

# Run a WSGI server to serve the application. gunicorn must be declared as
# a dependency in requirements.txt.
#CMD gunicorn -b :$PORT main:app
FROM gcr.io/supplytracker/main:latest
CMD gunicorn -b :$PORT main:app
