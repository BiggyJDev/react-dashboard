# React-Dashboard App

This build has come from JavaScript Mastery. I do not want to follow this tutorial blindly so here I will annote what we have done to get to the finished product.

# The Setup

First we created a react app and deleted the entire src folder to clean up the applications. Once we had done this we created a new src folder and added the index.js file and App.js file.

For this build we are going to be using alot of Sync Fusion so to make sure this build works we are going to get the dependancies from the JS Mastery Repo so we have exact versions we need.

Once we have added these dependances we need to go to the command line and install these dependances, we can do this using the command

npm install --legacy-peer-deps

## Styles

As this tutorial is focused soley on the React build we will also be utilising the pre-made styles from the JS Mastery Repo.

The first of the styles file is the index.css

Within this file we are

1. Importing the font we need from google fonts
2. Resetting the margin and padding within the body and setting the default font to Open Sans - The one we imported from google fonts
3. Lastly we are importing tailwind

The second styles file we are copying is the App.css file.

As we can see from the index.css we are going to be using Tailwind in this build so to get Tailwind up and running we have a couple task to complete.

Firstly in our root directory so outside the src folder we need to create a tailwind.config.js file

This config file will contain a quick tailwind set up which includes some fonts, fontsizes, colors, border options etc...

Next we have to create a craco.config.js file, I will openly admit I am not 100% as to what this file does but I will do some research :)

# Test the set up

Now I believe the set up is complete I need to perform some tests.

The main test is to make sure our CSS framework Tailwind has been set up correctly. To check this, in our App.js I am going to try render a h1 with some tailwind styling.

The test failed. Now to find out why Tailwind is not working correctly.

A silly mistake, I accidently created the config files outside of our root directory

# File Structure

Now we have our app initialised we need to create our file structure. As this application is quite large in size and contains many stand-alone files, our file structure is crucial.

Firstly we need to create out components folder. Next we need to create a Contexts folder, this will use our React Context API. I have never used the React Context API before, so this will be a first and another opportunity to learn. I'm looking forward to this! :)

Next we need to create a Pages folder, unlike components where a component can not be used inside another component. We will create a page which will contain multiple components

Components -> Pages -> Applications

Lastly we have the data folder, this will contain images and demo-data for running our application. This folder has been pulled from the JS Mastery Repo as it contains all the data we need for this build.

In the data file we have some fake images for people and products. Alongside this we also have a dummy.js file which holds lots of dummy data we can use in this project
