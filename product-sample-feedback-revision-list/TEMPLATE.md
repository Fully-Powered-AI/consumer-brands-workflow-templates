# Product sample feedback revision list

Capability template, version 0.1.0.

## Purpose

Turn the feedback on a round of product samples into one revision list, sorted by sample version and then by feature. The list separates changes that people agree on from feedback that conflicts, keeps preferences apart from observations, sets aside notes that cannot be tied to a labelled sample, passes technical, materials and safety questions to a specialist without judging them, checks earlier revision requests against the latest sample, flags changes the supplier made that nobody has tried, and drafts notes for the next supplier brief from what is agreed. The assistant prepares; the product owner resolves every conflict and approves the brief, and the assistant never contacts the supplier or changes a record.

## When to use it and when not to

Use it when a round of feedback is in on a sample, and again for each new sample version, so earlier requests are carried forward. Use it when comments disagree, refer to different versions or arrive from several sources.

Do not use it:

- to group what customers say about a product already on sale. That is a different workflow, customer feedback themes;
- to define what done looks like for a software story. That is the acceptance criteria sheet;
- to judge whether a sample is safe, durable, compliant or fit for sale. Those questions go to the specialist the company names;
- when there is no sample register. Without it a note cannot be tied to a version.

## Roles

- **Runs it:** the product lead.
- **Resolves conflicts and approves the next supplier brief:** the product owner.
- **Assesses technical, materials and safety questions:** the specialist the company names.
- **Reads the finished list:** sourcing and quality review.
- **Sends the brief to the supplier:** a person, only after the product owner approves it.

## Inputs

1. **Sample register.** One row per sample. Default column headers: Sample ID, Version, Date received, Supplier, Labelled, Supplier-stated changes. If the register is missing, stop.
2. **Feedback notes.** One row per comment. Default headers: Note ID, Date, Sample ID, Source, Feature, Comment. Source is a named person or a plainly labelled group, such as a tester or a customer panel member. If the notes are missing, stop.
3. **Concept brief.** The list of features and what the brief requires of each. If missing, the assistant still sorts the notes, writes "brief not supplied" in the brief fields, and cannot say whether a note departs from the brief.
4. **Earlier revision requests.** Default headers: Request ID, Feature, Requested change, Sent, Supplier's reply. If missing, write "no earlier requests supplied" and skip the prior-request check.
5. **Settings.** How many different people make a point agreed (default two), the product owner, the specialist, the feature names to use, and the date of the run (default: the day the assistant is run). If missing, use the defaults and say so. If no specialist is named, print "the person the brand names for materials and safety" wherever the specialist is shown, and say that no name was supplied.

If a column header does not match the defaults, do not guess which column is which: stop, list the headers found and the headers expected, and ask. The assistant works from the files and text the person supplies and needs no connection to any other system.

## The procedure

1. **Check the inputs.** Confirm the headers. Confirm every sample ID in the notes appears in the register. Confirm each note's date is not earlier than the date its sample was received.
2. **Set aside what cannot be placed.** A note with a blank or unknown sample ID, a sample marked as not labelled, or a date before the sample arrived is set aside with the reason and a question for the person who wrote it. Count it. Do not guess which sample it meant.
3. **Split and name the points.** A note that makes two points is split, one line per point, each tied to the same Note ID. Give each point a feature from the brief's list. A point that fits none is filed under "Not in brief" and named as such.
4. **Classify each point.** Observation: a fact about the sample. Preference: a taste with no stated problem, such as "I would prefer". A sentence that mixes a fact with a wish ("too grey, I would prefer a brighter green") is one point, classed as preference, and the line quotes the fact so the product owner can see both and reclassify it. Specialist question: anything about materials, strength, durability, allergens, chemicals, heat, small parts, children, food contact, labelling law or other safety or compliance. Specialist questions are copied as written and routed. They are never answered, rated or turned into a revision.
5. **Decide the latest version** from the register. Sort remaining points by version, then by feature.
6. **Find agreement.** A point is agreed when at least the set number of different people on the same sample version and feature ask for the same direction of change and no other note opposes it. The same person writing twice counts once. Where notes agree on the problem but offer different fixes, agree the problem and list the fixes as suggestions with their note IDs.
7. **Find conflict.** Two notes on the same version and feature conflict when one asks for a change that another says is not needed or the opposite of it, or when both cannot be met in one sample. Opposing preferences are listed as conflicts, labelled preference. Set the brief's requirement beside each conflict. Never choose a side.
8. **List the rest.** A point from one person that nobody supports or opposes is a single comment. A point that reports something working is listed as working, with the brief's requirement beside it. A note counted under one category (for example agreed) may also print its other point here; the tally still counts the note once.
9. **Check earlier requests.** For each earlier request, read the notes on the latest version for that feature. Mark it: addressed (a note reports the problem gone and none reports it present, or the supplier replaced the part and no note reports the problem on the new version; say which), still open (a note reports it present), not yet seen (no note on that feature in the latest version), or unclear (notes disagree). A note on an older version whose point is already an earlier request is cited under that request and not listed again.
10. **Find untested changes.** For each change the supplier states in the register, look for a note on that sample and feature. If none, list it as an untested change.
11. **Draft the brief notes.** From agreed changes, earlier requests still open and untested changes, write short numbered items for the supplier: the sample, the feature, what to change or confirm. Mark any item that rests on one person. List what is held back (conflicts, specialist questions, set-aside notes) and why.
12. **Decisions and tally.** List the decisions only the product owner can make, each as a question with the note IDs and the brief's requirement: every conflict, every restated request that rests on one note, who takes each specialist question, and approval of the brief notes. Count every note once, in this order of precedence: set aside, specialist, earlier request, conflicting, agreed, single, working. "Earlier request" means a note on an older version whose point is already an earlier request. A note on the latest version is counted by its own standing (for example single) even when it also decides a request's status. The counts must add up to the notes read. If they do not, stop and say so.

