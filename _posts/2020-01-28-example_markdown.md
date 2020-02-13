---
title: "Continuous delivery using Google App Engine"
date: 2018-01-28
tags: [data wrangling, data science, messy data]
header:
  image: "/images/perceptron/percept.jpg"
excerpt: "Data Wrangling, Data Science, Messy Data"
mathjax: "true"
---

In continuous delivery, code changes in the underlying pipeline can immediately trigger changes and updates to a running application. Google app engine  was used to build and deploy a web app. After, I tested the ability to make changes to the app file (main.py) and have these updates trigger and redploy an  updated web app. The purpose of the web application is to allow users to input a symptom for a condition or disease they are interested in, and the application will give a diagnosis and return a list of possible causes.

Google's App Engine was used to build and deploy a web application using the key files:

-*main.py* : primary Flask application   
-*app.yaml* :  specifies the python runtime  
-*requirements.txt* : additional packages that need to be installed  
-*cleaned.csv* : contains symptoms and diagnosis data. This was pulled from kaggle (https://www.kaggle.com/plarmuseau/sdsort).   
-*cloudbuild.yaml* : builds the application  

To see a demo of this web app, view the demo mp4 video.[(link)](https://github.com/jtwang1027/contint)
