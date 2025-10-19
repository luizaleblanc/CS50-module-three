<div>
        <h1>CS50 Problem Set 3: Algorithms</h1>
        <p>This repository contains the solutions for Problem Set 3 of Harvard's CS50 course. This module focuses on the fundamentals of algorithms, exploring their design, implementation, and efficiency. The projects cover sorting algorithms and various voting systems, all implemented in the C programming language.</p>
        <hr>

  <h2>1. Sorting Algorithms</h2>
        <p>This part of the problem set involved implementing fundamental sorting algorithms to understand how data can be efficiently organized. The goal was to grasp the logic behind each algorithm and appreciate their differences in performance (Big O notation).</p>
        <h3>Key Implementations:</h3>
        <ul>
            <li><strong>Bubble Sort:</strong> An introductory algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. While simple to understand, it is inefficient for large datasets.</li>
            <li><strong>Selection Sort:</strong> This algorithm divides the input list into a sorted and an unsorted sublist. It repeatedly finds the minimum element from the unsorted sublist and moves it to the end of the sorted sublist.</li>
            <li><strong>Merge Sort:</strong> A highly efficient, recursive "divide and conquer" algorithm. It divides the unsorted list into n sublists, each containing one element, and then repeatedly merges sublists to produce new sorted sublists until there is only one sublist remaining.</li>
        </ul>

   <h2>2. Plurality Voting System</h2>
        <p>The <code>plurality</code> project is an implementation of the most straightforward voting method: "first-past-the-post." In this system, every voter gets one vote, and the candidate with the most votes wins the election.</p>
        <h3>Implementation Details:</h3>
        <ul>
            <li>The program accepts candidate names as command-line arguments.</li>
            <li>It prompts for the number of voters and then records each vote.</li>
            <li>A custom <code>struct</code> is used to store candidate data (name and vote count).</li>
            <li>The program iterates through all votes, tallies them, finds the maximum vote count, and declares the winner(s). It correctly handles ties by printing all candidates who share the highest vote count.</li>
        </ul>

  <h2>3. Runoff (Instant-Runoff Voting)</h2>
        <p><code>Runoff</code> implements a ranked-choice voting system designed to elect a candidate with a majority of the votes (>50%). If no candidate initially has a majority, rounds of elimination occur until a winner is found.</p>
        <h3>Core Logic:</h3>
        <p>The election proceeds in rounds. In each round:</p>
        <ol>
            <li>The votes are tabulated based on each voter's current top preference among the remaining candidates.</li>
            <li>If a candidate has more than 50% of the votes, they are declared the winner.</li>
            <li>If not, the candidate(s) with the fewest votes are eliminated from the election.</li>
            <li>The votes previously cast for an eliminated candidate are transferred to that voter's next-ranked preference. This process repeats until a majority winner emerges.</li>
        </ol>
        <p>The implementation required completing several functions, including <code>tabulate</code>, <code>find_min</code>, <code>is_tie</code>, and <code>eliminate</code>, to manage the state of the election across multiple rounds.</p>

  <h2>4. Tideman (Ranked Pairs)</h2>
        <p>The <code>tideman</code> project is the most complex of the set. It implements a sophisticated ranked-choice voting method that selects the Condorcet winner—the candidate who would win a one-on-one race against every other candidate.</p>
        <h3>The Three-Phase Algorithm:</h3>
        <p>The Tideman method is implemented in three distinct stages:</p>
        <ol>
            <li><strong>Tally:</strong> The program analyzes voter preferences to determine the winner of every possible head-to-head matchup. A <code>preferences[i][j]</code> matrix stores how many voters prefer candidate <code>i</code> over candidate <code>j</code>.</li>
            <li><strong>Sort:</strong> The pairs of candidates from the tally phase are sorted in descending order based on the margin of victory (the strength of the win).</li>
            <li><strong>Lock:</strong> The program iterates through the sorted pairs and "locks in" edges on a directed graph, representing one candidate's victory over another. A crucial constraint is that an edge is only added if it does not create a cycle in the graph. This step prevents paradoxical outcomes (e.g., A > B, B > C, C > A).</li>
        </ol>
        <p>Finally, the winner is determined by finding the "source" of the graph—the single candidate who has no edges pointing towards them, meaning no other candidate defeated them in a locked-in pair.</p>
    </div>

</body>
</html>
