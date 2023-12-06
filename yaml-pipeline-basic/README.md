![TechSlate](../global/images/ts.png)

# **Running a Sample Yaml Pipeline in Azure DevOps**

# Table of contents
1.[Introduction](#**<Introduction>**)

2.[Prerequisites](#**<Pre-requisites>**)

3.[Running a Sample Yaml Pipeline in Azure DevOps](#how-to-run-a-sample-yaml-pipeline-in-azure-devops)


## **Introduction**

### **What is Azure DevOps**

Azure DevOps is a set of development tools and services offered by Microsoft as part of the Azure cloud platform. It provides a comprehensive set of features to support the entire DevOps lifecycle, from planning and coding to building, testing, and deploying applications. Azure DevOps aims to help development teams collaborate effectively and deliver high-quality software faster.

### **What is Yaml Pipeline**
A YAML pipeline typically refers to a configuration file written in YAML (YAML Ain't Markup Language) that defines a continuous integration/continuous deployment (CI/CD) pipeline for software development. YAML is a human-readable data serialization format, and it's commonly used to define configuration settings in a concise and easy-to-read manner.

***

## **Pre-requisites**

1.**Create Azure DevOps Account and make sure pipelines are all set to run**

2.**Install Visual Studio**

***

# **How to Run a Sample Yaml Pipeline in Azure DevOps**

Now, First we will clone the repository **ADO-BASIC-PIPELINE** in local Visual Studio Code.


### **1. Open your Visual Studio Code.**
![Visual studio page](../global/images/vscodepage.png)
***

### **2. Now open the Terminal and do Git Clone.**

![Visual studio page](../global/images/git-clone.png)


### **3. Now , you have to see your reposirtory appearing on left side of the panel and checkout the code Pipeline-basic.yaml** .

![Visual studio page](../global/images/pipeline.png)

***

### **4. Now , Open the Azure DevOps URL - dev.azure.com . Azure DevOps is a tool where we run the pipeline . So before we run pipeline we need to import respository here in Azure DevOps** .

![Visual studio page](../global/images/az.png)

### **4. Now , give the respevtive URL of the repository and click on import** .

![Visual studio page](../global/images/import.png)

### **5. We can see that , repository is imported successfully !** .

![Visual studio page](../global/images/success.png)

### **5. Now click on the pipeline to start the  process of running pipeline .**

![Visual studio page](../global/images/pipe2.png)

### **6. Click on Azure Repos Git .**

![Visual studio page](../global/images/az-git.png)

### **7. Select the respective repostory of yours which you have imported.**

![Visual studio page](../global/images/repo.png)

### **8. Click on Existing Azure Pipeline YAML file**

![Visual studio page](../global/images/starter.png)

### **9. So here , select the path of your pipeline**

![Visual studio page](../global/images/branch.png)

### **10. Now click on Run**

![Visual studio page](../global/images/run.png)

### **11. So , the pipeline started running , lets wait until it completes**

![Visual studio page](../global/images/start.png)

### **11. Pipeline is successfully running**

![Visual studio page](../global/images/running.png)

***

### **12. Now , lets explore and try to run YAML Pipeline with Variables**

![Visual studio page](../global/images/variables.png)

### **13. Copy that code we shall replace that in pipeline-basic.yaml . so from 11th line just remove previous code and paste the code that we have taken from README.md**

![Visual studio page](../global/images/cut.png)

### **14. Once replaced click on commit .**
![Visual studio page](../global/images/replaced.png)

### **15. So, Once commited just come back to the pipeline and click on New pipeline and you can see that their is one variable mentioned in the script i.e., myurl . we need to add varible up their with name myurl.**

![Visual studio page](../global/images/var.png)

![Visual studio page](../global/images/myurl.png)

### **16. Once variables added , Click on Run .**
![Visual studio page](../global/images/run1.png)

### **17. Pipeline started running .**
![Visual studio page](../global/images/re-run.png)

### **17.Successfully Running .**
![Visual studio page](../global/images/running2.png)

***

### **18. As we have tried with variables, Now lets explore and try to run YAML Pipeline with Group Variables**

![Visual studio page](../global/images/grp-var.png)

### **19. Copy that code we shall replace that in pipeline-basic.yaml . so from 11th line just remove previous code and paste the code that we have taken from README.md**

![Visual studio page](../global/images/add.png)

### **21. Once replaced click on commit .**
![Visual studio page](../global/images/commit.png)

### **22. Now lets add group variables in Library which are mentioned in the Script .**
![Visual studio page](../global/images/dev-prod.png)

### **23. Click on the Pipelines and select Library.**
![Visual studio page](../global/images/lib.png)

### **24. Create Variable Group with name "env-dev" and Add URL & KEY with respective values**.
![Visual studio page](../global/images/env-dev.png)

### **25. Create another Variable Group with name "env-prod" and Add URL & KEY with respective values**.
![Visual studio page](../global/images/env-prod.png)

### **26. Once Group variables assigned , now run the pipeline , while you are running it will ask you to permit it before running , click on permit**.
![Visual studio page](../global/images/permit.png)

### **27. As Dev is successfully ran , its asking to permit for prod**.
![Visual studio page](../global/images/permit2.png)


### **27. Pipeline is running successfully**.
![Visual studio page](../global/images/done.png)

***