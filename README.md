#Tracker

By Chris Beard (https://github.com/chrisbeard).

## Description
**Tracker** is a script which can track any type of numerical data.
Data is stored in a sqlite3 database, which resides in your home directory. All values are stored as reals.

Data is organized by tracker name, and each entry is associated with a date under-the-hood. Tracker data can then be visualized and tracker statistics can be displayed.


##Usage:

####Add a new tracker

```
$ tracker update pushups 10
Tracker 'pushups' not found
Confirm 'pushups' to create: pushups
'pushups' updated
$
```

####List existing trackers

```
$ tracker list
Current Trackers:
  pushups
  naps
$
```

####Update a tracker for today

```
$ tracker update pushups 25
'pushups' updated
$
```
Note: If the tracker already has data for today, it will *add* the value given to the existing value.

####Update a tracker for arbitrary date

```
$ tracker update pushups
Provide date YYYY-MM-DD (leave blank for today): 2016-01-01
Value: 50
'pushups' updated
$
```
Note: If the tracker already has data for the given day, it will *add* the value given to the existing value.

####Show raw data for a tracker
```
$ tracker show pushups
2016-01-05 | 10.0
2016-01-06 | 50.0
2016-01-07 | 25.0
$
```

####Delete a tracker
```
$ tracker delete pushups
Type 'puhsups' to confirm: pushups
Tracker named 'pushups' deleted
$
```
Note: Deletion is permanent and cannot be undone!


####Show global tracker stats
```
$ tracker stats
2 tracker(s)
12 total entries

pushups
  3 entries

naps
  9 entries
$
```

####Show detailed tracker stats
```
$ tracker stats pushups
pushups: 14 entries

   sum -- 350.000
   avg --  25.000
   min --  10.000 (2016-01-05)
   max --  50.000 (2016-01-06)

   longest streak --  5 day(s)  (2016-01-13 to 2016-01-17)
   longest break  -- 25 day(s)  (2016-02-04 to 2016-02-29)

             Total                  Avg                   Min                   Max
   Sun --   30.000               30.000                30.000                30.000
   Mon --   50.000               25.000                10.000                40.000
   Tue --   10.000               10.000                10.000                10.000
   Wed --   80.000               40.000                30.000                50.000
   Thu --  105.000               26.250                25.000                30.000
   Fri --   10.000               10.000                10.000                10.000
   Sat --   65.000               21.667                10.000                30.000
$
```
Note: Longest break does not consider time between last entry and current day, as it may not make sense.


####Show correlation between trackers
```
$ tracker stats pushups naps
Correlation coefficient: -0.7574057028716906
$
```


####Plot a tracker
```
$ tracker plot pushups


                                     pushups

  55 +++-+--+-+-+-+-+--+-+-+-+-+-+--+-+-+-+-+--+-+-+-+-+--+-+-+-+-+-+--+-+++
     |          +              +               +            pushups ****** |
  50 ++  *                                                                ++
     |   *                                                                 |
  45 ++  *                                                                ++
     |   *                                                                 |
  40 ++  *          *                                                     ++
     |   *          *                                                      |
  35 ++  *          *                                                     ++
     |   *          *                                                      |
  30 ++  *      *   *    *       *                        *               ++
     |   *      *   *    *       *                        *                |
  25 ++  *  *   *   *    * *   * *                        *              *++
     |   *  *   *   *    * *   * *                        *              * |
  20 ++  *  *   *   *    * *   * *                        *              *++
     |   *  *   *   *    * *   * *                        *              * |
  15 ++  *  *   *   *    * *   * *                        *              *++
     |   *  *   *   *    * *   * *                        *              * |
  10 ++* *  *   *   *    * * * * *             +          *   *          *++
     +-*-*--*-+-*-+-*--+-*-*-*-*-*--+-+-+-+-+--+-+-+-+-+--*-+-*-+-+-+--+-*-+
              01/09          01/16           01/23          01/30
$
```
Note: Only one tracker can be plotted at a time.