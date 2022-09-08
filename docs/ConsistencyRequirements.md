# Consistency Requirements

## Read consistency

The app should have consistent reads where queries may show stale data (data
excluding the results of a recently completed write action). Realtime
queries after recent writes are not a concern with the use of this app.

## Write consistency

The app should have consistent writes where new data does not have conflicting
action IDs. These action IDs may be managed by the database or database
management system.
