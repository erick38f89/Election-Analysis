# Election-Analysis
Week 3 PyPoll Analysis

#Overview of Election Audit
  The election audit is a descriptive analysis of the quantitative distribution of Colorado congressional district that is made up three counties: Arapahoe, Denver and Jefferson. We get to sort the total of votes by the total votes and the county distribution as well as identifying the county with the largest voter turnout.
  There is also the classic analysis of declaring the winner by counting the votes each received, the percentage of votes and identifying the cadnidate with the higherst vote count and percentage.
  
#Election-Audit Results

-How many votes were cast in this congressional election?
  There were a total 369,711 votes in the three disctricts of this congressional election.
  
-Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
  The distribution of votes per county was the following: Arapahoe: 6.7% (24,801 votes); Denver 82.8% (306,055 votes) and Jefferson 10.5% (38,855 votes).
  
-Which county had the largest number of votes?
  Denver had the largest number of votes with 306,055 for a 82.8%.
  
-Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
  This is how the votes were distributed among the candidates: Charles Casper Stockham: 23.0% (85,213); Diana DeGette: 73.8% (272,892) and Raymon Anthony Doane: 3.1% (11,606).

-Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
The election winner was Diana DeGette, getting a total 272,893 votes, resulting in a 73.8%.

#Election-Audit Summary

  This analysis was used with code written in the Python language by accessing the data with a csv file and writting it into a txt file. We were able to perform this analysis by declaring variables for the total votes, the candidates options and corresponding votes as well as the county options and corresponding votes. As well as variables to determine the winning candidates, votes total and percentages as it follows:
  
# Add a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Initialize a total vote counter.
total_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

# 1: Create a county list and county votes dictionary.
county_names = []
county_votes = {}   

# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

  This code can be used given any dataset with a similar format to determine this facts for election counts.

  The actual count is done via for loops that iterate each row, reading the votes listed for each particular candidate and increasing the count by one for each appearance.
  
      # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        county_name = row[1]

        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1
  
  A similar excercise was ran to determine the county vote distribution.
    # 6a: Write a for loop to get the county from the county dictionary.
    for county in county_votes:
    
        # 6b: Retrieve the county vote count.
        county_vote = county_votes[county]
        # 6c: Calculate the percentage of votes for the county.
        county_percent = int(county_vote)/int(total_votes) * 100

         # 6d: Print the county results to the terminal.
        county_results = (
            f"{county}: {county_percent:.1f}% ({county_vote:,})\n")
        print(county_results, end="")
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
        
  Just by modifying the source csv file. This can be applied to any votes lists to determine the local distribution, candidates votes and winner. We can use this for low to high turnout elections, such as a school student board for a lower vote example and up to a medium city major and commissions election.
