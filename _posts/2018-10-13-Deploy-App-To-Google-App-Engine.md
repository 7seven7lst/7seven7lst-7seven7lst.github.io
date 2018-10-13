---
layout: post
title: Deploy Web app to Google App Engine!
---

Deploy NodeJS App to Google App Engine.

* Create a new project
1. Navigate to [Google Cloud Dashboard](https://console.cloud.google.com/home/dashboard)
2. Click "New Project" ![Create New Project]({{ site.baseurl }}/images/deploy_gcp_nodejs/create_new_project.png "Create New Project")
3. Give project a name, and click "Create" ![New Project Created]({{ site.baseurl }}/images/deploy_gcp_nodejs/new_project_name.png "New Project Created")
* Create a skeleton NodeJS webapp
1. create a skeleton NodeJS webapp (express) with the following file structure: ![NodeJS skeleton]({{ site.baseurl }}/images/deploy_gcp_nodejs/nodejs_skeleton.png "NodeJS skeleton")
2. In `package.json` file, make sure to specify the node version ![Specify NodeJS version]({{ site.baseurl }}/images/deploy_gcp_nodejs/nodejs_version.png "Specify NodeJS version")
3. In `package.json` file, include the following for google cloud related testing ![Google cloud related tools]({{ site.baseurl }}/images/deploy_gcp_nodejs/gcp_tools.png "Google cloud related tools")
4. In `app.yaml` file, specify the NodeJS version ![Specify NodeJS version in YAML]({{ site.baseurl }}/images/deploy_gcp_nodejs/nodejs_version_yaml.png "Specify NodeJS version in YAML")
5. An example app can be found at [This Repo](https://github.com/7seven7lst/nodejs-gcp)
6. To get this app running in local ( assuming you have the correct NodeJS version installed),do `yarn install`, `yarn start`, and navigate to [Localhost](http://localhost:3001) to see the result
* Getting ready to deploy to Google App Engine
1. If you are using a Mac, go to [Google SDK](https://cloud.google.com/sdk/docs/quickstart-macos) to download the google cloud sdk ![Dowanload Google Cloud SDK]({{ site.baseurl }}/images/deploy_gcp_nodejs/download_gcloud_sdk.png "Dowanload Google Cloud SDK")
2. In terminal, install the sdk by running: `{LOCATION_OF_DOWNLOADED_SDK}/google-cloud-sdk/install.sh`
3. Restart the terminal to pick up the change
4. cd into the NodeJS webapp directory, and do `glcoud init` to initialize the gcloud config
5. Create a new configuration or chose existing configuration ![Create or choose gcloud configuration]({{ site.baseurl }}/images/deploy_gcp_nodejs/gcloud_config.png "Create or choose gcloud configuration")
6. Choose an existing gcloud account ![Choose an existing gcloud account]({{ site.baseurl }}/images/deploy_gcp_nodejs/choose_gcloud_account.png "Choose an existing gcloud account")
* Deploy app to Google App Engine
1. Enter `gcloud app deploy` and choose a region ![Chooseing a deployment region]({{ site.baseurl }}/images/deploy_gcp_nodejs/choose_deployment_region.png "Chooseing a deployment region")
2. confirm deployment summary ![Confirm deployment summary]({{ site.baseurl }}/images/deploy_gcp_nodejs/confirm_deployment_summary.png "Confirm deployment summary")
3. It will show deployment is in progress ![Deployment in progress]({{ site.baseurl }}/images/deploy_gcp_nodejs/deployment_in_progress.png "Deployment in progress")
4. It will finish deploying the app in some time. Based on the information provided, you can navigate to `https://<app_project_id>.appspot.com` to access the web app. [Here is mine](https://nodejs-demo-218704.appspot.com)



