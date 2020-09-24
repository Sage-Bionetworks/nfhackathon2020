# Hack for NF - NF Hackathon 2020


<p align="center">
<img src="https://github.com/Sage-Bionetworks/nfhackathon2020/blob/master/1200x628.png" alt="banner" width="800"/>
</p>


## About the event

Welcome to the 2020 Hack for NF, a virtual Hackathon focused on building high-tech solutions to improve research, clinical innovation, and quality of life for patients living with neurofibromatosis (NF). NF is a rare genetic disease that causes benign and malignant tumors to grow throughout the body. More than 2.5 million people worldwide are affected and there is still no cure. CTF’s mission is to drive research, expand knowledge and advance care for the NF community. Hack for NF is an initiative to bring together talent from various disciplines to help the NF community come closer to their vision to End NF. 
 
Hack for NF is offering three challenge tracks focused on NF Data, Mobile Device Engagement, and a Wildcard challenge. The NF Data track aims to: 1) re-use the data that NF researchers and scientists have already generated in innovative ways to answer interesting challenge questions, 2) incentivize data sharing as a powerful practice that will allow researchers to move at a faster pace and create new insights, and 3) create innovative collaborations between diverse disciplines.

## How to use this repository

We've prepared Docker containers that contain all of the necessary dependencies to retrieve available NF data from Synapse and perform some basic analyses of these data. The goal of this is to help you orient yourself to the data prior to the event in September.
We've created containers for both R and Python users. You can find instructions on running these containers and following the data demos below. 
If you like, you can also use these containers as a basis for creating your own Docker containers during the hackathon so that others can reproduce your analyses.

### Prerequisites 

These instructions assume that you:
* have registered for a [Synapse account](https://www.synapse.org/#!RegisterAccount:0) 
* have followed the [How to Participate and Getting the Data!](https://www.synapse.org/#!Synapse:syn22336443/wiki/605183) instructions on Synapse. 
* have [installed Docker Community Edition](https://docs.docker.com/v17.12/install/) and that the docker service is running on your machine
* are running a Unix-based OS, such as Ubuntu or Mac. These instructions have not been tested on Windows-based platforms. 

### RStudio Docker Image (Local)

1. Open a command line interface, such as Terminal. 
2. Do `docker pull nfosi/nf-hackathon-2020-r` to get the Docker image. 
3. Do `docker run -e PASSWORD=<mypassword> -e ROOT=true --rm -p 8787:8787 nfosi/nf-hackathon-2020-r` to start the container. Make sure to replace `<mypassword>` with a unique password. It cannot be "rstudio"!
4. Open your preferred browser and navigate to `localhost:8787`. Login using the username "rstudio" and the password that you set in step 3. 
5. In the Files pane, click on "0-setup.Rmd" to get started, and to learn how to make your Synapse credentials available to `synapser`. 

*IMPORTANT NOTE* To save any results created during your Docker session, you'll need to mount a local directory to the Docker container when you run it. This will copy anything saved to the working directory to your local machine. Before step 4, do `mkdir output` to create an output directory locally. Then run the command in step 4 with a `-v` flag e.g. `docker run -e PASSWORD=pwd --rm -p 8787:8787 -v $PWD/output:/home/rstudio/output nfosi/nf-hackathon-2020-r` Alternatively, or in addition, you can save all of your results to Synapse using `synapser`.

### jupyter Docker Image (Local)

1. Open a command line interface, such as Terminal. 
2. Do `docker pull nfosi/nf-hackathon-2020-py` to get the Docker image. 
3. Do `docker run -p 8888:8888 nfosi/nf-hackathon-2020-py` to start the container.
4. Open your preferred browser and navigate to the one of the links provided in your Terminal window after running the previous command. It should look something like: `http://127.0.0.1:8888/?token=abcd1234abcd1234abcd1234abcd1234abcd1234abcd1234`. 
5. In the Files pane, click on "Work" and then "0-setup.ipynb" to get started, and to learn how to make your Synapse credentials available to the Python `synapseclient`. 

*IMPORTANT NOTE* To save any results created during your Docker session, you'll need to mount a local directory to the Docker container when you run it. This will copy anything saved to the working directory to your local machine. Before step 4, do `mkdir output` to create an output directory locally. Then run the command in step 4 with a `-v` flag e.g. `docker run -p 8888:8888 -v $PWD/output:/home/jovyan/work/output nfosi/nf-hackathon-2020-py
` Alternatively, or in addition, you can save all of your results to Synapse using `synapseclient`.

### Running Docker containers on Windows

These instructions for running Docker on Windwows courtesy of [Lars Ericson](https://www.synapse.org/#!Synapse:syn18666641/discussion/threadId=5866):

We are given some [docker images provisioned with data and Python or R](https://github.com/Sage-Bionetworks/nfhackathon2020) for quick setup for the challenge.

I haven't tried to dual-boot my Windows Home Edition PC to Linux.  I can still run the docker images.  Here is the path:

* Download [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).  Note this is what works on Windows Home Edition.  You need Windows Professional to run the more recent Docker.  But it's OK, it still works.

* Run the newly installed Docker Quickstart 

* In Docker Quickstart, download one of the docker images listed on the GitHub, for example ```docker pull nfosi/nf-hackathon-2020-py```

* In Docker Quickstart, run ```docker-machine ip``` to get the IP address.  Suppose it is 123.456.78.910.

* Run the docker image ``` docker run -p 8888:8888 nfosi/nf-hackathon-2020-py ``` It will tell you something like ```[I 00:16:50.410 NotebookApp] The Jupyter Notebook is running at: [I 00:16:50.411 NotebookApp]  http://127.0.0.1:8888/?token=fa13464756954b325753106b75c8398c991ce9d05ff523de```

* Replace IP address 127.0.0.1 with the string you wrote down in Step 3 (because Windows will probably be blocked 127.0.0.1 for Docker).  So something like ``` http://123.456.78.910:8888/?token=fa13464756954b325753106b75c8398c991ce9d05ff523de ```

* Paste the modified URL into your Browser to get to the Docker image Jupyter notebook.

### Documenting your Projects

We've provided a template in a submodule of this repository. You can fork this submodule to start your own project to record your hackathon work! [Check it out here](https://github.com/Sage-Bionetworks/GoodDocData/blob/master).
