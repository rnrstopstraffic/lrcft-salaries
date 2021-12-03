# lrcft-salaries

## Background
The Los Rios College Federation of Teachers has been researching the salary structure for its faculty in the Los Rios Community College District. Part of this research is to compare the structures of our salary schedule to those of the 71 other community college districts in the state of California. Once the structural analysis was completed, we identified districts which were similar to us across several different characteristics (number of students, number of colleges, population density, etc.) and created a new salary schedule which was more in line with those colleges than our current schedule was. 

In order to successfully implement this new schedule, it was necessary to hold a vote among members to ratify the proposal. In order to fully inform members, we wanted to create a tool by which they could individually compare their personal current salary to the proposed salary, as well as to what their salary would be in those comparable districts, based on their education and years of experience. We decided that we would use Tableau to create a dashboard ([found here](https://public.tableau.com/app/profile/brett.sanchez/viz/salarytableau/Salary)), but it would necessitate data that was in a different form than we currently had.

The Python scripts in this project were created to take raw salary schedules in the form found in the [schedules folder](schedules/) and transform them into a single long data set that could be used by Tableau to create the desired visualization.

## Implementation
The transformation process occurrs in two steps:
1. Run the [transpose_schedules](python_scripts/transpose_schedules.ipynb) script which transposes the schedules into a form that is more usable to us in Pandas (note that this script creates a new folder called "transformed_schedules")
2. Run the [salary_prep](python_scripts/salary_prep.ipynb) script to create the desired aggregated output in csv format, along with individual csv files for each distinct district (these are found in a new folder called "prepped_schedules"). 

## Notes
1. While the implementation given is for a small handful of districts that are similar to Los Rios, it can be used to compare any number of districts; simply add the salary schedule into the "schedule" folder before running the scripts.
2. The initial purpose for these scripts was to create a dataset that was Tableau-ready, but transforming the schedules into a long shape allows for other analysis to be done with ease as well. For example, given a count of faculty at each step and class, it is a simple process to determine an approximate annual salary cost to the district for various schedules. 
3. The scripts might seem overly complex for a handful of roughly 6 x 25 rectangular arrays, but the arrays are not particularly standardized. For example, the cutoff between Class I and Class II in one district might be 30 units above a master's degree while the same cutoff in another district might be 36 units above a master's degree. Another complicating factor is longevity increases (which are based on years of service in the district and not on overall years of experience). As such, it became clear that simple transformations using tools such as Excel were not going to suffice.
4. The campaign to ratify the new salary schedule was a success; turnout amongst members was nearly double that in a standard election, with approximately 97% of members voting "yes." With this achievement, we accomplished the first underlying structural change to the salary schedule (as opposed to simple percentage increases) in over 50 years.
