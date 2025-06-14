Activity 3-- Debugging PeopleCode Programs. In this activity, you will review the activity overview and investigate the features of the PeopleCode debugger.

Activity Overview. In this activity, you will open the PeopleCode program in the RowInsert event for the ORDER_LINE_NBR field in the PSU_PO_DTL record. You will set a breakpoint in the program and run the application until it hits the breakpoint. Then you will explore the types of information and options that are available to you through the PeopleCode debugger.

Activity Detailed Steps. In this activity, you will launch PeopleSoft Application Designer in three-tier mode. So we come back over here to our desktop and open up our Application Designer. We'll change the connection type from Oracle to be Application Server. And we'll use the T1B85701 Application Server Name. And we'll sign in as the user ID and password of PTCODE.

We'll open a PeopleCode program, start the PeopleCode debugger. We'll set visible breakpoints, view the values by hovering. We'll view values in the panes. We'll create a debug log. We'll debug a second program. We'll change a value in the Local Variables pane, view the Call Stack pain, and exit the PeopleCode debugger.

So to launch the PeopleSoft Application Designer in three-tier mode, from the PeopleTools folder on the desktop, select the Application Designer icon. Change the connection type to Application Server. Share the database name as T1B85701. For the user ID, enter PTCODE. For the password, enter PTCODE. And that's what we just did.

To open up PeopleCode program to debug, maximize your PeopleSoft Application Designer window. And in PeopleSoft Application Designer, open the PSU_PO_DTL record. So we'll do a File, Open, and we'll say, Record, and we'll say, PSU_PO_DTL. Right-Click the ORDER_LINE_NBR field and select View PeopleCode. And select the events in the upper-right corner of the editor and select RowInsert.

So we go to the ORDER_LINE_NBR field, Right-Click and view PeopleCode. Change the event to be RowInsert. Verify that you have the correct event, RowInsert, not RowDelete. Close the output window, Alt-1, to make more room for the debugger pane. So we hit Alt-1, and that closes the output window.

To start the PeopleCode debugger, from the menu, select Debug, enter Debug Mode. The Call Stack pain and the Local Variable pane is open. If the PeopleCode programs had breakpoints set from previous debugging sessions, they are opened as well, and the breakpoints are restored. So if we come over here, click on our Debug menu bar. And we'll say, Enter Debug Mode.

And here, again, you can see the Call Stack is already opened. You see we have the Local Variables being open as well. We have no current breakpoints already selected. Select Debug, View Component Buffers. The Component Buffer pane opens.

For better viewing of data in the debugger panes, you may drag and drop the Local Variables pane next to the Component Buffers pane. So if I come back over here and go to my Debug, and I can come in here and choose to View Component Buffers. And you can also resize this information. So I can drag this up a little bit further up here like this, something of that type. Maybe the Call Stack, maybe make it a little smaller. So I can move things around, as you've just seen.

The debugger provides visual indicators that signify breakpoints locations. To set breakpoints, place your cursor on line number three of the code, If the LINE is greater than MAXLINE Then. And then from the menu, select Debug Toggle Break at Cursor, or hit F9. A red dot will appear in the gutter beside and to the left of the line of code.

So we go over here to our If line. If I go to my Debug, I'll say, let's go out here and set my breakpoint by pressing the F9. Now you see we get the little red octagon area here saying it's going to stop when we're executing at that point.

To test in the browser, select Purchasing, Maintain Purchase Orders, and select Order 00000029. So if we come back over here to the PIA, I go to my Nav bar, go to my Navigator. And I'll go back to my root level, and I'll go into Purchasing. And we'll go into our Maintain Purchase Orders. And I'll do a Search, and I'll select order number 00000029, which is the first order.

Position your cursor on the second line and insert a single row. Press the plus sign insert. In the dialog box, verify that the value is 1 and press OK. The program breakpoint is reached, and the PeopleSoft Application Designer either flashes in the taskbar or gains focus automatically. So we come back over here and hit the plus sign on the second line. And we'll just keep it as a 1 here, and we'll hit OK.

And you'll see down here at the bottom, the App Designer flashing. If we come over here and click on it, here you can see the yellow arrow on my breakpoint, letting me know that's where we're currently located in our code. So it ran into that point and then it stopped. Notice in the gutter that the red dot has been overlaid by a green arrow that marks the current PeopleCode statement.

You can position the cursor and hover over a variable in the PeopleCode Editor to see its value. Hover over the &I until you see a box containing the value of the variable. You can also hover over field names to see the current value of the field. So if we're over here, and I hover over the &I, you can see it's currently equal to 1. If I come in here and I hover over one of these fields, I can see my ORDER_LINE_NBR is currently equal to 0.

