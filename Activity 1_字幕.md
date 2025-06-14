Activity 1-- Reviewing the PeopleSoft Application Development Process. In this activity, we'll review the activity overview and review the eight steps of application development using the Training Tasks application as an example.

Activity overview. In this activity, you will review the eight steps of PeopleSoft application development, looking at specific examples of how those steps were implemented to create the Training Tasks application. In the process, you will consider how PeopleCode can be used to enhance and complete the application.

Activity detailed steps. Perform the detailed steps to complete the activity. Reviewing the application development process. To review, the eight steps of PeopleSoft application development-- plan the application, define the fields, define the records, build the tables, define pages, define components, register components, test the application. And each of these will be covered in more detail in these following sections.

Step number 1 will be planning the application. This is probably the most difficult step in the entire process. Fortunately, our application has been designed for us. First thing they're going to want us to do is launch the PeopleSoft Application Designer in two-tier mode. So we'll open up the PeopleTools folder on the desktop, double-click App Designer, ensure that the connection type is Oracle, ensure that the database name is T1B85701, and the user ID and password will be PTCODE.

So we go to our desktop and open up the folder called PeopleTools. And here you'll see the Application Designer. Before I go into it, I am going to do a couple of additional steps. I'm going to right-click on the Application Designer and send this to my desktop. Just gives me one less step to do each day to open it up. And I'm going to double-click on the Configuration Manager. And I'm going to change that user ID to be PTCODE.

I'll hit OK. And I'll close this folder, open up my Application Designer. And you can see we've defaulted our PTCODE here. We're coming in in two-tier, Oracle, T1B85701 for the database, user ID and password of PTCODE. Come back over here to our guide.

It says, to increase the workspace area, dismiss the Property window by selecting View Property Window or pressing Alt-2, which acts as a toggle key. Note-- to disable the property window, select Tools, Options, General tab, and then deselect the Enable Property Window checkbox. For the settings to take effect, you'll need to close the Application Designer and then open it.

And we'll do that in a few moments. But for now, if I just come over to my Application Designer, I'll do an ALT-2, and that will temporarily close it or close it just for this one session. Open the PSU_TASKS project. This will make access to objects easier as we discuss them. So if I come over here, I'll say Open Project. And I'll say PSU_TASKS task. And I'll say Open.

And we can see our different definitions that are in this project-- Components, Fields, Pages, and Records. From the menu, select Tools, Options. In the Insert Definition into Project Group box, select the "When definition is modified and saved or deleted" option. And select the "Reload last project at startup" checkbox. So if I come over to our project, go to Tools, choose Options, I'll select the radio button "When definition is modified, saved, or deleted." And I'll select the checkbox that says "Reload last project at startup."

In addition, I'm going to come over here to the General tab. And I'm going to deselect the checkbox that says Enable Property Window. So that way, I won't have to do the ALT-2 every time I sign in. And if I hit OK, now I've got my project option set up for me. Here I can look inside my project for the different definitions that we have in here.

So you see we've got Components, Fields, Pages, and Records. The nice thing about planning this one out, this project has already been created for us. So here you can see we've got the PSU_TASKS project. We're just going to be making some changes to it.

Oracle University has asked for an application to assist in tracking curriculum development projects. Each project comprises multiple tasks. And each task may be assigned to one or more resources. They want us to record the dates and numbers of hours expended on that date for each resource assigned to a task. Since tasks can be determined in advance of resource allocation, they want the ability to track a task and its data separately from the resources that are assigned to it.

So that's some of the things that we'll be doing in here. And you can see the Records, the Components, the Pages are out here. But we will be adding some PeopleCode to get the job done.

Defining fields. In the project workspace, expand the Field folder. We'll open up the TASK_STATUS field by double-clicking it. Field characteristics are global and are defined in the field definition, not in the record definition. Change any field characteristic, and it will automatically be changed in every record in which that field is used.

Select the Properties button to look at the translate values for a field. So if we come over here and take a look at our TASK_STATUS field if I double-click it to open it up, here you'll notice when I come in here that this is a character field. Maximum length of this is 1. And here you can see in the grid, we only have one label. Label is what we'll see when it gets rendered on a page.

And you can see we have label ID-- unique identifier of the label-- and then you've got a long name and short name. Developers can pick which one they want to use on a page. In this case, both of these I have the same name-- TASK_STATUS. And it is the default label. It's the only label. You see format. The data is always going to be in uppercase.

If we wanted to look at the properties for this field, I could go to my Toolbar, and I could click on the finger that points that looks like a page. That takes me into Properties. If I click on the Properties, the General tab is where I can do documentation.

