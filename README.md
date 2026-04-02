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
1) Query #1 creates a standings table for all teams particpating in tournaments across multiple years and various tournaments. Using a CASE-WHEN statement, the query tallies the total wins, losses, and draws that a team has had across its tenure. Additionally, the table is ordered so that the teams with the best record are at the top of the standings and those with the worst record are at the bottom.
<img width="782" height="687" alt="image" src="https://github.com/user-attachments/assets/27c31888-4410-42d3-92d7-72d20d840f1f" />

Query #1 allows managers to view which teams have been most successful and least successful across numerous past tournaments and the matches they have participated in. This can help managers decide the original seedings entering the tournament, as the teams with the best aggregate records should be seeded higher than those who have performed poorly. This helps the tournament management set the bracket for the tournament, rewarding those teams who have historically performed well. Additionally, if a team is consistently at the bottom of the standings table, tournament organizers can decide to exclude them from future tournaments, opening spots for newly established teams.


2) Query #2 returns a list of players on a given team who have more years of experience than the average years of experience on their team. It also showcases which team these experienced players are on.
<img width="1002" height="782" alt="image" src="https://github.com/user-attachments/assets/71506858-3c89-42fd-9b16-119f4e7b3a03" />

Query #2 allows tournament organizers to view which players in their tournament have the most experience playing videogames at the professional level. This can help these tournament organizers determine marketing campaigns, as they will often market players that are well known and well established in the video game space. Additionally, combining this with the standings table in Query #1, tournament organizers can determine which players specifically have contributed to long term success of well-performing teams, further reinforcing which players they should label as the "star" of their tournament.


3) Query #3 uses a left join on the Venues and TournamentVenues tables combined with a NOT EXISTS clause to determine which venues have not hosted a tournament and the city they are located in.
<img width="1146" height="330" alt="image" src="https://github.com/user-attachments/assets/ceb12302-8824-4205-b796-f701614b9971" />

Query #3 lets tournament managers to clearly see which venues are suitable to host a tournament event but have not been granted the opportunity to. This then allows managers to dive into why these venues have yet to host an event. Organizers can investigate the city itself, determining the size of the fan base that is present in said cities and the quality of the facilities that are located there. As a result, after this analysis, tournament organizers can plan upcoming events to expand to these cities and venues that have yet to host a tournament in order to tap in to new markets.


4) Query #4 establishes various tiers for sponsorship amounts, namely Platinum, Gold, Silver, and Bronze for contributions to a single tournamnet. The query uses a CASE-WHEN statement to label sponsors by their sponsorship tier, ordering the results by largest donors to smallest donors.
<img width="1102" height="800" alt="image" src="https://github.com/user-attachments/assets/54e18cfe-88ed-4940-9ca6-a0e59ca4494d" />

Query #4 allows tournament managers to clearly categorize their sponsors by the contributions that they make to each tournament. As a result, they can take this information and be able to roughly guess what they expect from each sponsor in future tournamnets, helping them establish a prize pool. Additionally, they can clearly pinpoint which sponsors clearly have ample funds, allowing them to determine which sponsors to approach when in need of more funds. Finally, by establishing a tier system, this motivates the sponsors to want to donate more money in order to increase their sponsorship tier status.

## Database Information
