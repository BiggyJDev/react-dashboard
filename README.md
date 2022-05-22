# React-Dashboard App

This build has come from JavaScript Mastery. I do not want to follow this tutorial blindly so here I will annote what we have done to get to the finished product.

# Useful Links

- [SyncFusion Documentation](https://ej2.syncfusion.com/react/documentation/introduction/)
- [React Router DOM Documentation](https://github.com/remix-run/react-router/blob/main/docs/getting-started/tutorial.md)
- [Tailwind Documentation](https://tailwindcss.com/docs/installation)

# The Setup

First we created a react app and deleted the entire src folder to clean up the applications. Once we had done this we created a new src folder and added the index.js file and App.js file.

For this build we are going to be using alot of Sync Fusion so to make sure this build works we are going to get the dependancies from the JS Mastery Repo so we have exact versions we need.

Once we have added these dependances we need to go to the command line and install these dependances, we can do this using the command

`npm install --legacy-peer-deps`

# Styles

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

# Lets get started!

## App.js

So the first bit of coding we will do to start the app off happens in the App.js file.

Here we will import a few components from React-Router-Dom, React-Icons, and @Syncfusion.

Alongside this we will import the useEffect hook to utilise later on.

So the code...

First we need to use the BrowerRouter component and inside this we will have a few things.

1. A div with the class that defines it being flex with a postion relative. We will also add that in dark mode we want the background to be the main-dark-bg we set in our tailwind config file
2. Inside that div we have another div which has some inline styling to make sure it appears above everything else.
3. Inside that div we will use our first component from @SyncFusion. This component is the Tooltip component, we have set the contents to settings and the position as Top.

The Contents prop is a string that is displayed when we hover over the icon.

Finally to give our ToolTip Component something to render to the DOM we will have a button inside of this that contains an Icon from react-icons

With our button we need to add a bit of styling. The styles we have used make the button larger and gives it a drop shadow and Background color change on hover. For development purposes we are going to set the background color to blue, however this will not be forever as we are going to give the user an option of which theme they would like there dashboard to be in. We have also give the button a border radius of 50% so it is now a circle

### Sidebar

Within App.js the settings icon when clicked will open a side bar. To implement a side bar we are going to use a ternary operator so if the sidebar is 'active' we will display, if it is 'not active' we will set the width to 0 so it is not visable

### Navigation Bar

For our Navigation bar we are creating a div that will have different styling depenedant on its state . The orginal code is very repetative so we refactored it so we can follow the DRY coding practice.

The orginal code was:

`<div className={ activeMenu ? "dark:bg-main-bg bg-main-bg min-h-screen md:ml-72 w-full" : "dark:bg-main-bg bg-main-bg min-h-screen w-full flex-2" } > Navigation bar </div>`

As we can see the styling is pretty much the same across both states bar one piece of styling.

The refactored code is

` <div className={`dark:bg-main-bg bg-main-bg min-h-screen w-full ${
activeMenu ? "md:ml-72" : "flex-2"
}`} > Navigation bar </div>`

Inside the Nav container we have created another div which has a fixed position. This div will eventually contain our Navbar Component

### Routing

Below our Nav bar we have started to code our routing table. Here we are using React-Router-DOM so our 'links' are contained in a single Component named Routes and each 'link' is a self closing Route which contains a path and Element to be displayed. At the current moment we have set them to Hard coded text but these will be replaced with components later down the line

`<Routes> <Route path = '/' Element ='Home'> </Routes> `

## Finalising the File Structure

### Components

The boiler plate we will be using for our components is generated using 'rafce'.

This creates a simple Arrow function which also imports React and Exports our Component

Inside our Components Folder we have another folder named Charts - This will store all our charts.

Component wise we have around 12 components we will be working with.

The index.js component is there so we can import all our components by just using one line. This component has been copied from the JS Mastery Repo

### Pages

The pages have the same structure as the Components folder, except for the index.js in the pages I have coded that myself

### Importing into App.js

Now we have Pages and Components set up we can start importing them into our App.js file.

We can import all our Components/Pages through a destructured assignment because of the index.js file we made each folder

### Utilising our new components.

Now we have our Components and Pages imported we can go back and remove our hard coded text and replace them with the relevant component

# The Application

## Sidebar

Let's get started on the sidebar

First we need to be able to switch between different pages in our application, so we need to import both Link and NavLink from React-Router-DOM. Alongside the navigation we need a few icons and the Tooltip Component from @SyncFusion. Lastly we will need some data to work with so we will import the links from ../data/dummy

Our side bar is going to be affected by state so whilst we develop it we are going to create a dummy state and set the activeMenu = true

For this side bar we are going to be using a lot of logic, hence why we have the dummy data file imported.

We start our Sidebar off with a div that is styled to fill the screen and control the overflow.

Within this div we have our first logical statement, this checks to see if the activeMenu is true and if it is true it will display a react fragment which contains:

1. A div that contains

- The heading for the nav bar
- An exit button if the application is loaded on devices of medium width or less

2. A div that contain:

- The title and Logo that is mapped from the dummy data file

For the title of each section we map the links we imported earlier mapping each object to an 'item'..

We then generate the title by looping through the data file displaying each item.title inside of a p tag

For the actual link, we house this inside the NavLink component we imported from react-router-dom.

The destination of the link is given by a template literal string `./{Link.name}`.

The key is also assigned to Link.name so it is unique

The onClick function is not in use yet, we will use that later, so it is set to an empty callback function.

With the styling we have used some Logic: We want to change the styling of the link dependant on whether it is active or not. The styling has been stored in two variables to keep our code clean. We have activeLink and normalLink

Inside the NavLink we need to render something, we do thisby using our mapped data by rendering the Link.icon and a span tag that contains Link.name