And then you see we've got the Translate Values tab, where I can see the valid values for this field. So this particular field is validating to the PS [INAUDIBLE] Item table. And you can see that the values have the effective date of 01/01/1901. Typically means this was delivered by PeopleSoft, and these values should always be available. You see when we select a value, you see the code that will be written to the database-- A for Assigned, or C for Completed, or S for Started, are U for Unassigned.









And I'll close this Field Definition window again. Come back over here to our activity guide. Defining records. So open the PSU_TASK_RSRC record definition. Paged down a little bit too far on that.

It says, open the PSU_TASK_RSRC record definition. Notice that the default display is the Field Display. And select the Use Display button on the Toolbar. So if I come back over here, and I open up my record PSU_TASK_RSRC, sure enough, when I come inside here you'll see that we are looking at the view of the Field Display showing me the field attributes coming from field definitions. So when we create a record definition, it is a blueprint for creating a table. And when we create it, we tell it fields that we want to use. These fields will become columns when we're creating a SQL table.

if I click on the Next icon beside it, the one with a picture of a key, it takes me into the Use Display. In here I can take a look at the properties here. This is where we'd set up what's going to be the keys. Keys are going to be used to determine unique row of data. So here we see this is keyed by task and resource name. And they are ascending keys.

We could set up search keys, alternates, and list box, if it's going to be used as a search page or a prompt table lookup. This record, this one doesn't have any search keys, alternates, or list box set up on it.

It says, double-click the RESOURCE_NAME and notice the default. So if we come over here and take a look at that, if I come over here to the RESOURCE_NAME, double-click to go into its Record Field Properties, we see it's a key, but notice for default value it says it goes to RESOURCE_NAME PSU_INSTR_NM_VW. Field name is RESOURCE_NAME.

So here in this case, you see that we are opening up a view to be able to display data. So this is going to be a view with some SQL behind it to tell us what's going to be brought in here by default. And we see that this one is a key.

You'll notice it says double-click instructor. Click the Edit tab and notice the table edit is defined for this field. So if I come in here and I double-click on instructor, instructor is not a key. And if I come over to the Edit tab, notice it has a Prompt Table Edit. So it prompts to the PSU_INSTR table.

Well, in this application for task resources, this is where we're assigning the resources that are going to work on the task. Maybe the task is we want to create a trucking application for trucks that are coming and going. Or maybe in this case, we're creating a application to keep up with how much time is being spent on a development project.

Well, when we're doing that, we are wanting to log certain data, like who is working on this application or this component, where we're tracking the people working on the project. So in here, you see it's keyed by the task what's the project that they're working on. Maybe they're doing a fleet maintenance system, or maybe they're creating whatever type task. Maybe this is to write the book for PeopleTools. So whatever the task might be.

And then you see after that, the key is RESOURCE_NAME. The key is not the instructor. It's the resource name. Now, probably most of the time the person that's going to be the resource name is going to be an instructor. But not always. So we can have resources who are not instructors.

So in this case, these tasks here are going to be used for keeping up with training. This task here might be for working on one of the training courses that we are developing-- maybe PeopleSoft Fluid User Interface. So who's the people in the company who's going to work on this task?

So when it comes to it, you'll have instructors working on it. So instructors would work on it to verify the correct information is going into it. But there'd be other people work on it. You'd have the DBA working on being able to set up the database that will be used for the training course. You'd have the technical writers who actually put the information into the guide.

So not everybody who works on setting up a training course information would necessarily be an instructor. But they are a resource. So it might be where we can go out here and pick the instructor from the instructor table, and it would filter and put in the name of the instructor as the resource name. Or we could just type in a resource name in the case that they're not an instructor. Notice the instructor field is not required.









Open the PSU_TASK_EFFORT record definition. And notice that the common key fields-- TASK and RESOURCE_NAME-- between this child and its parent record, PSU_TASK_RSRC. So if I go into the TASK_EFFORT, we open this record definition. And if we take a look at this one, especially if we look at the Use Display, I see this is keyed by task, resource name, and effort date.

So that indicates to me that this is a child of the PSU_TASK_RSRC. So this is going to be used where we're going to track how many hours is a resource spending working on this task. So they're writing the PeopleSoft Fluid User Interface. How many hours have they put into this? And when did they work on it? Remember, to be a child table you've got to have the same keys as your parent, with at least one additional key.

