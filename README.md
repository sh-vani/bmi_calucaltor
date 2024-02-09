This project is simple python program for BMI calculator having basic operations . It takes input from user as height and weight

As checked code was working right. For its working we need some additional tools such as tiktar as its code dependancy. Using Dockerfile we have created docker image for this project Steps for it as: ####Here We have selected base image as

FROM python:3.9-slim

Container has its temporary WD inside it let set it as WD. WORKDIR /app

Copy the current directory contents into the container at /app COPY . /app

Install any needed dependencies specified in requirements.txt RUN pip install --no-cache-dir -r requirements.txt

Make port 8080 available to the world outside this container EXPOSE 8080

Run main.py when the container launches CMD ["python", "main.py"]

Create docker image using following command docker build -t smitwaman/simple-calculator:v4 .

Upload it to registry using login PAT

docker login -u hp

docker push hp/BMI-calculator:v5 .

And simply using pull command we can run our python project.

For ex: docker pull hp/BMI-calculator:v5

for running python code in interactive mode we need to use -t -i with run command

sudo docker run -it hp/BMI-calculator:v5
