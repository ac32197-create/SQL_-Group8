# SQL_-Group8
## Team Name:
Group 8-  E-Sports Tournament Organizer
## Team Members
1. Jason Bui [@jasonbui](https://github.com/jjayyan)
2. Angel Chen [@angelchen](https://github.com/ac32197-create)
3. Henry Joiner[@hankjoiner](https://github.com/HankJoiner)
4. Faaris Rana [@faarisrana](https://github.com/Faariscodes)
5. Matthew Watson[@matthewwatson](https://github.com/mattwaa)


## Scenario Description
Our database captures the relationships within an eSports organization. The database allows organizations to track all aspects of tournaments. These include ways to track the progress of each team within the tournament. 

Tracking for matches follows the structure of matches, stages, seasons, tournaments. This allows the user to view the outcomes of all levels of the path to the final tournament. 

Next, we have the funding for the teams and tournaments. The tables within the financial funding include sponsors and prize pools. The sponsors are also able to determine their ROI based on the teams they have sponsored. Users are also able to view how much each sponsor contributed to the prize pool of the overall tournament.

Then, teams and people within the team are able to be referenced through the tables of teams, coaches, and  players. These tables allow the user to reference team rosters, coaches associated with each team, and overall team wins and losses. 

Finally, the database tracks the venues for each tournament and when these venues will be used for that specific tournament.


## Data Model
<img width="960" height="1190" alt="image" src="https://github.com/user-attachments/assets/b8a31c6e-0656-4aec-9ecd-c07d14cec222" />

## Data Dictionary


## Queries
1) Query #1 creates a standings table for all teams particpating in tournaments across multiple years and various tournaments. Using a case-when statement, the query tallies the total wins, losses, and draws that a team has had across its tenure. Additionally, the table is ordered so that the teams with the best record are at the top of the standings and those with the worst record are at the bottom.
<img width="782" height="687" alt="image" src="https://github.com/user-attachments/assets/27c31888-4410-42d3-92d7-72d20d840f1f" />

Query #1 allows managers to view which teams have been most successful and least successful across numerous past tournaments and the matches they have participated in. This can help managers decide the original seedings entering the tournament, as the teams with the best aggregate records should be seeded higher than those who have performed poorly. This helps the tournament management set the bracket for the tournament, rewarding those teams who have historically performed well. Additionally, if a team is consistently at the bottom of the standings table, tournament organizers can decide to exclude them from future tournaments, opening spots for newly established teams.
## Database Information
