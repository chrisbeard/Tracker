#Tracker

By Chris Beard (https://github.com/chrisbeard).

## Description
**Tracker** is a script which can track any type of numerical data.
Data is stored in a sqlite3 database, which resides in your home directory.

Data is organized by tracker name, and every entry is associated with a date under-the-hood. Tracker data can then be visualized and tracker statistics can be displayed.


##Usage:

####Add a new tracker

```
$ tracker **update** pushups 10
Tracker 'pushups' not found
Confirm 'pushups' to create: pushups
'pushups' updated
$
```

####Show existing trackers

```
$ tracker **list**
Current Trackers:
	pushups
	naps
$
```

####Update a tracker for today

```
$ tracker **update** pushups 25
'pushups' updated
$
```
Note: If the tracker already has data for today, it will *add* the value given to the existing value.

####Update a tracker for arbitrary date

```
$ tracker **update** pushups
Provide date YYYY-MM-DD (leave blank for today): 2016-01-01
Value: 50
'pushups' updated
$
```
Note: If the tracker already has data for the given day, it will *add* the value given to the existing value.

####Remove a tracker
```
$ tracker **delete** pushups
Type 'puhsups' to confirm: pushups
Tracker named 'pushups' deleted
$
```
Note: Deletion is permanent and cannot be undone!


####Show global tracker stats
```
$ tracker **stats**
2 tracker(s)
12 total entries

pushups
  3 entries

naps
  9 entries
$
```