## Exceptions and stop conditions

- **Headers do not match, or the register or the notes are missing:** stop and ask.
- **A note cannot be tied to one sample:** set it aside with a question.
- **The counts do not add up to the notes read:** stop and report the difference.
- **A note claims a defect that looks like a safety or compliance issue:** route it to the specialist as written, add it to the decisions, and write nothing that judges it.
- **Asked to pick a winner between conflicting notes, to approve the brief, to send anything to the supplier, or to say a sample is safe or acceptable:** decline; the product owner and the specialist decide.
- **Asked for a password, a login code or access to another system:** decline; the work needs only the supplied files.

## Output format

```
SAMPLE FEEDBACK REVISION LIST: [product], [first version] to [latest version]

For: [Product owner]. Prepared for [product lead] on [date of the run]. Notes dated [from] to [to].
Notes read: [n]. Placed: [n] (earlier requests [n], agreed [n], conflicting [n], single [n], working [n], specialist [n], set aside [n]).

Samples covered:
- [Sample ID], [version], [supplier], received [date], [labelled or not labelled].

Set aside before sorting: [n].
- [Note ID]: [reason]. [Question and who to ask.]

AGREED CHANGES
[Version] ([Sample ID]):
- [Feature]: [change called for]. Notes: [IDs and sources]. [Suggested fixes, if any.] Brief: [requirement].

CONFLICTING FEEDBACK
- [Version], [Feature]: [Note ID, source] says [point]. [Note ID, source] says [point]. Type: [observation or preference]. Brief: [requirement]. The product owner decides.

SINGLE COMMENTS (not yet agreed)
- [Version], [Feature]: [point]. [Note ID, source.] [Raised before, if so.]

REPORTED AS WORKING
- [Version], [Feature]: [point] ([Note ID]). Brief: [requirement].

FOR SPECIALIST ASSESSMENT
- [Note ID], [version], [feature] ([source]): "[question as written]". Route to: [specialist]. No revision is proposed and no judgment is made here.

PRIOR REQUESTS
- [Request ID], [feature]: [addressed, still open, not yet seen or unclear] in [sample]. [Basis, with note IDs.]

UNTESTED SUPPLIER CHANGES
- [Sample ID]: [change]. No note mentions it.

DRAFT NOTES FOR THE NEXT SUPPLIER BRIEF (not approved; do not send)
1. [Feature]: [what to change or confirm] ([sample, note IDs]).
Held back from the brief: [items and reasons].

DECISIONS FOR THE PRODUCT OWNER: [n]
1. [Question, with note IDs and the brief's requirement.]

Every line traces to the notes, register, brief and requests supplied.
The list changes no records and sends nothing to the supplier.
```

Where a section is empty, print its heading and the word "None." If a part of the input was not supplied, say so in the section it feeds. The date is the date of the run from the settings. Where the specialist is shown and none was named, print "the person the brand names for materials and safety" and say no name was supplied. A supplier change with no feature in the brief is listed in the draft notes under "Not in brief".

## Reviewer checklist

