---
title: Setting up Quartz, Obsidian and GitHub Pages
draft: false
tags:
  - tutorial
enableToc: true
---
In this article I'm going to walk through the steps to create a simple markdown based docs for people to write in and hit publish!  The steps below will lead to roughly replicating the same style of site you are currently on, with helpful tips towards simple customization.  
  
Note: I have set this up on a Linux System which runs the distro Pop OS 22.04 (which is based on Ubuntu 22.04). 
### The Basics  
[Download the Obsidian app](https://obsidian.md/download), it's available for Windows, MacOS and Linux.  Before we get into setting up Obsidian, we will first get Quartz from [here](https://github.com/jackyzha0/quartz). (I presume that you already have git in your system).  You would also need to install Node and npm. 

The steps, as mentioned in the [setting up](https://quartz.jzhao.xyz/) page: 
```bash
git clone https://github.com/jackyzha0/quartz.git
cd quartz
npm i
npx quartz create
```
Now, follow the steps below to get setup with Obsidian and Quartz: 
- Open your Obsidian app 
- If you are using Obsidian for the first time: 
	- It will prompt you to either "Create a new Vault" or to "Open an existing Vault". 
	- Click on "Open an existing Vault" 
	- Navigate to the Quartz directory cloned from GitHub and open :  **/quartz/content** 
- If you have an existing Obsidian Vault 
	- Click the top-right button, go to navigation pane 
	- At the bottom, you can click the button to navigate to open a new vault from an existing directory. 
	- Open the directory **/quartz/content**

### First Note 
If you've gotten through the previous section, you can now start creating markdown documents, and see how they are rendered as web pages, we will concern ourselves with styling in the later sections. 

You can start writing your first note, simply by creating a note within the /content directory (Note: Quartz will always expect pages to be rendered, to be placed within this directory).  
- One way is simply Ctrl+N - this would open a new note. 
- Alternatively, use Ctrl + P - this opens a command pane - and type "new", select "Create new note". 

Now, you can give any name you want for the note. The most important thing is to enable metadata for each note you create, this will give finer control on how the note should be rendered.  This is done as follows: 
```
Enter three dashes just below the header as follows: 
<Your-Note-Header> 
--- 
```

This will immediately bring up a property field, here, you can add properties, beyond the existing ones, such as *draft* (choose weather to render the note as web page or to remain hidden as a note) and *enableToC* (this enables Table of Content's as seen on the left hand side of the web page). Under the *title* property, you can specify the exact title of the web page (this can be same as the name of your note). 

For more specifics on editing markdown files, I suggest a quick run through of [how to use Obsidian to edit markdown](https://www.youtube.com/watch?v=fVMlUd9orf4).   
### Styling
*(Still being edited)* 

First things first, let's remove the quartz graph layout, it complicates the entire page. Here's how to do that: 

Open 
```
/quartz/quartz.layouy.ts 
```

 Comment out all instances of the following: 
```ts 
Component.Graph()
```
Yay! No more graph view. 

### Hosting 
In this section, we will talk about everything *free*[^1] hosting; from setting up a GitHub account along with GitHub Pages to deploying the website.    

Create a new repository, give it a name, and choose weather to keep it public / private. 

Then execute from within the **/quartz** directory the following : 
```bash 
# Set your origin url (currently it'll belong to the cloned repo)
git remote set-url origin git@github.com:jnx84/nairsnotes.git

# Run the following 
npx quartz sync --no-pull 
```

### References 
1. [isak's youtube tutorial](https://www.youtube.com/watch?v=zGFroBGud7w&t=322s) 

[^1]: Upto 2 GB of storage permitted under the *free* quota
