# Ticket Breakdown
We are a staffing company whose primary purpose is to book Agents at Shifts posted by Facilities on our platform. We're working on a new feature which will generate reports for our client Facilities containing info on how many hours each Agent worked in a given quarter by summing up every Shift they worked. Currently, this is how the process works:

- Data is saved in the database in the Facilities, Agents, and Shifts tables
- A function `getShiftsByFacility` is called with the Facility's id, returning all Shifts worked that quarter, including some metadata about the Agent assigned to each
- A function `generateReport` is then called with the list of Shifts. It converts them into a PDF which can be submitted by the Facility for compliance.

## You've been asked to work on a ticket. It reads:

**Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.**


Based on the information given, break this ticket down into 2-5 individual tickets to perform. Provide as much detail for each ticket as you can, including acceptance criteria, time/effort estimates, and implementation details. Feel free to make informed guesses about any unknown details - you can't guess "wrong".


You will be graded on the level of detail in each ticket, the clarity of the execution plan within and between tickets, and the intelligibility of your language. You don't need to be a native English speaker, but please proof-read your work.

## Your Breakdown Here
- I assume every facility that uses clipboard health will have some sort of dashboard were they can see all their Agents and the shifts they work. In this dashboard they should be able to add and save custom details for each of their Agents, this added Data would then be saved in the database table that contains the list of Agents of that particular facility.

- Knowing the above, to achieve adding a custom id for each Agent, I would make an api call to the Database of the particular facility using a function `getShiftsByFacility` and probably passing the facility `id` as a parameter. This should then return all the Agents working at the facility which would be rendered in the dashboard.

- Then there should be a way to edit or add custom data (which in this case would be a custom id) to a specific Agent field. Upon adding the custom id, i will make an api call to update the Database table using maybe a function `updateShiftsByFacility` and passing in the facility `id` and the `customId` as parameters, which would then update the Agent field working for that particular facility.

- Now that we have a custom id for each Agent working for a specific facility, we can then use the custom id upon generating reports for a specific facility using the `generateReport` function.
Modify function generateReport include the agent facility id in the generated report.

Time Effort: 2 - 4 hours

Acceptance Criteria:

A column custom_id should be present in the pdf showing the facility id of the agent
Implementation Details:

Add a column custom_id to the generated pdf
