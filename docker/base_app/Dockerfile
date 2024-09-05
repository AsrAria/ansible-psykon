FROM python:3.7

# copy project from base server image
COPY --from={{ base_server_path }} /home/app/ /home/app/

# move to working directory
WORKDIR /home/app/server

# install python packages
RUN pip install -r requirements