# Temp File for Assignment 2

## Part 1 - Three Decisions before use case

Which use case is it? "Nudge the non-submitters" could be one use case or three. The instructor seeing a list, the instructor sending a nudge, and the scheduler skipping the finished are not obviously the same actor doing the same thing at the same time. Larman's three tests from week 4 apply. Pick a scope and defend it in one sentence. If you decide it is more than one use case, write the one the instructor triggers, and name the others in your pull request.

### Use Case 1: Weekly Activity Report

#### Which use case is it

The use case I am deciding to implement is the instructor sends a nudge to the students that have not completed the WAR on the course section's due day

#### Larman's Three Tests

1. Boss
   - The instructor spent the morning emailing students that have not completed the weekly activity report for the day.
   - This is a reasonable thing for an instructor to say to their boss.
2. EBP
   - The instructor is the one person that is sending out the nudge
   - The place is inside of project pulse
   - The business event that triggers this is the weekly activity report is due on the course section's due date
   - The value that it adds is that nudging a student allows for the submission rate for WAR to increase
   - The data that is in a consistent state is to track which students that have not submitted the weekly activity report have already been nudged by the instructor
3. Size
   - The instructor opens up project pulse 2 hours before the course section's due date for WAR
   - The instructor looks at the list of students that have not submitted their WAR
   - The instructor sends out a nudge through project pulse to remind the students that the weekly activity report is due today from the list.
   - The system marks each student the instructor has sent a nudge out to

### Use Case 2: Peer Evaluation

#### Which use case is it

The use case I am deciding to implement is the instructor sends a nudge to the students that have not completed the Peer Evaluation on the course section's due day

#### Larman's Three Tests

1. Boss
   - The instructor spent the morning emailing students that have not completed the peer evaluation for the day.
   - This is a reasonable thing for an instructor to say to their boss.
2. EBP
   - The instructor is the one person that is sending out the nudge
   - The place is inside of project pulse
   - The business event that triggers this is the peer evaluation is due on the course section's due date
   - The value that it adds is that nudging a student allows for the submission rate for Peer Evaluation to increase
   - The data that is in a consistent state is to track which students that have not submitted the peer evaluation have already been nudged by the instructor
3. Size
   - The instructor opens up project pulse 2 hours before the course section's due date for the peer evaluation
   - The instructor looks at the list of students that have not submitted their peer evaluation
   - The instructor sends out a nudge through project pulse to remind the students that the peer evaluation is due today from the list.
   - The system marks each student the instructor has sent a nudge out to

### Scope and Defense

The use case I am implementing is the weekly activity report. The weekly activity report and peer evaluation are two separate use cases since they target two different events. The students that have not submitted the weekly activity report are different than the people that have not submitted the peer evaluation by the course section's due date. Additionally, these events have different governing rules. For example, the WAR is not gated by active weeks (a student may record activities in any week, but is only expected to in an active week, per the glossary's Active Week), while the peer evaluation covers the previous week and has a one-week window.

The weekly activity report use case also includes the list use case since the instructor has to look over a list of the students that have not completed the WAR which has become a step inside this use case.

Furthermore, I am not including changing the scheduler to implement this logic as this is not defined as a use case. This would be a non-use case functional requirement since there is no primary actor, the scheduler is a part of the system not an actor defined.

Which area does it live in? Every use case ID is UC-<AREA>-<slug>, and the area is baked in permanently. Read the areas already in use: WAR, EVA, SEC, STU, TEA, INS, CFG, and a dozen more. None of them is obviously right for a notification, and there is no UC-NOT area, though the specification does carry FR-NOT-weekly-reminder. Choose, and say why in the pull request. There is no answer key here; there is a defensible choice and an undefensible one.

# What area does it live in?

The weekly activity report will live under the area of WAR. This is because the weekly activity report and the peer evaluation are two separate artifacts that have different rules governing them. The reason why it is not under a new notifications area is because the list of people that will have to receive the nudge notification are coming strictly from the WAR. So the WAR decides who counts as a non-submitter.

Additionally, the peer evaluation use case would be under the area EVA for similar reasoning.

What does "has not submitted" mean? This is the decision the whole feature turns on, and the one an agent will get wrong quietly. A weekly activity report and a peer evaluation are different artifacts on different deadlines. Decide, precisely, and write it down.

# What does "has not submitted" mean?

"Has not submitted" for WAR can be described in the following way:

1. The student is enrolled in the course section, assigned to a team in that section, and is not deactivated
2. When the instructor opens the list before the WAR due date and due time, the student has no saved activity records associated with the active reporting week, the previous calendar week
3. Any saved activity counts regardless of the status
