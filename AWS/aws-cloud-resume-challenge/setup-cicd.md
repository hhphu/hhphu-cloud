# Setting CI/CD for Front End using Github Actions

![image](https://github.com/hhphu/Cloud/assets/45286750/5a743c6b-f168-49d9-844c-a99b7cde58f1)

# INTRODUCTION
This blog post go through Continuous Integration & Continuous Deployment (CI/CD) for our website. Everytime I make changes to my website, I automate GitHub to deploy the changes to S3 bucket.
In other words, we don't have to log in AWS console and reupload files everytime we make changes.

# Create Git repository for our website
- On Github, create a new repository for the website.
- Inside the repository, create a folder `.github/workflows`
- Go into the `workflows` folder and create a yaml file for GitHub Action. The structure should look like this.

![image](https://github.com/hhphu/Cloud/assets/45286750/9dbb4422-bf51-4dcf-8c4c-2d0cecb63c1c)