Building the SQL table. Building a database tables is the most frequently forgotten step. So when you're creating a new application, you'll generally be creating a new table. So don't forget to build the table, step number 4. Now, if I was building this, I'd be going up there and say Build, Current Definition. And I would tell it to create the table and execute the SQL now or execute and build the script.

I'm not going to do that. Because if the tape already exists, which it does in our training environment, it would drop the table, meaning I would lose all my data. Not a good thing to do right here.

Defining pages to view page definitions. We're going to open up the PSU_TASK_RESOURCES page. And we'll select the Order tab to notice the Allow Deferred Processing column. Even if it is selected here, you must enable deferred processing at the component level.

So if we come back over and open up our PSU_TASK_RESOURCES page, and here you can see the record fields we have listed on here. So you see we've got a level 0, a level 1, and a level 2 listed on this page. And if I come over here and go to my properties, if I go to my Use tab, here you can see that this one has been set to allow for deferred processing.

Now, as the book mentioned this is initially going to be set up at the component level. If the component has it said to say that it's going to run in interactive mode, then it doesn't matter what the page says. So the page could say Allow Deferred, but it would still be running in interactive mode. If the component says run in deferred mode, then it defers it to the page.

And here you could see that it would look here to say, OK, how do I run this particular page that's inside the component? And you can see that this one is set to be run in deferred processing. It it's set to be run in deferred processing, then it defers the processing to the controls on the page.

If I cancel here and I go to this Order tab, here you can see the different record fields that are on this page. You see at level 0, we're pulling from the PSU_TASKS table. Level 1 is pulling from the PSU_TASK_RSRC. And level 2 is pulling from the PSU_TASK_EFFORT. And if you look over here, you see all these fields are allowing deferred processing.

Again, before these controls would work, it would be dependent upon the page. If the page didn't allow deferred processing, then it doesn't matter what the field says. Everything's going to run interactive. If the page says allow deferred processing, we've got to go back to the component. If the component says run interactive, it don't care what the page says. It runs everything interactive. But if it says deferred, then it uses the deferred processing. So first it checks the component, then the page, and then the fields.

Next step would be defining the component. So if we open up the TASK_RESOURCES component, open up the Components properties. Component properties are accessible only when the Definition tab is in the active tab. Select the Internet tab and notice the Processing Mode choices, Deferred and Interactive. We'll spend more time on deferred processing later.

Close the component properties, and then look at the Structure tab and note the hierarchy. So if we come back over here and look at our component that we're looking at inside here, so if I open up my PSU_TASK_RESOURCES component, and if I'm looking at the Definition tab, here you see the item label. That's the name of the tabs on the pages.

If I go over here to my properties of my component, we have the General tab where we can set up documentation. Here you see the Use tab, where one of the things we tell it is the search record. So this was the search records used to build the search page of the component. We tell it the actions.

If I go to the Internet tab listed inside here, over here on the right you'll see over here under Processing Mode, interactive or deferred. If the component is set to deferred mode, it's deferring the processing to the page. If the page is set to deferred, then it's deferring the process to the page controls.

If I click on the Structure tab, here I can see this hierarchy levels over here. So here you see our search record pulled from PSU_TASKS table. Then we have a level 0 pulling data from PSU_TASKS table, a level 1 scroll area pulling from the PSU_TASK_RSRC resources table. And then we have a level 2 PSU_TASK_EFFORT pulling from the PSU_TASK_EFFORT table.






Registering the component. The Component Registration Wizard attaches components to menu definitions, assigns security access for users, and places navigational links in the registry. You won't need to use the Component Registration Wizard in this course. Everything we're working with has already been registered.

But when we register our component, it places it on a menu in the Application Designer. That's the placeholder for finding the component for security or for the user navigation in the PIA. It adds a content reference into an existing folder in the portal registry that is the user navigation in the PIA. And it grants authorization to an existing permission list for that component.

Testing the application. To test the application, we're going to launch a web browser by double-clicking the T1B85701 icon on the desktop and sign into the PeopleSoft system as PTCODE. So if we come back over here to our desktop, double-click on T1B85701, log in. And I'll say let's log in here as our PTCODE.

And once we log into PTCODE, it tells us, from the Navigator, select Setup Training, Training Tasks, Task Table to access the Tasks page. So from the nav bar, I'm going to come in here and go to my Navigator. I'll go to Setup Training. I'll go into Training Tasks.

And then I'll come in here and select my Task Table to be able to look at tasks that are out here. And if I do a search, you can see we have the following five tasks that are out here-- PeopleTools Training Guide, PeopleTools 8.4 Live Webcast, PeopleTools 2 Training Guide, PeopleTools 8.2 Delta, Task 11, New Integration Technologies. So these are the different tasks that we have currently already out here.

