# Election Analysis

## Overview of the Audit

In this project we are helping Tom, a Colorado Board of Election employee audit the tabulated results of the Colorado US Congressional precinct. Tom is expected to present the following 

 * Total votes cast during this election 
 *	Number of participating counties
 *	Names, votes and % votes per county 
 *	Number of candidates with votes 
 *	Names, votes and % votes per candidate 
 *	Winning county - name, total votes and % votes 
 *	Winning candidate - name, total votes and % votes

This task is currently being done using excel but Tom’s boss, Seth wants to know if there is anyway this audit can be automated using Python.  He also feels that if this exercise is successful then this analysis can be scaled to cover election audits in other congressional precincts, senatorial districts and local elections. 

## Resources

*	Data source:  election_results.csv 
*	Software: Python 3.7.6, Visual Studio Code 1.57.1

## Election-Audit Process
To help us answer the questions of the Election Board we used python. We followed the below steps 

*	The data we need to retrieve for our analysis 

        *	Import csv 
        *	File_to_load = os.path.join(“Resources”, “election_results.csv”) 
        *	File_to_save= os.path.join (“analysis”, “election_analysis.txt”)


* Total number of votes cast
   * Initialize vote counter with 
   
          * total_votes = 0
   
   * For each row in the reader add the votes with 
   
          * total_votes=total_votes+1
   
   *	Print the results tot the terminal and election_analysis.txt 

             *	election_results = ( 
               *	f"\nElection Results\n" 
               *	f"-------------------------\n" 
               *	f"Total Votes: {total_votes:,}\n" 
               *	f"-------------------------\n\n" 
               *	f"County Votes:\n") 
             *	print(election_results, end="") 
             *	txt_file.write(election_results)

* Get the complete list of counties 

   * Create a county list and a county votes dictionary with

          * county_option [] 
          * county_vote{}

  * Track the winning county, the vote counts and percentages with 

          *	winning_county = ”” 
          *	winning_count = 0 
          *	winning_percentage = 0

  *	Get the county names from column 1 for each row below the header row with

          * county_name = row[1]

  *	Get the list of county names and votes and using 

          *	if county_name not in county_options: 
              *	county_options.append(county_name)
              *	county_votes[county_name] = 0 
              *	county_votes[county_name] += 1

  *	Get the votes & vote percentatges using   

          *  votes = county_votes[county_name] 
          *  vote_percentage = float(votes) / float(total_votes) * 100 
          *  county_results = ( 
          *  f"{county_name}: {vote_percentage:.1f}% ({votes:,})\n")

  *	Print the county results to the terminal and election_analysis.txt 

          *	Print (county_results) 
          *	txt_file.write (ccounty_results)

  *	Determine the largest county & voter turnout 

          *	if (votes > winning_count) and (vote_percentage > winning_percentage): 
            *	winning_count = votes 
            *	winning_county = county_name 
            *	winning_percentage = vote_percentage

  *	Print the county with largest turnout to terminal and to election_analysis.txt 

            *	largest_turnout_summary = ( 
              *	f"-------------------------\n" 
              *	f"largest_turnout: {winning_county}\n" 
              *	f"-------------------------\n") 
            *	print(largest_turnout_summary) 
            *	txt_file.write(largest_turnout_summary)

*	Get the complete list of candidates who received votes

            * candidate_option [] 
            * candidate_vote{}

  *	Track the winning candidate, the vote counts and percentages with 

            *	winning_candidate = ”” 
            *	winning_count = 0 
            *	winning_percentage = 0

  *	Get the candidate names from column 2 for each row below the header row with 

            *	candidate_name = row[2]

  *	Get the list of candidate names and votes and using 

            *	if candidate_name not in candidate_options: 
                *	candidate_options.append(candidate_name)
                *	candidate_votes[candidate_name] = 0 
                *	candidate_votes[candidate_name] += 1

  * Get the votes & vote percentatges using  

              * votes = candidate_votes[candidate_name]
              * vote_percentage = float(votes) / float(total_votes) * 100
              * candidate_results = ( 
               * f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

  * Print the candidate results to the terminal and election_analysis.txt 

              * print (candidate_results)
              * Txt_file.write (candidate_results)

  * Determine the winning candidate & votes 

              * if (votes > winning_count) and (vote_percentage > winning_percentage): 
                * winning_count = votes 
                * winning_candidate = candidate_name 
                * winning_percentage = vote_percentage

  * Print the winning_candidate_Summary to terminal & election_analysis.txt 
  
                * winning_candidate_summary = ( 
                  * f"-------------------------\n" 
                  * f"Winner: {winning_candidate}\n" 
                  * f"Winning Vote Count: {winning_count:,}\n" 
                  * f"Winning Percentage: {winning_percentage:.1f}%\n" 
                  * f"-------------------------\n") 
                * print(winning_candidate_summary)
                * txt_file.write(winning_candidate_summary)


## Election Results:

From our election analysis we could infer the following 

*	A total of **369711** votes were cast 

*	**Denver** had the largest turnout with **306055** votes and a vote share of **82.8%** 

*	**Diana De Gette** was the winning candidate with **272892** votes and a vote share of **73.8%**
*	
![PyPolls_Challenge_terminal](https://user-images.githubusercontent.com/85518330/124598484-49052a00-de2a-11eb-91d5-b852af80c02d.png)

<img width="542" alt="Election_analysis_txt" src="https://user-images.githubusercontent.com/85518330/124598519-55898280-de2a-11eb-9503-b4ebccd8df47.png">


## Election-Audit Summary: 

We believe we have built a pretty scalable election analysis code for Tom and Seth. 

* Elections in the United States could be of a few kinds 

    * Primary 
    * Local 
    * General 
    * Special Elections – To fill a vacancy 
    
*	They could very well use this code for all individual state congressional precincts 
*	They will need to modify the code when it is used for the general elections as the electoral vote counting method used is different from the one used here.
 
