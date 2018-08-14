# Git Branching Strategy
##### (by Ravi Kalla)

## Necessary Branches
<img src="https://github.com/ravikalla/documents/blob/master/Images/GitBranchingStrategy5.png" width="30%" height="30%">

#### What does the branches contain and who uses them?
 1. Master Branch:
     * Contains most stable source code
     * No one need to certify this code as it was already certified by the team in release branches
     * Created by product owner once in the project lifetime
 2. Release Branch:
     * Contains source code for a release
     * To be tested and certified by Quality Engineers
     * Branched out from Master Branch by Release Manager / Scrum master / Development Lead once for a project release
 3. Dev Branch:
     * Contains source code for a release
     * To be tested and certified by Development Lead
     * Branched out from Release Branch by Development Lead once for a project release
 4. Feature Branch:
     * Contains source code for a user story
     * Code created by developer and certified in Peer Review
     * Branched out from Dev Branch by individual developers for every user story

## Feature Branch Merge
<img src="https://github.com/ravikalla/documents/blob/master/Images/GitBranchingStrategy4.png" width="38%" height="38%">

#### Where is the code change done for a given user story?
   * Code changes for a story are done in Feature branch
   * After unit testing and peer review, Feature branch is merged to Dev Branch
   * Every Feature Branch should be deleted immediately after merge to Dev Branch

## Dev Branch Merge
<img src="https://github.com/ravikalla/documents/blob/master/Images/GitBranchingStrategy3.png" width="70%" height="70%">

#### When is the unit testing done?
   * Unit testing is done in developer machine for the first time.
   * Unit testing is done once again in Continuous Integration[CI] pipeline(Jenkins) that is associated with Dev branch.
   * If unit tests pass in the CI Pipeline, Development Lead should review any critical changes in the code and merge the Dev Branch into Release Branch

#### When is the code deployed to Dev environment?
   * Code is deployed to Dev environment when there are any changes in Dev Branch within a certain timeframe (usually 1 hr)
   * Don’t delete Dev Branch after every merge to Release Branch. Delete it only after release is completed.

## Release Branch Merge
<img src="https://github.com/ravikalla/documents/blob/master/Images/GitBranchingStrategy2.png" width="78%" height="78%">

#### When is the QA testing done?
   * Quality Engineers do testing in QA environment
   * Code to QA Environment comes from Release Branch

#### When is the code deployed to QA Environment?
   * Code is deployed to QA Environment when there are any changes in Release Branch within a certain timeframe (usually 1 day)
   * Once QA Environment is certified by Quality Engineers with the latest code in Release Branch, corresponding build file will be deployed to Production environment and then the Release Branch code is merged to Master Branch
   * Delete Release Branch and corresponding Dev Branch once the code from Release Branch is merged in master.

## Starting a new release
<img src="https://github.com/ravikalla/documents/blob/master/Images/GitBranchingStrategy1.png" width="85%" height="85%">

#### How to branch out for a new release?
   * Create a new branch from Master Branch
   * Don’t use previously used release branches

## Hot Fixes – Not part of a release
<img src="https://github.com/ravikalla/documents/blob/master/Images/GitBranchingStrategy.png" width="95%" height="95%">

#### How to handle Hot Fixes?
   * Create a new branch from Master Branch
   * Do the code changes and test them in Dev and QA environment ASAP
   * Deploy certified build to Production
   * Finally, merge the HotFix Branch to Master Branch and also in Release Branches that exist