By default, the Local Variables pane appears with the debugger, shows the values of local variables, and the properties of objects. You can expand objects here to view more details about them. So here's your local variables. And here you see the MAXLINE, 0, &I is equal to 1. And &LINE is equal to 1.

You can also open panes for global variables, component variables, and function parameters. To view values in the panes, press F8 to go to the next line of the code. The arrow that shows the current line of execution will move to the next line. So if I hit my F8, step into. So here you can see, I've moved in my next line of code. My MAXLINE is equal to LINE.

Continue to step through the code and notice how the variables change as you loop through the rows in the buffer. Look at the Component Buffers pane. The pane gives you the view of all the data in the Component Buffer. You can go out and expand the plus sign for the following items. Do you see the field values for the PSU_PO_DTL, level 0 rowset, GetRecord, PSU_PO_HDR, the GetField.

It says, warning, do not drill on any ParentRowsets or ParentRow items. You can end up in an endless loop if you did that. But it we come back over here and take a look at this, here you see I'm on my next line of code. So here you see MAXLINE is 0. LINE is 1. And if I hit F8 to execute this line, now you can look and see MAXLINE is 1, and LINE is 1. So you can see it executed the code.

If I hit my F8 again, I can see my n4. Then it goes back up. It says, wait, 4I I is equal to 1 to ActiveRowCount. And now if I look in here, you can see my line, &I is equal to 2. And we can take a look at it and say, if the line 2 is equal to the Fetch value of PSU_PO_DTL, ORDER_LINE_NBR, and &I, hit my F8 again. Now I can see that my ampersand line is also equal to a 2.

And if LINE is greater than MAXLINE, then MAXLINE is equal to line. If I hit F8 again, we can see it execute the code. And now I can see MAXLINE is also equal to 2.

If I go to my Component Buffers pane, if I go up here, and here's the Component Buffer, you see the level 0 rowset. If I expand the level 0 rowset, here you'll see the methods properties, I should say, that are available for a rowset. And we'll talk more about these later, RowCount, ActiveRowCount, DeleteEnabled, InsertEnabled. So we can look at this information inside here.

If I look further down, you'll see that a rowset is-- if I look inside here, you can see GetRow. So rowsets are made up of rows, and if I expand my GetRow, at level 0, you'll always have only one row of data. So here you see, I got a row. If I expand a row, rows are made up of either rowsets or records. And if I expand it, here it says, for this row, here you can see the methods and properties that you would see available to this, RecordCount, ChildCount, RowNumber, Visible. So you can see these properties.

And we said that a row is made up of either records or rowsets. If I look at the record at this row at level 0, I can see that the records that are being referenced in my level 0 information is the PSU_PO_HDR. This is the primary record. Then you see additional records at level 0, PSU_TRANSPORT_TBL, VENDOR_TBL, and DERIVED_ED_SVCS.

If I expand my PSU_PO_HDR, here again, you see is deleted, is changed, so I can see these properties that are available at the record level. If I come on down here, you see records are made up of fields. And if I expand the GetFields, here you'll see the fields that we have at level 0. So here you see Business Unit, and you can see the data, the value, that is equal for this field right now. So you see Business Unit ASP01, Order Number 29. And if I expand the field, guess what, I'm going to see the properties that are available at the field level.

Creating a Debug Log. It says, you can send a debug log to the PeopleCode log tab of the output window. To do so, you select Debug, Options, Log Options. Select the Each statement checkbox in the Execution Trace group box. Note the other options that are available. You can also save your debug log. Be aware that logging will slow system performance.

Click the OK. Press the ALT-1 to view the debug log. So if I come back in here and go up here to my debug menu bar., and if we go over here to the Options, and I can say, take me into my Log Options. And I'll select Execution Trace for each statement checkbox in the group box here. And I'll click OK. Now if I hit my ALT-1, and look in my output window, here's your PeopleCode log. So that brings up the PeopleCode log information.

And again, I can still come in here and resize this maybe a little. I can hit F8 to keep going through my logging information here. So notice in the PeopleCode log, the N4 is executed, goes back to my For statement. And again, I can go through this and see it writing to the log.

Debugging a Second Program. To debug another program, in the menu, select Debug, Edit Breakpoints, and click Remove All button, and click OK. Come over here on my menu bar. If I come in here to my Debug, and I say Edit my Breakpoints and Remove All the breakpoints that we have. Hit my OK.

Select Debug, Abort Running Program. Close the PeopleCode Editor window, and the PSU_PO_DTL record definition to reduce the clutter in the definition workspace. So I go to Debug, Abort Running this program. And now that I've aborted it, I'm going to come in here and Close my windows that we have in here. So I'll close all the PeopleCode Editor windows.