But I could go out here, and I could go in and add a new task. I can say, let's add task-- maybe I'll name this one 000-- about two 0's, 55. Click on Add. And here I could give it a description. I could say, PeopleSoft Fluid User-- I'll just say "User Guide." Short description. I'll call this one-- how about FLUID?

Effort, total effort hours spent. I'll say that maybe we're going to assume that this is going to take maybe about 2,000 hours to get this completed. It might be a little much. Let's do a thousand hours. None has been spent so far. So the start date of when do we predict that people will start working on this one, we'll just set it to today.

Effort spent so far working on the guide, none. We're just now creating the task. When do we hope to have this ended? So this one right here will be when the project is completed. Task status, currently it is unassigned. We haven't assigned anyone to work on it yet. So here I can save it and take a look at this task.

If I go back to my Search page by hitting F5, I could look at a task that already exists, like task 1. So here you see PeopleTools 1 Training Guide, PT 1 Guide; effort total hours, 1,200; start date; you see the effort spent so far is 480; and it says the end date was June 23, 2002. And it has been completed.

It says, from the Navigator select Task Resources and Efforts to access the Task Resources page. So if I come in here and go back to my Navigator and go back to the Task Resource and Effort content Reference and because I already had it loaded in the component buffer, it defaulted to task 1. So here I can see we have four people who have worked on this PeopleTools 1 task so far.

You see we've got Ed 50% available. And he's finished with the task. And here's the data that he has worked on the information. And if I come through here, you can see we have Jim Guss, we have Joe Yang, Scott Sanchez. So we see the different roles that are out here.










If I return to Search, I could come over here and to my task. And I could say, let's assign someone to work on this. So I could say, let's go out here and I'll assign an instructor to work on this one. I'll say he's 25% available. And I'll say he hasn't actually done anything yet. So I'll just hit Save.

And now I've assigned someone to work on this right now. Now, keep in mind I probably should go back to the task and say we've assigned someone. Or maybe we should have code that once you've assigned someone that it automatically changes the radio button on the other page. So this is an example where we might need some PeopleCode out there.

The other thing is, when I set up effort date, and amount, and charge back, maybe I need to go out there to the parent page, the Task page, and update the amount of hours that have been worked out there. If I'm looking over here, and I return to my search, and I look at these tasks, we might want to make sure that the hours that you see added up on all these tasks for all the people that's worked on this resource, we probably ought to make sure that they equal the charge back that we see over here on the Task table, the amount of hours worked. So here we probably ought to verify that those are in sync with each other. Set up PeopleCode to keep them in sync.

And we added a new task. Associate resource and efforts to the new task, including insertions, and deletions in both scrolls. That is, add a resource to the new task and add multiple effort amounts to that resource. So if I come back over here, and I'll just go back to the one I did, come back in here to 55.

Let me come back in here and go to the right place I want to do. I'm going come back in here and go to my Navigator, go to Task Resources and Efforts. And maybe now on Effort Date, we'll say-- I'll just make up a date here-- effort amount, I put in eight hours of effort in here. Charge that information back.

And maybe we also went in here on the 6th, and we put in another two hours. Charge it back. And if I save this, now I've got 10 hours in here. Maybe I'll add another resource worked on this as well.

So I'll say, let's also say we got a resource-- I'll add another resources in here. And I'll say 10% available. And on this date, they worked two hours. And I'll save it. So I've set up multiple rows here.

Now if I come back over here and take a look at my Task table, and if I come in there and I look at this task that we just looked, notice it didn't update the hours. So here I can come in here and I could say, how about I got 876 hours, and I could save that. Well, that's bad, because that's not true. Right now we've got 12 hours. So that's something maybe I need to think about here.

Maybe I'll say, we completed this one on 01/01/2019. You're like, wait a minute. You shouldn't do that, because you didn't start till 3/18/20. Oh, maybe I need some PeopleCode here. It's allowing me to put in a date that ends before the start date-- bad. It allows me to put in hours spent that is more than what's actually been spent.

I could come over here, and maybe I can put 1,876 hours. Bad-- bad, bad, bad. Now I've went over the total hours allocated that can be used. So you see we got some opportunities that we might come out here and put in some PeopleCode to make this application work better.

Check your prompts, your defaults so we looked at prompts, for example, the instructor. We've seen the default values that come in on the options. This concludes the activity. Please do not continue.