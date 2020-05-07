**[Steps to Automation or Continous Integration]{.underline}**

[**Step 1:**]{.underline} Create a new repo in github(e.g. activity1) &
initialize it with a local git repo.

![](media/image1.png){width="6.268055555555556in"
height="3.5256944444444445in"}

**[Step 2:]{.underline}** Create a file( e.g. index.html ) in local git
by appending data from 2 different branches (i.e. master & dev1).And
then we upload the data to the github by using commands given below:

1.  git add .

2.  git commit . -m "Comment"

3.  git push -u origin "branch\_name"

![](media/image2.png){width="6.268055555555556in"
height="3.5256944444444445in"}

![](media/image3.png){width="6.268055555555556in"
height="3.5256944444444445in"}

**[Step 3:]{.underline}** Now we create 3 jobs in our continuous
integration tool i.e. Jenkins

![](media/image4.png){width="6.268055555555556in"
height="3.5256944444444445in"}

**JOB 1 :** The duty of this job is to track the data of branch dev1
from the github.

![](media/image5.png){width="6.903873578302712in"
height="3.8833333333333333in"}

Further more deploy the data to testing environment by launching an OS
with the docker image of httpd.

![](media/image6.png){width="6.268055555555556in"
height="3.5256944444444445in"}

**JOB 2 :** The duty of this job is to fetch the data of the master
branch from github.

![](media/image7.png){width="6.268055555555556in"
height="3.5256944444444445in"}

And then we deploy the data to web server in the production environment
consisting of an docker image httpd OS & web server.

![](media/image8.png){width="6.268055555555556in"
height="3.5256944444444445in"}

**Note : Make sure both the environment i.e. testing & production should
be identical.**

**JOB 3 :** The duty of this job is to fetch the data from testing
environment & provide the certificate for the changes which is done by
dev1 branch & that certificate is provided by the Quality Assurance Team

![](media/image9.png){width="6.268055555555556in"
height="3.5256944444444445in"}

Behind the scene,this job will merge the data of dev1 branch with the
master branch.

![](media/image10.png){width="6.268055555555556in"
height="3.5256944444444445in"}

And finally we push that merged data to github (internally) which
triggers the activity1.2 automatically when this job is built. Hence the
data gets deployed to the production environment. In the end we check
the output manually of the jobs.

![](media/image11.png){width="6.268055555555556in"
height="3.5256944444444445in"}

**Note : Job Chaining must exist between the jobs .**

**[STEP 4:]{.underline}** Expose the data through PAT

In this step we perform the PAT concept to expose the docker OS data to
our base OS or third party OS i.e. (Windows , Mac etc.) by the help of
command

-pnew\_port:80

Here 80 is the default port no of Apache Web Server that we are using in
this operation.

![](media/image12.png){width="6.268055555555556in" height="4.375in"}

**[STEP 5:]{.underline}** Implementation of Tunnelling Concepts

In this step we perform tunnelling operation by ngrok for using our
application from client side.

Ngrok is the software which converts the private IP to public IP.

![](media/image13.PNG){width="6.268055555555556in"
height="3.7243055555555555in"}

![](media/image14.png){width="6.268055555555556in"
height="3.5256944444444445in"}