I'm also going to Close my PSU_PO_DTL information. And I'll come over here to the PIA as well. Notice over here, program's been terminated from the PeopleCode debugger. I'll hit OK. And I'll just click on Home here.

And then the next step is to open the PSU_STUDENT_TBL record definition. I've opened up the student table's record definition. Right-Click the STUDENT_ID, and select to View the PeopleCode. Click the events in the upper right-hand corner of the editor, and go into, SavePreChange. So we go over here to our STUDENT_ID. And if I Right-Click and say PeopleCode, and if we go in here and make sure we have our SavePreChange for that opened up inside here.

Right-Click any occurrence of the assign_student_id function and select View Function assign_student_id. So if I come in here, Right-Click on it, view the function. And now I'm on the code for the function. Place your cursor on line 7 of the code, STUDENT_ID is equal to LAST_STUDENT plus 1.

From the menu, select Debug, Toggle Break at Cursor, or press F9. So I'll set my focus on here and hit my F9. That sets up my breakpoint. And to test, in the browser, select Students, Personal Information. Note, you will receive a save warning message for the changes you made at the Purchase Order page. Click Cancel to continue without saving.

Add a new value. Enter in your Name, Last Name, First Name, and select a Customer ID, and hit the Save button. So if we come back over here, go to my Nav bar. And if I go to my Navigator, and if I go back to my root level, and we go to Students, and I go into my Personal information. So we'll add a new value, put in Last, First, and Customer, and hit Save.

So if I come in here, click on my Add a new value. And I'll just keep it as New. I'll click Add. Put in the Last Name. We'll say Swenson, and I'll say, Jennifer. And I'll say, Customer. I'll say it is XYZ, and I'll click the Save button.

And when I click the Save button, we should notice that down here in App Designer, it's opened up again. It's flashing at me, saying, come here, come here. And we can see it stopped at our breakpoint. Notice you've got the arrow again pointing at our line of code.

The program breakpoint is reached, and the PeopleCode Application Designer window flashes in the taskbar or gains focus automatically. Because PeopleCode execution has been stopped, Saving will continue to display in the browser window until you step through the execution of the entire program. Notice the green arrow that marks the current PeopleCode statement. I'm color blind, so I didn't know if it was green or yellow, but it's an arrow.

To change a value in the Local Variables pane, you can hover over the LAST_STUDENT ID variable in the PeopleCode Editor to view its current value. For example, the value might be 3001. And the Local Variables pane replaced the current value for LAST_STUDENT ID with a new higher value, for example, replaced the 3001, with 4001.

It says, important, while the original value is surrounded by quotation marks, remove the old value and the quotation marks and replace them with just the numeric value. So we come back over here. And if I'm looking at this one right here, you see the LAST_STUDENT that we have right here. If I want to come in here and make a change to this one right here, I'm going to go back to my debug. And I'll say, let's turn on those Local Variables.

And here's my 3001. I'm going to come in here and change this one to be 4001. And I press Enter to accept a new value. If I want to verify that, if a hover over my LAST_STUDENT, now I can see that it is 4001. Hover over the LAST_STUDENT variable in the PeopleCode Editor. See its value. Well, that's what I just did.

I'm down here talking about viewing the Call Stack pane. Press F8 to execute the next PeopleCode statement, and then observe the Call Stack pane. Continue to press F8 three more times to complete the execution of the program. Notice when the function completes execution, it is popped off the stack.

So if I come back over here, and I need to go back up here to my debug. And if I say, show me the Call Stack window-- so here you can see the function that I'm currently on, the function being executed, [INAUDIBLE] PSU_STUDENT_ID field formula. Student ID, statement number 7, you see PSU_STUDENT_ID, SavePreChange statement.

And if I hit F8 to walk through the lines of my information here, you can see where we are in the Call Stack, see the arrow. And now you can see it popped off when I hit my F8 the last time.

Return to the browser window to examine the ID for the newly entered student ID. The ID will be one greater than the value you entered, so for example, 4,002. So I've got one more F8 to hit. And now you can see my 4002, my new student ID.

Exiting the PeopleCode Debugger. Before exiting the debugger, you should clear your breakpoints. So in the Application Designer, select Debug, Edit Breakpoints. Click the Remove All button and hit OK. So we come up here, Debug, Edit Breakpoints, Remove All, press OK.

Select Debug, Options, Log Options. Deselect the Each statement checkbox and hit OK. And then we'll select Debug, Exit Debug Mode. So if I go back over here to Debug, go back in here to our Options, our Log Options, Remove our Each statement, press our OK. And then we'll go to Debug, and we'll say, let's Exit Debug Mode.

Select File, Exit to quit the PeopleSoft Application Designer. You will launch a different PeopleSoft Application Designer session at the beginning of the next activity. This concludes the activity. Please do not continue. 