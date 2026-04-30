# dsu

Post-BOJ plans on linking other OJs to solved.ac

Draft Apr 30, 2026

## TLDR

- We will support other OJs.
- Current top priority is to link other OJs to find same problems in BOJ, and make the problems solvable if you know the BOJ problem ID.
  - This is an effort to recover 'broken links' of the BOJ -- many online resources (especially in Korean) rely on the BOJ problem IDs.
- In the long term, we plan to link as many OJs as possible and provide the library and features just like we did with the BOJ.

## Plans on Linking

We will have our own...
- **ID/password account system.** Basic things are already done by Apr 26th.
  - We plan to allow logging in by other OJs' accounts in the future.
- **Problem numbering system.**
  - We will basically use the same number scheme as the BOJ, which starts from #1000.
  - For problems #1000..#35515, most of the problem numbers will match the BOJ's numbers, excluding problems such as duplicate problems - it is a N:M mapping.
  - For other OJs, if the problem is identical of that in the BOJ, we 'link' the existing ID to the foreign OJ's ID. Otherwise we assign them starting from #35516.
  - For instance, the problem *Scenery* will be `solved.ac #14640` = `BOJ #14640` = `Kattis scenery` = `QOJ #2774` = ...

### Step I: Syncing the Problems

First, we would like to sync the problems fron other OJs. To do this we will contact and/or accept contacts from other OJs.

- Foreign OJs do not have to do anything in this step. If they have an API, we will use them, and if they have not, we will write a crawler to run a recurring job.
- The contributors from the BOJ will assign solved.ac problem IDs.
  - This means that the problems in the foreign OJs will get the difficulty levels assigned to their problems (which had an identical version in the BOJ, for now)
  - The users of the foreign OJs can get used to the level scheme, and many of the lost problems of the BOJ will be recovered in this step.
  - solved.ac would help accelerating this process by matching the source of the problems, or mass-comparing descriptions with LLM, etc.
 
### Step II: Syncing the Users

Then we sync the users.
A solved.ac user can link multiple foreign OJs' accounts. You can think of the way that [CLIST](https://clist.by/) does, but with more trust.

- Foreign OJs should allow us to verify whether the user owns her account or not, by but not limited to the following means:
  - Allowing us as a 3rd party to use the judge's OAuth authentication flow (recommended)
  - Allowing us to read an arbitrary user's submission history. We will prompt the user to make a submission to some random problem. [An example way of doing this](https://github.com/iiitl/Cp_Discord_Bot/blob/critical/commands/cfverify.js)
  - Allowing us to read a user's profile, and allowing the user to write an arbitrary string to their profile, etc.

This enables the users from the other OJs to be able to [contribute to the level database](https://help.solved.ac/en/problem/level).

- For the user to be able to contribute to a problem, the user needs to solve it beforehand.
  - The user's problem solve states will be merged across the judges. It means that if `solved.ac #14640` = `BOJ #14640` = `Kattis scenery` = `QOJ #2774`, and if the user had solved a problem from any source, the user can contribute to the problem `solved.ac #14640`.
  - This will negin to mix the contributors across multiple judges.

From this stage, the users will also be [rated by the solved.ac rating scheme](https://help.solved.ac/en/stats/ac-rating).

### Step III: Strong Integration

These were the integrated before with the BOJ and will definitely make the user experience far more pleasant if supported by foreign OJs:

- The OJs would send the users' submission results in real time;
- The OJs would send informations about new problems, modified problems, rejudges, new users, and deleted users, in real time;
- The OJs would support displaying the problem levels and tags from solved.ac;
- solved.ac and the OJ would work together to support logging in to solved.ac with other OJ's accounts (OAuth, which can also be done in step II)

### Step IV: Stronger Integration?

It will be more than awesome tom maybe even support making submissions from solved.ac but with the user's own account in the respective judges. But I am expecting this would happen in the time very far from now.

## Requirements

The judges' behavior should be similar to that of the judging environment of the ICPC.

## The Protocol

For step III to be done, solved.ac needs to prepare a protocol or maybe a API scheme. I expect this to be done in mid-to-late 2026.

## Moderations, I18n, etc

I'll try to think of the other specific topics. In the meantime please feel free to leave a suggestion in the [issues](https://github.com/solved-ac/dsu/issues).
