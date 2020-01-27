# Standard 00001: Flight Log chaining

Proposal is to mark every flight log with an auto increment number, counter is initialized to 0 when drone is manufactured in a factory, every flight log generated contains the counter and then incremented. every subsequent flight log will have counter value of 1 plus the counter value of previous flight log

## Schema changes

- Add a mandatory field `sequenceNo`

## Broken chain

Incident report is generated for each flight log skipped.

## Mandatory Requirements

- DSP should accept logs in a sequence, except for incident reports against skipped flight logs.
- UAS should not be able to fake a broken chain.