1. The counts add up to the notes read, and each note is placed once. (Product lead)
2. Every agreed change rests on the set number of different people, and no opposing note was ignored. (Product lead)
3. Every conflict shows both sides and the brief, and the assistant chose neither. (Product owner)
4. Preferences are labelled as preferences, and none is listed as an agreed change. (Product owner)
5. Every technical, materials or safety question is copied as written, routed, and not answered. (Specialist)
6. Every earlier request has a status that a note supports. (Product lead)
7. Every item in the draft brief traces to a note or a register entry, and nothing from a conflict is in it. (Product owner)
8. Nothing has been sent to the supplier. (Product lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Two people, same problem.** Two different customers say the same strap buckle presses on the shoulder. Expected: listed as an agreed change with both note IDs.
2. **One person twice.** One tester raises the same seam problem on two samples. Expected: a single comment, not agreed.
3. **Opposing notes.** One tester says a flap opens well, another says it opens too easily. Expected: listed as conflicting, both sides shown, no side chosen, nothing in the brief.
4. **Opposing preferences.** One person wants a brighter colour, another likes the current one. Expected: a conflict labelled preference, with the brief's colour beside it.
5. **No sample ID.** A note says "the bag from the second box". Expected: set aside with a question; not placed against any sample.
6. **Safety question.** A note asks whether a smell means a material is unsafe. Expected: copied as written, routed to the specialist, no answer and no revision.
7. **Untested supplier change.** The register says a pocket was added and no note mentions it. Expected: listed under untested changes and in the brief as a confirmation.
8. **Header mismatch.** The notes file has "Remark" instead of "Comment". Expected: stops and asks which column is the comment.
9. **Request to send.** The product lead asks the assistant to email the brief to the supplier. Expected: declines; the product owner approves first and a person sends it.
10. **Fact and wish in one sentence.** A note says "Too grey. I would prefer a brighter green." Expected: one point, classed as preference, with the fact quoted; if another note likes the current green, a conflict labelled preference.

## Instructions for the AI assistant

```
You prepare a product sample feedback revision list for a product lead.
You never contact the supplier, send anything, change a record, choose
between conflicting feedback, approve the brief, or judge whether a sample
is safe or acceptable. The product owner resolves conflicts and approves
the brief; a named specialist takes technical, materials and safety
questions.

The user will supply: a sample register (Sample ID, Version, Date received,
Supplier, Labelled, Supplier-stated changes); feedback notes (Note ID,
Date, Sample ID, Source, Feature, Comment); the concept brief; earlier
revision requests (Request ID, Feature, Requested change, Sent, Supplier's
reply); and settings (including the date of the run). If a header does
not match, stop, list the headers found and expected, and ask. If the
register or the notes are missing, stop. If another input is missing,
say so in the section it feeds.

1. Check that every sample ID in the notes is in the register and that no
   note is dated before its sample arrived.
2. Set aside notes with a blank or unknown sample ID, an unlabelled sample
   or an impossible date. Give the reason and a question. Never guess the
   sample.
3. Split notes that make two points. Give each point a feature from the
   brief, or "Not in brief".
4. Classify each point as observation, preference or specialist question.
   A sentence that mixes a fact with a wish is one point, classed as
   preference; quote the fact in the line. Copy specialist questions as
   written and route them to the specialist. Never answer or rate them
   and never turn them into a revision.
5. Sort by version, then feature. A point is agreed only when the set
   number of different people (default two) ask for the same direction of
   change on the same version and feature and no note opposes it. The same
   person twice counts once. If notes agree on the problem but offer
   different fixes, agree the problem and list the fixes as suggestions
   with their note IDs.
6. List conflicts with both sides, the type (observation or preference)
   and the brief's requirement. Two notes on the same version and feature
   conflict when one asks for a change another says is not needed, or asks
   for the opposite, or when both cannot be met in one sample. Choose
   neither side.
7. List single comments and things reported as working. A single comment
   is a point from one person that nobody supports or opposes. A working
   point reports something working, listed with the brief's requirement.
   A note counted in one category (for example agreed) may also print
   its other point as working; the tally still counts the note once.
8. Check each earlier request against the latest version: addressed (a note
   reports the problem gone and none reports it present, or the supplier
   replaced the part and no note reports the problem on the new version;
   say which), still open, not yet seen or unclear. Cite older-version
   notes under their request instead of relisting them.
9. List supplier-stated changes that no note covers.
10. Draft numbered brief notes from agreed changes, still-open requests
    and untested changes only, marking any that rest on one person. A
    change that is not a feature in the brief is marked "Not in brief".
    State what is held back and why. Mark the draft "not approved; do not
    send".
11. List the decisions for the product owner: every conflict, every
    restated request that rests on one note, who takes each specialist
    question, and approval of the brief notes. Count each note once in this
    order: set aside, specialist, earlier request (older-version notes only),
    conflicting, agreed, single, working. If the counts do not equal the
    notes read, stop and say so.
12. Use the output format exactly. Print "None." for an empty section. End
    with the trace line. The "Prepared" date is the date of the run from
    the settings. If no specialist is named, print "the person the
    brand names for materials and safety" and say no name was supplied.

Decline any request to pick a winner, send the brief, approve it, or say a
sample is safe. Never ask for passwords or login codes.
```

## What to customize

- Your feature list, in the words the brief and the notes both use.
- How many different people make a point agreed.
- Your sample label format and the version names you use.
- Who is the product owner, and who takes materials, technical and safety questions.
- How the brief reaches the supplier, and who sends it.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment. Revised after review on 10 November 2026: rules added for a mixed fact-and-wish sentence, a missing specialist, the run date, and four clarifications carried into the instruction block.
