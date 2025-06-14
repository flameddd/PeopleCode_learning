Activity 2-- Using the PeopleCode Editor. In this activity, we'll review the activity overview and try out some several features of the PeopleCode Editor.

Activity Overview. In this activity, you will use the PeopleCode Editor to write and change segments of PeopleCode and to observe several features of the editor, such as automatic formatting, syntax validation, and automatic backup.

Activity Detailed Steps. Perform the detailed steps to complete the activity.

Using the PeopleCode Editor. To launch the PeopleCode Editor, open any PeopleCode program. Open the PeopleCode program on the Record field PSU_STUDENT_TBL, SAME_ADDR_CUSTOMER.FieldChange. Use any of the techniques you have learned to open the program in the PeopleCode Editor.

So if we come over here and open up or App Designer, if I do a File, Open Record, and I say PSU_STUDENT_TBL. I'll open it up. And here we see the field Same Address as Customer. One method we could use is we could click on our PeopleCode display, and here you see the FieldChange. So I could go ahead and double-click on the FieldChange checkmark, and that would open up the PeopleCode Editor, with the focus on Same Address as Customer with the event called FieldChange.

It says, note that the text is color-coded. Select the dropdown on the left, and notice the current field. Fields that have PeopleCode, appear in bold type. Select the list on the right. Notice it displays the current PeopleCode event. Selecting it enables you to change events. Events with PeopleCode of programs appears in bold.

So if we take a look at this, I can see over here the color-coding. So you see comments are in one color. You see keywords are in blue. You see things that are in quotes would be in another color. And all that can be set up underneath your menu bar, underneath your Edit Display Fonts and Colors, which color you want things to show up as. So here you can see, I can set my Comments to be green. I can set up my quoted strings to be red. Get the idea.

If I come over here on the left, here you see all the fields that are in this record definition. Anything that is bold means it has PeopleCode applied to the Record field. And over here on the right, you see, I get the dropdown, and I see all the events. Any event that is bold means it has PeopleCode being applied to it.

Select a STUDENT_NAME field and select the FieldEdit event. The larger text editor area behaves like a standard text editor. So if we come over here and click on our dropdown over here on the left, and we'll choose the STUDENT_NAME, while on our right, we'll choose the event called FieldEdit. And it says, enter the following text into the text pane exactly as it's shown.

So if carat equals student_id, then warning "Student name equals student ID." And then put a semicolon; and hit the Save button. So we come over here and place this in. If I say, If and I use a caret. Caret says put in the record field that you're currently on, which would be the PSU_STUDENT_TBL.studentname, equals, and I could say student_id. I can list a different field that's in the same record, and automatically, it'll put the record name in front of it.

Then Warning, student name equals student ID. And it says to hit Save. When I hit Save, I should get an opportunity. Syntax error, expecting an if. If we have an If statement, then I also need to have an indent inserted inside here.

So when you Save or select the Validate syntax menu item, PeopleCode Editor checks the syntax and automatically forms them as the code 0 all syntax checking passes. Note you'll see a syntax error that indicates the And/If keyword is missing. The shame of it all.

Option number 8, add the following to the end of the same line and hyphen f with a semicolon and hit Save again. So now we come in here and say, and hyphen if semicolon. And if I hit Save, ah, no error. And notice what happens. It automatically goes out here and formats my information for me. So it puts the warning on the second line and If on the last line and beautiful color-coding, as we expected.

Validates and saves your PeopleCode, formats it correctly. Notice the following features of the PeopleCode Editor. If the editor encounters a caret, it replaces the caret with the current field name. If the editor encounters a field name, it checks to see whether that field belongs to the current record definition. And if it does, then the editor adds the record name before the field name.

So again, we can see that happened here, put in with the caret and said you're on STUDENT_NAME from student tables, so put PSU_STUDENT_TBL as student name. We said, equals student_id. Says, hey, that's inside this record, so it put it in there for us. If the field name does not exist in the current record, then the editor displays an error message and does not complete Validation or save the program.

Editor matches the defined case for PeopleCode built-in functions, constructs, classes, methods, and properties. The editor also places definition names, records, fields, and so on all in uppercase and matches the case of each variable to its first occurrence.

To improve readability, the editor reformats the code into blocks by indenting the statements within each block. The editor ignores text that are in quoted literals. So you can pretty well type whatever you want in there. And the editor checks for undeclared variables and displays an auto-declare message in the Validate pane. So if we have a variable and we haven't defined the type, it will tell us it's going to be defined as type Any.

Important-- while not required, declaring all variables is strongly recommended for type-checking and other considerations. In particular, declaring object type variables is critical, since PeopleCode syntax validation will catch data type mismatches and other mistakes in property or method usage for most declared object types.

Cut, copy, paste, and undo functionality is available, as in other text editors. So if we come over here and just take a look while I'm inside here. You notice up here at the top, you have your options-- Edit, Undo, Redo, Cut, Copy, Paste, Delete, Select All.

PeopleCode definitions is not saved with the record definition. It is stored in other PeopleTools tables. Position your cursor on the word "Warning" and press F1. The PeopleCode language reference is opened in the browser on this subtopic for the Warning function. It could get a note to us, or it could be in new version to go to since the class was created. If so, choose the newer version.

It says, note PeopleCode F1 Help is case-sensitive. Pressing F1 for Warning opens the PeopleCode online Help to a valid topic file. Pressing F1 for Warning would result in 404 Not Found error. Using F1, you can view the online documentation for PeopleCode built-in function system variables, meta-HTML and meta-SQL, and the PeopleCode language reference, and for building classes and certain delivered application classes in the PeopleCode API reference.

