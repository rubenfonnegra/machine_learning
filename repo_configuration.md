
# Configuring the repository

In this section, you will learn how to configure the github repository in Colab. This will be useful to upload and follow your code up.
First, you will have to create an account in [github](https://github.com/) in case you don't have an account. Otherwise, you can jump to step 1

## Step 1: Fork the couse repository

You will have to fork the repository in order to introduce your own changes and updates. You can do this as follows: 

- Go to the [repository](https://github.com/rubenfonnegra/machine_learning) in Github, and click the fork button in the upper right corner of the page.
- Choose the owner of the repository. In case you belong to multiple organizations, choose your username. RECOMMENDED: Do not change your fork name.
- Click on "create fork".

**Note**: In case you need more information, visit this [link](https://docs.github.com/es/get-started/quickstart/fork-a-repo#propose-changes-to-someone-elses-project) 


## Step 2: Clone your forked repository.

- Go to your [Drive](https://drive.google.com/drive/u/0/my-drive), create a Colab notebook and open it.
- Mount your drive and navigate to the directory where you want to download your forked repository using the ```cd``` command.

```
%cd /content/drive/path/to/your/folder/ 
```

- Go to your fork in your github profile (github.com/<your_username>/machine_learning).
- In the upper right corner, clic in "<> Code"
- Copy the url that appears in the https section in the window. 
- Go back to your notebook and run the following command

```
!git clone github.com/<your_username>/machine_learning
```

- Navigate inside the repository using the ```cd``` command.

```
%cd machine_learning/ 
```

**Note**: In case you need more information, visit this [link](https://docs.github.com/es/get-started/quickstart/fork-a-repo#propose-changes-to-someone-elses-project) 

## Step 3: Dealing with your repository

- Move the notebook you created inside the ```Sem_1``` folder.
- Create a new section within your notebook to configure your fork.


