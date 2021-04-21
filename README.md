# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.

Fill the parts marked '_enter' in the **Tasks** section below.

## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Access to the csv file.
3. Telemetric information/data availability in the csv
4. Function to generate the PDf report 

(add more if needed)

### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | Yes           | Use Functions to generate PDF
Counting the breaches       | Yes           | Analyse and count the breaches incase of data availability in csv
Detecting trends            | Yes           | Analyse and detect the trends incase of data availability in csv
Notification utility        | Yes           | Function/Feature part of the software being developed

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
2. Write "Invalid input" to the PDF when the csv doesn't contain expected data
3. Write "No data found" to the PDF when the csv doesn't contain any data
4. Write "Breach Count" to the PDF when the data in csv crosses the defined threshold
5. Write "No Breaches Found" to the PDF when the readings in csv is well maintained within the defined threshold
6. Record the trends to PDF with date & time when the reading is continuously increasing for 30 minutes
7. Write "No Trends detected" to the PDF when the readings doesn't increase rapidly
8. check if the PDf is generated and stored in the serverweekly
9. Set an alert to trigger a notification everytime a new report is available.


(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | PDF File     | Notification triggered      | fake the notification triggers
Report inaccessible server | Server IP
                            /Path         | Connection Failed           | None - it's a required verification
Find minimum and maximum   | csv          | Obtain max and 
                                            min readings                | None - it is a pure function
Detect trend               | csv          | Obtain trends with date 
                                            and time                    | None - it is a pure function
Write to PDF               | csv          | pdf with obtained max,min 
                                            and trends                  | fake the pdf generator call
