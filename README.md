# githubGraph
MIT course 6.S079 group project

## Scraping the data

First, before launching any jupyter notebook in the terminal to scrape github, make sure to run the lines:  

```
export GITHUB_TOKEN= <your token>
export GITHUB_USERNAME= <your username> 
```

## Datasets
#### *Repositories*
`repo_info_stop75.csv` contains information `[name, stargazers_count, forks_count, subscribers_count, topics, language, created_at, updated_at, url, search_word]` for 24207 unique repositories, and where `search_word` is the keyword for which the respository showed up in the search results. 

`topic_relationship_table_stop75.csv` maps repositories to topic words included in their topic list. This dataset contains 67779 repository-topic pairs. 

#### *Contributors*
`10_contributor_info_all.csv` contains information `[login, url, type, name, company, location, hireable, bio, # of public repos, # of public gists, # of followers, # of following]` for 45236 unique GitHub users. 

`repo_contributor_relationship_table_all.csv` maps GitHub users to Repositories they've contributed to and includes the number of contributions they've made to the repository. This dataset contains 129093 contributor-repository pairs. 

## Precomputed Networks
**Repo Contributor:** Nodes are repositories and edges are mutual contributors. Size of nodes are # of stargazers of the repo and color is either the searchword or language. Size of edges are average number of followers among all mutual contributors. 

**Topic Repo:** Nodes are simplified topics and edges are mutual repositories. Size of nodes are # of repositories in topic and size of edges are # of mutual repositories. 

**Topic Contributor:** Nodes are simplified topics and edges are mutual contributors. Size of nodes are # of contributors in topic and size of edges are # of mutual contributors. 


**_Naming Conventional for Precomputed Networks_:**

`{type of network}_network_{parameters}.html`

_Type of Network:_

`rc` – Repo-Contributor

`tc` – Topic-Contributor

`tr` – Topic-Repo

_Parameters:_

`n` – Value of minimum size of connected components included

`k` – Value of minimum k_core size <https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.core.k_core.html>

`threshold` – Threshold value for minimum number of mutual repos/contributors depending on network type
