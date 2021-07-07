# Getaround EU Analytics Engineering Challenge (previously Drivy)

Looking for a job? Check out our [open positions](https://uk.getaround.com.com/jobs).
You can also take a look at our [engineering blog](https://drivy.engineering/) to learn more about the way we work.

## Guidelines

- Clone this repo (do **not** fork it)
- Solve the exercises in  ascending order
- Only do one commit per exercise, include the `.git` when submiting your work

Please do the simplest thing that could work for the exercise you're currently solving.

For higher levels we are interested in seeing code that is:

- Clean
- Extensible
- Reliable

## Challenge

The challenge needs to be resolved in PostgreSQL.
Exercises depend on datasets available in /data/
**You can't modify them.**

Your solution to exercise {N} needs to live in the `worksheets_{N}` directory as .sql files.

For certain parts of the challenge, you will be asked to provide written answers, in these cases, please submit them in `worksheets_{N}` as markdown files.

## Setup

### 0.1

Create a local Postgresql instance, ideally 13.3 on MacOS

### 0.2

Create a table named `raw_payloads` in the SQL instance you have just created and insert the payloads provided in `./data/tracking_payloads_20210603.csv`.

### 0.3

Create another table named `payloads` and insert a parsed version of `raw_payloads` inside of it.

## Exercise 1

The payload you have been provided with are generated whenever a user triggers an action relevant to our analytics on the platform. Each payload respects a default structure:
- `timestamp`: generated at the exact time of the action.
- `anonymous_id`: associated to a user device
- `action_id`: associated to the action

With an optional additional key:
- `url`: url the user has triggered the action from

### 1.1

We want to aggregate these events together to analyse user behavior over a certain period of time.
Create a table that aggregates events per session of events. If a user has stopped their activity for more than 30 minutes, we should consider the session as ended.

The SQL query you design to create this table should ultimately respect the following format:
- `anonymous_id`
- `session_id`
- `session_start`
- `session_end`