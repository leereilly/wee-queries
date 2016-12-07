# Wee Queries

Query sets for [BigQuery](https://bigquery.cloud.google.com/dataset/bigquery-public-data:github_repos) :mag:

## Example

Word on the street was that https://github.com/leereilly/games was on the front page of Hacker News, Reddit, and GitHub's explore page on Oct 24th...

### Query

```sql
SELECT repo.id AS ID, repo.name AS Name, COUNT(*) as Stars
FROM TABLE_DATE_RANGE([githubarchive:day.], TIMESTAMP('2016-10-24'), TIMESTAMP('2016-10-24'))
WHERE type = "WatchEvent"
GROUP BY ID, Name
ORDER BY Stars DESC
LIMIT 5;
```

### Result

| Row | ID       | Name                                              | Stars        |
|-----|----------|---------------------------------------------------|--------------|
| 1   | 3112748  | leereilly/games :eyes:                            | 1383 :trophy:|
| 2   | 71732460 | engineerapart/TheRemoteFreelancer                 | 1009         |
| 3   | 70905478 | songrotek/Deep-Learning-Papers-Reading-Roadmap    | 726          |
| 4   | 28457823 | FreeCodeCamp/FreeCodeCamp                         | 517          | 
| 5   | 14807173 | SamyPesse/How-to-Make-a-Computer-Operating-System | 385          |


