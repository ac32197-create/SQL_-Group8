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
The central entity of our data model is the Tournament entity used to store the list of tournaments and their status. The tournament entity is connected to the Seasons entity to show the time at which the tournament is taking place. The Stages entity represent the levels in which the games are being played at in the season. Since there are many games that happen within the Season, the Match entity was created as the associative entity to show the games that are taking place. In order to show the actual teams that are playing within the matches, the teams entity is connected to matches through an associative entity called Teams_In_Matches.

One team has multiple players but the players can only belong to one team at a time which is represented but the one to many relationship. This also applies to the Coaches entity. The teams entity has a many to many relationship with tournaments to show which teams are competing at the exact tournaments.

Tournaments has a one to one relationship with PrizePool because one tournament only has one prize pool. Prize pool is connected with sponsors to allow sponsors to analyze how much money they've contributed to the pool and the results of their investment. Sponsors can sponsor many teams and a team has many sponsors so the many to many realtionship is formed and forming the TeamSponsor entity. To show which sponsor is sponsoring a tournament, another man to many relationship is formed and is shown through thr TournamentSponsor entity.

The last part of the data model is a many to many relationship with tournament to venues to show where locations of the available are loacted. The assocative entity, TournamentVenue, shows the location and time of when the specific tournament will take place at.

<img width="960" height="1190" alt="image" src="https://github.com/user-attachments/assets/b8a31c6e-0656-4aec-9ecd-c07d14cec222" />

## Data Dictionary
|Column|Desc|Data Type|Role|
|------|----|---------|----|
|Tournament|
|tournamentID|unique tournament ID|INT|PK|
|tournamentName|name of tournament|VARCHAR(45)||
|numberOfTeams|# of teams per tournament|INT||
|tournamentStatus|status of tournament|VARCHAR(45)||
|--||||
|Stages|
|stageID|unique stage ID|INT|PK|
|stageName|name of stage level|VARCHAR(45)||
|stageNumber|stage sequential order|INT||
|--||||
|Matches|
|matchID|unique match ID|INT|PK|
|matchGame|current videogame title|VARCHAR(45)||
|seasonID|connects the match to the unique season|INT|FK|
|stageID|connects the match to the unique stage|INT|FK|
|--||||
|Season|
|seasonID|unique season ID|INT|PK|
|name|season term|VARCHAR(45)||
|year|season year|VARCHAR(45)||
|startDate|season start date|DATETIME||
|endDate|season end date|DATETIME||
|tournamentID|connects the season to the unique tournament|INT|FK|
|--||||
|Sponsor|
|sponsorID|unique sponsor ID|INT|PK|
|sponsorAmount|amount of money invested by sponsor|DECIMAL(12,2)||
|sponsorROI|return on investment for the sponsor|DECIMAL(12,2)||
|prizepoolID|unique prize pool ID|INT|FK|
|--||||
|PrizePool|
|prizepoolID|unique prizepool ID|INT|PK|
|tierlevel|reward level granted to winners|VARCHAR(45)||
|amount|amount of money per tie|DECIMAL(12,2)||
|Tournament_tournmentID|connects the prize pool to the unique tournament|INT|FK|
|--||||
|TeamSponsor|
|sponsorID|connects the unique sponsor ID to the unique team ID|INT|PK FK|
|teamID|connects the unique team ID to the unique sponsor ID|INT|PK FK|
|--||||
|TournamentSponsor|
|sponsorID|connects the unique sponsor ID to the unique tournament ID|INT|PK FK|
|tournmentID|connects the unique tournament ID to the unique sponsor ID|INT|PK FK|
|year|year in which this sponsor funded the tournament|INT||
|startDate|start date of when the sponsor began funding the tournament|DATETIME||
|endDate|end date of when the sponsor stopped funding the tournament|DATETIME||
|--||||
|Teams|
|teamID|unique team ID|INT|PK|
|teamName|title of the team|INT||
|wins|total wins of the team|INT||
|losses|total losses of the team|INT||
|totalTournamentsPlayed|total tournaments the team has played in|INT||
|city|hometown of the team|VARCHAR(45)||
|--||||
|Players|
|playerID|unique player ID|INT|PK|
|playerFirstName|first name of player|VARCHAR(45)||
|playerLastName|last name of player|VARCHAR(45)||
|age|age of the player|INT||
|yearsOfExperience|total years of experience of the player|INT||
|teamID|connects the player to their unique team|INT|FK|
|--||||
|Coach|
|coachID|unique coach ID|INT|PK|
|coachName|name of the coach|VARCHAR(45)||
|yearsOfExperience|years of experience for the coach|INT||
|teamID|connects the coach to their unique team|INT|FK|
|--||||
|Teams_In_Match|
|matchID|connects teams to the unique match ID|INT|PK FK|
|teamID|connects the matches to the unique team ID|INT|PK FK|
|score|score of the match between two specific teams|INT||
|outcome|win or loss for each team in the match|VARCHAR(10)||
|--||||
|Teams_in_Tournament|
|tournamentID|connects the unique tournament ID|INT|PK FK|
|teamID|connects the unique team ID|INT|PK FK|
|--||||
|Venues|
|venueID|unique venue ID|INT|PK|
|venueCity|city in which the venue is located|VARCHAR(45)||
|venueState|state in which the venue is located|VARCHAR(45)||
|venueCountry|country in which the venue is located|VARCHAR(45)||
|venueName|title of the venue|VARCHAR(45)||
|venueCapacity|the max capacity of the venue|INT||
|--||||
|TournamentVenue|
|tournamentID|connects the venue to the tournament|INT|PK FK|
|venueID|connects the tournament to the venue|INT|PK FK|
|stateDate|start date of tournament at the venue|DATETIME||
|endDate|end date of the tournament at the venue|DATETIME||



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

Query #4 allows tournament managers to clearly categorize their sponsors by the contributions that they make to each tournament. As a result, they can take this information and be able to roughly guess what they expect from each sponsor in future tournaments, helping them establish a prize pool. Additionally, they can clearly pinpoint which sponsors clearly have ample funds, allowing them to determine which sponsors to approach when in need of more funds. Finally, by establishing a tier system, this motivates the sponsors to want to donate more money in order to increase their sponsorship tier status.

## Database Information
Database Name: ns_Sp26_61608_Group8