F1 Help for relevant features and dialog boxes, such as the PeopleCode Editor can be found in the PeopleCode Developer's Guide. So if we come over here and go to our Warning and hit our F1 on it, here I get prompted saying, what browser do you want to use to open up the online Help. I'll just say, open up Google Chrome. And it looks out there, and it says, hey, we found It.

It says, but there's a newer version of the guide since this class was created. Right now, we're on Version 2, but apparently, there's been an update since this class was created. So I can say, go to the latest version now. And now I'm on Version 3. But of course, the negative thing with that is, I'm no longer on the context-sensitive Help. The shame of it all. So the good and the bad.

Now we could go and change it to go to the latest and greatest information, but I'd have to go in there and bounce my web server. I have to bring it down and bring it up. But if I wanted to do that, I could come over here to my Nav bar, go to my Navigator, go to my PeopleTools, choose to go into my web profile if I have authority. I don't know what we have access to here, but we'll find out, web profile configuration.

Search-- and I'm pretty sure in class, we're using the Prod web profile. And from here is where you tell it your Help URL. So here you see where it's saying, go to Release 2. I would probably change that to Release 3 now, since that is out. And I'd hit Save, and this would update for the PIA. But we also would need to update it for App Designer Data Mover, which would be in your PeopleTools options.

I come over here to my Navigator, and if I go back to PeopleTools, and if I go into my PeopleTools Utilities, and go into Administration, and PeopleTools options, inside here you'll see the option of where we set up our Help location for our development tools. And here you see it listed, and now it changes from Release 2 to be Release 3.

As I said, if I wanted this to go into effect for my PIA, I would need to bring down my PIA domain and bring it back up. I'm not going to do so right now. I might do it before the day is over. But for now, I'll just keep it. But if I come over here and click on F1 here, on the Warning, here again, I haven't brought anything down and up, so I'm still looking at the older version.

I'm going to come in here and just close this instead of going to the new release. And here you can see how to use Warning. So it brings up the context-sensitive information. Let's just see what would happen if I changed this to a 3. Probably won't work at all, but hey, I think it's worth a shot. What do you think?

Nope, didn't work, but it was worth a shot. But that's how you change it. And then I'd need to bounce my web server, sign out, sign back in, before it would be going back into effect.

Position your cursor on the word PSU_STUDENT_TBL. Right-Click and select View Definition. You can view any definition or the PeopleCode associated with a definition by Right-Clicking the definition name. In the program. So if we come over here and go back to our App Designer, and if we come in here and go to PSU_STUDENT_TBL and Right-Click on it and say View Definition, it opens up the Record Definition, where I can view the Record field properties that are in here, or the Record's properties.

If a user-defined function is referenced in a program, you can open that program by Right-Clicking in the function name and selecting View Function. If an application class is referenced in a program, you can open that class or package definition by Right-Clicking in the class name and selecting View Application Package or View Application Class. And we will be doing some of that a little later in our lessons.

The PeopleCode Editor supports drag and drop functionality. Try dragging the following items from the Project View into the editor pane, but do not save them. So you can bring in a record definition, field definition, record field, a field name within a record definition, component definition. You can also drag and drop from a definition that is open in a definition workspace and from one PeopleCode program to another.

So just as kind of an example in here, if I may go back to my PeopleCode Editor. And if I come back in here, and if I'm looking at this right here and I want to put in information, I can drag and drop from in here. So I could come in here, and I could say, let's drag the Customer ID from the record. And I could drop it inside here, and I could say, let's make that equal to XYZ, maybe. So that's an example of dragging and dropping the information from the project workspace area into your PeopleCode area.

Review the PeopleCode auto-save file in the TMP directory on your system. The TMP directory is typically not C:Temp. The temporary directory is located in the Windows TMP path. From a command window, type set to see the path. There is a Temp and a TMP, T-M-P path, which may be different. Double-click the Temp shortcut on the desktop to navigate to the TMP directory defined on your system.

So if I come back in here-- and I'm going to close this one before I forget and accidentally save it-- I come over here, and I go to my desktop. And here's our Temp folder. And I double-click on it, it'll take me in to my Temp directory information that we want to look at here.

Says, if a numbered folder, such as a 2 exists, open that folder. Locate the file name, PPCMMDDYY_HHMMSS, in which MMDDYY is today's date, and HHMMSS is the time the file was generated. This is your PeopleCode auto-save file. PeopleCode Editor automatically backs up every keystroke that's between saves.

When you save your PeopleCode, the backup file is deleted. This file does not currently exist in your Temp directory. Type a few characters in the editor and then look again. So if I come over here, and let's open up the-- inside here, I go into my PeopleCode Editor again. And I put something in here.

If come over here to the Temp directory that we was looking at inside here, somewhere inside here, I should find my information. In here, you see PeopleCode, and you see the date inside here. Like here, you see the date, 3/18, and you see my time information that we have inside here. And I double-click to open this maybe with a notepad.

Here you can see the information, and right there in writing, Greg is great. If it says it there, that means it must be true. But this is where it's being backed up to when you're setting up the information.

17. You can modify the font and colors used in a PeopleCode Editor. So if you go back to Application Designer, show that a PeopleCode program in the editor is the active definition. And you could select Edit, Display Fonts and Colors. So we looked at that a couple moments ago. If I come back over here, I can say Edit, Display Fonts and Colors.

And here, if I go in here, you can see that if we're looking at a keyword, you see the default color is blue. But I could change it to be some other color if I chose. Select File, Exit to quit the PeopleSoft Application Designer. You will launch a different PeopleSoft Application Designer session at the beginning of the next activity. This concludes the activity. Please do not continue.